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
