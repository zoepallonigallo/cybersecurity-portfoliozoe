Fases de la Auditoría y Análisis;

1. Adquisición y Análisis de Memoria Volátil (RAM)
Se realizó un volcado de la memoria RAM activa para capturar el estado "vivo" del sistema.

Mediante Mandiant Redline, se analizó la vista jerárquica de procesos para identificar relaciones "padre-hijo" anómalas, facilitando la detección de posibles inyecciones de código o malware ejecutándose en segundo plano.

Se documentaron los procesos en ejecución y su consumo de recursos utilizando utilidades de línea de comandos.

2. Auditoría de Artefactos del Sistema y Persistencia
Usuarios y Accesos: Se recopiló información sobre los usuarios locales y el histórico de inicios de sesión (logons) para identificar accesos no autorizados.

Mecanismos de Persistencia: Se auditaron los programas de arranque automático (startup) en busca de software malicioso que intentara establecer persistencia en el equipo.

Rastreo de Actividad: Se analizaron los archivos modificados recientemente y se extrajo el historial de dispositivos USB conectados al sistema, un paso crítico para investigar exfiltración de datos o vectores de infección inicial.

3. Informática Forense Multimedia (OSINT/Forensics)
Se aplicaron técnicas de análisis de metadatos (EXIF) sobre material fotográfico recolectado como evidencia.

Se logró identificar información precisa sobre el hardware de captura (fabricante y modelo) y se extrajeron las coordenadas GPS exactas, permitiendo la geolocalización física del dispositivo en el momento de la captura.

4. Preservación y Cadena de Custodia (Integridad)
Para garantizar la inmutabilidad legal de las pruebas, se generaron firmas criptográficas utilizando el algoritmo SHA-256 para la totalidad de las evidencias recolectadas.

Adicionalmente, se generó un registro de integridad (hashing) sobre los controladores críticos del sistema operativo (C:\Windows\System32\drivers), estableciendo una línea base de seguridad confiable para detectar futuras alteraciones o suplantaciones por rootkits/malware.
