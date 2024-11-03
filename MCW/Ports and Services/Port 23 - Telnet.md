Telnet es un protocolo de red usado para acceder de manera virtual y remota a un equipo. No es un protocolo seguro porque no está encriptado. No se suele usar porque es muy fácil de hackear.

* **¿Cómo poder comprometerlo?**
	1. Primero escaneamos con `nmap [ip machine]` la máquina objetivo para ver si tiene abierto el puerto 23 (telnet).
	2. Si está abierto, nos conectamos haciendo `telnet [ip machine]`
		Ahora tenemos que introducir un usuario y escribimos `root` sin contraseña para acceder.
	
Podemos ver un ejemplo en [[1. Meow - Telnet]]

