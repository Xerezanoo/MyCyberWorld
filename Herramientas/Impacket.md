Impacket es una colección de herramientas y librerías para trabajar con protocolos de red de bajo nivel. Es muy útil en pruebas de penetración, ya que permite la interacción con protocolos como SMB, DNS, HTTP, RDP, entre otros.
## Instalación y Configuración
1. Clonar el repositorio y entrar en él:
```bash
git clone https://github.com/SecureAuthCorp/impacket.git && cd impacket
``` 
2. Crear y activar un entorno virtual:
```bash
python3 -m venv .venv
```
```bash
source .venv/bin/activate
```
3. Instalar dependencias:
```bash
pip3 install -r requirements.txt
```
```bash
pip3 install .
```
## Herramientas y Usos Comunes de Impacket
1. **psexec.py**
Descripción:
Permite ejecutar comandos de manera remota en sistemas Windows utilizando el protocolo SMB. Ideal para realizar pruebas de penetración y obtener acceso remoto a través de SMB.
Ejemplo:
```bash
python3 psexec.py user:password@target_ip cmd.exe
```

2. **smbexec.py**
Descripción:
Ejecuta comandos de manera remota sobre un recurso compartido SMB de una máquina objetivo. Es similar a psexec.py, pero enfocado en ejecutar scripts y comandos sin necesidad de una shell interactiva.
Ejemplo:
```bash
python3 smbexec.py user:password@target_ip
```

3. **wmiexec.py**
Descripción:
Permite ejecutar comandos remotamente en máquinas Windows utilizando Windows Management Instrumentation (WMI). Es una excelente opción para evadir firewalls y restricciones SMB.
Ejemplo:
```bash
python3 wmiexec.py user:password@target_ip cmd.exe
```

4. **secretsdump.py**
Descripción:
Extrae hashes de contraseñas de un controlador de dominio o máquina Windows. Puede volcar los hashes de SAM y NTDS, permitiendo la posterior realización de ataques de cracking de contraseñas.
Ejemplo:
```bash
python3 secretsdump.py user:password@target_ip
```

5. **mssqlclient.py**
Descripción:
Permite interactuar con servidores Microsoft SQL Server de manera remota. Se puede usar para realizar consultas, ejecutar comandos SQL y obtener acceso a bases de datos. Ideal para pruebas de penetración en servicios MS SQL.
Ejemplo:
```bash
python3 mssqlclient.py user:password@target_ip
```
Ejecutar una consulta:
```bash
python3 mssqlclient.py user:password@target_ip -c "SELECT * FROM master.dbo.sysdatabases"
```

6. **impacket-smbclient.py**
Descripción:
Permite interactuar con recursos compartidos SMB en una máquina Windows, de forma similar a un cliente SMB tradicional. Utilizado para explorar los recursos de red de una máquina objetivo.
Ejemplo:
```bash
python3 impacket-smbclient.py //target_ip/share_name user:password
```

7. **ntlmrelayx.py**
Descripción:
Realiza ataques de retransmisión NTLM contra máquinas Windows. Permite tomar credenciales de autenticación NTLM de máquinas vulnerables para acceder a otros recursos o servicios dentro de la red.
Ejemplo:
```bash
python3 ntlmrelayx.py -t smb://target_ip
```

8. **getTGT.py**
Descripción:
Permite obtener un Ticket Granting Ticket (TGT) de Kerberos para un usuario autenticado en un dominio. Usado en ataques de Kerberos para la escalación de privilegios.
Ejemplo:
```bash
python3 getTGT.py user:password@target_ip
```

9. **dcomexec.py**
Descripción:
Ejecuta comandos de manera remota a través del protocolo DCOM. Es una excelente alternativa a los métodos SMB y WMI para ejecutar comandos sin necesidad de acceso físico.
Ejemplo:
```bash
python3 dcomexec.py user:password@target_ip cmd.exe
```

10. **wcs.py**
Descripción:
Permite la ejecución remota de comandos utilizando el servicio de Windows Command Shell. Similar a wmiexec.py, pero usando comandos específicos de shell.
Ejemplo:
```bash
python3 wcs.py user:password@target_ip cmd.exe
```

11. **kerberostgt.py**
Descripción:
Permite obtener un TGT de Kerberos y realizar ataques de Pass-the-Ticket (PTT) en redes de Windows. Es usado comúnmente para obtener acceso a servicios de Kerberos y escalar privilegios.
Ejemplo:
```bash
python3 kerberostgt.py user:password@target_ip
```

## Características Principales:
- **Protocolos soportados**: SMB, RDP, LDAP, HTTP, entre otros.
- **Acceso remoto**: Facilita el acceso y control remoto de sistemas mediante SMB, WMI y otros protocolos.
- **Extracción de credenciales**: Permite la recolección de hashes y credenciales de usuarios de sistemas Windows.

## Uso común en auditorías de seguridad:
- Realizar ataques de ejecución remota de comandos (RCE) sobre SMB y WMI.
- Enumerar y extraer hashes de contraseñas de sistemas comprometidos.
- Simular ataques como parte de un Pentesting para evaluar la seguridad de sistemas Windows.

Referencias de uso: [Impacket Documentation](https://github.com/fortra/impacket)
