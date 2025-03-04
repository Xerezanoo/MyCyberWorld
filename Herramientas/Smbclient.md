## ¿Qué es?
`SMBClient` es una herramienta de línea de comandos que se utiliza para acceder a recursos compartidos en sistemas que implementan el protocolo SMB (Server Message Block). Puedes usarla para interactuar con recursos compartidos en redes locales o en redes remotas, como compartir archivos, explorar directorios y realizar pruebas de acceso.

## ¿Para qué se usa?
- Acceder a recursos compartidos de archivos en sistemas remotos.
- Realizar auditorías de seguridad sobre servidores SMB.
- Probar accesos anónimos a recursos compartidos.
- Explorar directorios de servidores SMB de forma interactiva o automatizada.
- Realizar ataques de acceso remoto a servidores SMB mal configurados.

## Sintaxis básica  
Para acceder a un recurso compartido, se utiliza la siguiente sintaxis:
```bash
smbclient //IP-DESTINO/RECURSO -U USUARIO
```
- **`//IP-DESTINO/RECURSO`**: Dirección del servidor SMB y el recurso compartido.
- **`-U USUARIO`**: El nombre de usuario con el que acceder al recurso compartido. Si se quiere acceso anónimo, se puede usar un `guest`.

## Ejemplo
Si tienes un recurso compartido llamado `shared_folder` en un servidor con IP `192.168.1.10`, puedes acceder con:
```bash
smbclient //192.168.1.10/shared_folder -U guest
```
Si el recurso requiere autenticación, te pedirá la contraseña.

## Principales opciones de `smbclient`
- **`-L`**  
    Muestra los recursos compartidos disponibles en un servidor SMB. Ejemplo:
```bash
smbclient -L //192.168.1.10 -U guest
```
- **`-U`**  
    Especifica el nombre de usuario para la autenticación. Puede usarse también con un nombre de usuario anónimo (`guest`):
```bash
smbclient //192.168.1.10/shared_folder -U usuario
```
- **`-W`** 
    Permite especificar el dominio (si aplica):
```bash
smbclient //192.168.1.10/shared_folder -U usuario -W dominio
```
- **`-c`**  
    Ejecuta un comando SMB directamente, sin entrar en el modo interactivo:
```bash
smbclient //192.168.1.10/shared_folder -U usuario -c "ls"
```
- **`-p`**  
    Especifica el puerto SMB, si el servidor no utiliza el puerto predeterminado (445):
```bash
smbclient //192.168.1.10/shared_folder -U usuario -p 139
```

## Uso en Ciberseguridad
En el contexto de la ciberseguridad, `smbclient` es útil para realizar auditorías de seguridad, detectar configuraciones inseguras y probar el acceso a recursos SMB mal configurados.
- **Acceso a recursos sin contraseña:** Si un servidor SMB está configurado para permitir acceso anónimo, puedes acceder a los recursos compartidos sin necesidad de autenticación, lo que puede ser útil para realizar pruebas de penetración.
```bash
smbclient //192.168.1.10/shared_folder -U guest
```

  - **Exploitar configuraciones débiles:** Si un servidor SMB tiene contraseñas débiles o mal configuradas, puedes intentar acceder a los recursos utilizando un ataque de diccionario o de fuerza bruta, por ejemplo, con `smbclient` en combinación con herramientas como `Patator` o `Hydra`.

- **Enumeración de recursos compartidos:** Al usar la opción `-L`, puedes enumerar los recursos SMB disponibles en un servidor y examinar qué datos pueden estar accesibles sin autenticación o con credenciales predeterminadas.
```bash
smbclient -L //192.168.1.10 -U guest
```

## Integración con otras herramientas
`SMBClient` se puede combinar con otras herramientas de ciberseguridad para realizar pruebas más exhaustivas:
- **Hydra o Patator:** Para realizar ataques de diccionario sobre SMB con credenciales débiles.

- **Nmap:** Utiliza Nmap con el script `smb-enum-shares.nse` para detectar los recursos compartidos en un servidor SMB antes de intentar acceder a ellos con `smbclient`.
```bash
nmap -p 445 --script smb-enum-shares.nse 192.168.1.10
```

---
## Conclusión
`SMBClient` es una herramienta muy útil para interactuar con servidores SMB en auditorías de seguridad, pruebas de penetración y explotación de configuraciones débiles. Si bien no es tan potente como otras herramientas específicas de ataque, su simplicidad y flexibilidad lo hacen indispensable en el arsenal de cualquier profesional de la seguridad.
