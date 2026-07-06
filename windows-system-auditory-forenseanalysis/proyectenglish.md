Audit and Analysis Phases

1. Volatile Memory (RAM) Acquisition and Analysis
Performed a live RAM dump to capture the system's current state.

Using Mandiant Redline, analyzed the hierarchical process view to identify anomalous "parent-child" relationships, facilitating the detection of potential code injections, hidden processes, or malware running in the background.

Documented running processes and their resource consumption using command-line utilities.

2. System Artifacts and Persistence Auditing
Users and Access: Gathered information on local users and logon history to identify potential unauthorized access.

Persistence Mechanisms: Audited startup programs (autoruns) to detect malicious software attempting to establish persistence on the machine.

Activity Tracking: Analyzed recently modified files and extracted the history of connected USB devices—a critical step for investigating data exfiltration or initial infection vectors.

3. Multimedia Forensics (OSINT/Forensics)
Applied metadata analysis techniques (EXIF) on photographic material collected as evidence.

Successfully identified precise information regarding the capture hardware (manufacturer and model) and extracted exact GPS coordinates, allowing for the physical geolocation of the device at the time the picture was taken.

4. Preservation and Chain of Custody (Integrity)
To guarantee the legal immutability of the evidence, cryptographic signatures were generated using the SHA-256 algorithm for all collected files.

Additionally, an integrity record (hashing) was generated for critical operating system drivers (C:\Windows\System32\drivers), establishing a reliable security baseline to detect future alterations or spoofing by rootkits/malware.
