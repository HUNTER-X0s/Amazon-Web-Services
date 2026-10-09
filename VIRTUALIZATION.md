VIRTUALIZATION
virtualization is the process of creating multiple simulated environments or virtual machines from a single physical hardware system, enabling more efficient resource use.


Hypervisor :- It is a software that creates and runs virtual machines. 
Example : Virtual Box

How Hypervisor Works: 
Virtual box shares hardware resources from host OS.
Separate set of virtual CPU, RAM, storage, etc. 
Virtual machines are fully isolated, independent of hosted OS. 

Benefits of Virtual Machines:
- We don't need new resources to use a different OS.
- No risk of any issues with your primary OS.
- Testing any app on a different OS

Types of hypervisor:
- type 1: Bare-Matel 
ex : hardware → Hypervisor (VMware vSphere / ESXi) (Xen, Citrix Xen server) → Different OS (Linux, Windows, MAC)
- type 2: hosted  
ex : Virtual Box 


Virtualization use case : 
- Cheap
- Reduces workload
- Reduces space
- Reduces energy
- Easy backup using snapshot
- Easy recovery

## Remember virtualization as a resource boundary

A hypervisor divides one physical host's CPU, memory, storage, and network resources among virtual machines. Each VM has its own guest operating system and behaves like a separate computer, while the host and hypervisor remain shared dependencies. A Type 1 hypervisor runs directly on hardware; a Type 2 hypervisor runs on a host operating system.

Virtual machines provide stronger OS-level separation than containers, but consume more resources because each VM runs a guest OS. Snapshots can speed recovery and testing, but are not automatically a complete backup strategy—especially for active databases or data stored outside the VM disk.

**Recall check:** A VM is isolated, but the physical host fails. Why can multiple VMs still be affected? They share the host hardware and hypervisor as a failure domain.


























