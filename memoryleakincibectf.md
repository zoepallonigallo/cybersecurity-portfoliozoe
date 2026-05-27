**Bonus: Virtualization Troubleshooting During the INCIBE 2019/2020 CTF**


We faced a massive memory leak caused by VirtualBox, where background processes consumed over 14 GB of RAM, freezing the host Windows system and requiring forced reboots.

In order to complete the CTF, we applied problem-solving methodologies across different layers:

Virtual Hardware Layer: We strictly limited the RAM (Kali to 4GB, target to 512MB) and disabled 3D acceleration, audio, and USB ports to reduce the interaction surface.

Network Layer: We changed from "Bridged Adapter" to "NAT Network" to create a safely isolated environment and prevent driver injection into the host's physical network card.

Operating System Layer: We disabled "Memory Integrity" (Core Isolation) in Windows, as VBS was clashing with the hypervisor. We modified the boot record (bcdedit /set hypervisorlaunchtype off).

Headless Execution: Finally, we ran the vulnerable machine in "Headless" mode (background) to mitigate memory consumption from graphic rendering.

The Definitive Solution:
The definitive solution to the problem was reinstalling the Linux virtual machine from scratch, ensuring we allocated a significantly larger disk space.

The lack of storage in the original partition was creating a bottleneck and saturating the file system, which triggered the hypervisor's collapse and the subsequent massive RAM leak on the host machine. 
Upon correctly provisioning the disk, the environment operated with complete stability.

This exhaustive troubleshooting pointed to a deep compatibility flaw between the VirtualBox kernel version and Windows security patches.
