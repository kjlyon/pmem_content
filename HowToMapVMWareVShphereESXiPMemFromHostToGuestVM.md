# Mapping VMWare vSphere and ESXi PMem from Host to VM

In this post, we'll use VMWare ESXi 7.0u3 to create a Guest VM running Ubuntu 21.10 with two Virtual Persistent Memory (vPMem) devices, then show how we can map the vPMem device in the host (ESXi) to "nmem" devices in the guest VM as shown by the `ndctl` utility.

If you're new to using vPMem or need a refresher, start with the VMWare [Persistent Memory](https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.vsphere.resmgmt.doc/GUID-EB72D358-9C2C-4FBD-81A9-A145E155CE31.html) documentation.
