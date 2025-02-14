Telnet es un protocolo de red utilizado para acceder de manera remota a otros dispositivos a través de una red. Aunque fue muy popular en el pasado, Telnet no es seguro, ya que no cifra los datos ni las credenciales enviadas, lo que facilita su interceptación por parte de atacantes. Debido a sus vulnerabilidades, Telnet ha sido reemplazado en gran medida por protocolos más seguros como SSH.

**Características**:
- **No cifrado**: Telnet transmite los datos en texto claro, lo que significa que cualquier atacante que intercepte el tráfico podrá ver las credenciales y la información intercambiada.
- **Acceso remoto**: Permite a los usuarios acceder a un sistema de forma remota, pero sin protección adecuada contra ataques.

**¿Cómo comprometerlo?**:
1. **Escaneo de puertos**:  
    Usamos herramientas como `nmap` para escanear la máquina objetivo y verificar si el puerto 23 (Telnet) está abierto.
```bash
nmap [ip máquina]
```
2. **Conexión Telnet**:  
	Si el puerto está abierto, nos conectamos a la máquina remota usando el comando `telnet`.
```bash
telnet [ip máquina]
```
3. **Acceso sin autenticación**:  
	En muchos casos, Telnet puede estar configurado sin autenticación o con credenciales débiles. Una vez conectados, podemos intentar iniciar sesión como `root` sin necesidad de contraseña.
	
**Ejemplo de máquina**:  
[[1. Meow - Telnet]]

**Consideraciones de seguridad**:  
Debido a que Telnet transmite información sensible sin cifrado, se considera un protocolo inseguro. Su uso está desaconsejado, especialmente en redes públicas o no confiables. Siempre que sea posible, es preferible utilizar SSH (Puerto 22) para conexiones remotas seguras.
