# Mapping VMWare vSphere/ESXi PMem from Host to VM

In this post, we'll use VMWare ESXi 7.0u3 to create a Guest VM running Ubuntu 21.10 with two Virtual Persistent Memory (vPMem) devices, then show how we can map the vPMem device in the host (ESXi) to "nmem" devices in the guest VM as shown by the `ndctl` utility.

If you're new to using vPMem or need a refresher, start with the VMWare [Persistent Memory](https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.vsphere.resmgmt.doc/GUID-EB72D358-9C2C-4FBD-81A9-A145E155CE31.html) documentation.

## Create a Guest VM with vPMem Devices
The procedure you use may be different from the one shown below if you use vSphere or an automated procedure.

1. In a web browser, navigate to the IP Address of the ESXi host and login
2. On the home page, click the "Create/Register VM"

![Click  Create/Register VM ](https://user-images.githubusercontent.com/21182867/166822739-3cc23eaa-5dd1-46f8-918d-1f18b89b9b7e.jpg)

Alternatively, click "Virtual Machines" on the left, then click "Create/Register VM"

![CLick  Create/Register VM ](https://user-images.githubusercontent.com/21182867/166822845-e835a97c-8ffa-488f-9fc1-678eb914cb55.jpg)

3. Select "Create a new virtual machine", then click "Next"
![Select  Create a new virtual machine ](https://user-images.githubusercontent.com/21182867/166822931-2d6ed787-1139-497d-9444-e7ed1e966e5c.jpg)

4. Enter a "Name" for the Guest VM, then select the "Guest OS Family", and "Guest OS version"
![Select a name a guest OS](https://user-images.githubusercontent.com/21182867/166823119-05abb5cb-bb7d-4534-8cd2-043e8bb49471.jpg)

5. Select a disk datastore for the OS image

![Select Storage](https://user-images.githubusercontent.com/21182867/166823182-99b75bad-096b-4cd5-b2a2-4360af7c59bf.jpg)

6. In the "Customize settings" window, set the number of CPUs, Memory, OS disk size, Network, etc. To add vPMem devices, click "Add other device" and select "NVDIMM" from the list. Repeat adding NVDIMMs for the required quantity. Set the size for each vPMem/NVDIMM.
 
![Customize settings: Virtual Hardware](https://user-images.githubusercontent.com/21182867/166823251-a4f93580-dad7-4763-ac9f-3c584180a5ab.jpg)

![Customize settings: Add an NVDIMM to the guest](https://user-images.githubusercontent.com/21182867/166823365-73c10f53-9823-4e80-bb16-d14ec4df9af5.jpg)

![Customize settings](https://user-images.githubusercontent.com/21182867/166823470-aa662d08-b4b1-4d13-bb0f-73c38ea88686.jpg)

Click "Next" when you're done defining the configuration of the guest.
