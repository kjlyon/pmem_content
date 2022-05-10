The [ipmctl](https://github.com/intel/ipmctl) utility is used for configuring and managing Intel Optane Persistent Memory modules (PMem). It supports the functionality to:

- Discover Persistent Memory on the server
- Provision the persistent memory configuration
- View and update the firmware on the persistent memory modules
- Configure data-at-rest security
- Track health and performance of the persistent memory modules
- Debug and troubleshoot persistent memory modules

I wrote the [IPMCTL User Guide](https://docs.pmem.io/ipmctl-user-guide/) showing how to use the tool, but what if ipmctl returns an error or something you're not expecting? How do you debug the debugger? On Linux, ipmctl relies on libndctl to help perform communication to the BIOS and persistent memory modules themselves. This is a complicated stack involving multiple kernel drivers and the physical hardware itself. Anything along this path could be causing a problem.
