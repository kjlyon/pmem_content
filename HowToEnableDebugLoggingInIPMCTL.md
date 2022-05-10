The [ipmctl](https://github.com/intel/ipmctl) utility is used for configuring and managing Intel Optane Persistent Memory modules (PMem). It supports the functionality to:

- Discover Persistent Memory on the server
- Provision the persistent memory configuration
- View and update the firmware on the persistent memory modules
- Configure data-at-rest security
- Track health and performance of the persistent memory modules
- Debug and troubleshoot persistent memory modules

I wrote the [IPMCTL User Guide](https://docs.pmem.io/ipmctl-user-guide/) showing how to use the tool, but what if ipmctl returns an error or something you're not expecting? How do you debug the debugger? On Linux, ipmctl relies on libndctl to help perform communication to the BIOS and persistent memory modules themselves. This is a complicated stack involving multiple kernel drivers and the physical hardware itself. Anything along this path could be causing a problem.

While we could use tools such as strace, ltrace, bpftrace, gdb, etc, ipmctl actually has a nifty feature to record a lot of debug information that can be very helpful to understand where ipmctl is failing. The DBG\_LOG\_LEVEL option defines how much data ipmctl will log. The logs pertain to the operation of the ipmctl command-line tool only and do not reflect any logging functionality of the persistent memory or kernel itself. The available log levels are:

0: Logging is disabled. This is the default.  
1: Log Errors.  
2: Log Warnings, Errors.  
3: Log Informational, Warnings, Errors.  
4: Log Verbose, Informational, Warnings, Errors.

The default log file location on Linux is `/var/log/ipmctl/debug.log` and is defined by DBG\_LOG\_FILE\_NAME.

## Enabling ipmctl debugging
