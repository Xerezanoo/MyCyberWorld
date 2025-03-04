**Descripción**:  
Nmap es una herramienta de código abierto para escanear redes, descubrir hosts, identificar puertos abiertos y detectar los servicios que están corriendo en un sistema. Se utiliza comúnmente en auditorías de seguridad y pruebas de penetración.

**Funcionalidades clave**:
- **Descubrimiento de hosts**: Identifica dispositivos conectados a la red.
- **Escaneo de puertos**: Determina qué puertos están abiertos en un host.
- **Detección de servicios**: Identifica los servicios que se ejecutan en los puertos abiertos, incluyendo versión y detalles de los mismos.
- **Detección de sistema operativo**: Permite identificar el sistema operativo del host.
- **Escaneo de vulnerabilidades**: Usado para detectar posibles vulnerabilidades a través de scripts Nmap Scripting Engine (NSE).

**Comandos básicos**:
- **Escaneo de hosts**:
```bash
nmap [IP objetivo]
```
- **Escaneo de puertos**
```bash
nmap -p [puertos] [IP objetivo]
```
- **Detección de sistema operativo**:
```bash
nmap -O [IP objetivo]
```
- **Detecta la versión de los servicios que están corriendo en los puertos abiertos:**
```bash
nmap -sV [IP objetivo]
```
- **Escaneo con scripts NSE**
```bash
nmap -sC [IP objetivo]
```
- **Escaneo de tipo SYN Scan, que no termina la conexión TCP y es más rápido y menos detectable:**
```bash
nmap -sS [IP objetivo]
```
--> El escaneo SYN envía un paquete SYN al puerto, esperando una respuesta SYN-ACK, pero no completa la conexión, para ser menos detectable.
- **Controla la velocidad de escaneo configurando un mínimo de paquetes por segundo:**
```bash
nmap --min-rate [nº paquetes/segundo] [IP objetivo]
```
- **Proporciona una salida detallada con verbose (cuantas más `v`, más detallada será):**
```bash
nmap -v / -vv / -vvv [IP objetivo]
```

**Consideraciones de seguridad**:
- **Uso ético**: Realiza escaneos solo en redes y dispositivos que tengas permiso para auditar.
- **Detección**: El uso de Nmap en una red puede ser detectado por sistemas de monitoreo, ya que genera tráfico característico.

**Ejemplo de uso**:
- **Escanear toda la red local mandando 5000 paquetes por segundo con detección de servicios y versiones y que me lo detalle bastante**:
```bash
nmap -sS -sV -sC --min-rate 5000 -vvv 192.168.1.0/24
```
