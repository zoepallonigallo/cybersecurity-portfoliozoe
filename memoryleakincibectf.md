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


------

**Bonus: Troubleshooting de VirtualizaciónDurante la práctica del CTF INBICE 2019/2020**

nos enfrentamos a una fuga de memoria masiva (memory leak) provocada por VirtualBox,
donde los procesos en segundo plano consumían más de 14 GB de RAM, congelando el sistema Windows anfitrión y requiriendo reinicios forzados.  
Para poder finalizar el CTF, aplicamos metodologías de resolución de problemas en diferentes capas: 

Capa de Hardware Virtual: Limitamos estrictamente la RAM (Kali a 4GB, objetivo a 512MB) y deshabilitamos la aceleración 3D, audio y puertos USB para reducir la superficie de interacción.  

Capa de Red: Cambiamos de "Adaptador Puente" a "Red NAT" para crear un entorno seguro aislado y evitar la inyección de controladores en la tarjeta física del host.  

Capa de Sistema Operativo: Deshabilitamos la "Integridad de Memoria" (Aislamiento del núcleo) en Windows, ya que los VBS chocaban con el hipervisor. Modificamos el registro de arranque (bcdedit /set hypervisorlaunchtype off).

Ejecución Headless: Finalmente, ejecutamos la máquina vulnerable "Sin pantalla" (en segundo plano) para mitigar los consumos de memoria por renderizado gráfico. 


La solución definitiva al problema fue reinstalar la máquina virtual de Linux desde cero, asegurándonos de asignarle un espacio en disco significativamente mayor.
La falta de almacenamiento en la partición original estaba generando un cuello de botella y saturación en el sistema de archivos, lo que desencadenaba el colapso del hipervisor y la posterior fuga masiva de RAM en el equipo anfitrión.
Al aprovisionar correctamente el disco, el entorno funcionó con total estabilidad.


Este troubleshooting exhaustivo apuntó a un fallo profundo de compatibilidad entre la versión del kernel de VirtualBox y los parches de seguridad de Windows. 
