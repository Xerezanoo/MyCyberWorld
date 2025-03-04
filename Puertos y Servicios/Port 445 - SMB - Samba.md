Este es el puerto principal para la comunicación SMB en redes modernas. Es utilizado para las conexiones directas de SMB sobre TCP/IP (sin la necesidad de NetBIOS). La mayoría de las implementaciones de SMB (incluyendo Samba) escuchan en este puerto.
## SMB y Samba
- **Samba** es una implementación de código abierto del protocolo SMB/CIFS que permite que sistemas basados en Unix (como Linux) interactúen con clientes SMB (Windows, por ejemplo). Samba facilita la creación de servidores de archivos e impresión en redes heterogéneas (Windows y Linux).
### Servicios relacionados con Samba
- **Samba Server (smbd)**  
    El servicio principal de Samba, `smbd`, es el encargado de gestionar la compartición de archivos e impresoras. A través de este servicio, se accede a los recursos compartidos de la máquina.

- **NetBIOS (nmbd)**  
    El servicio `nmbd` gestiona las funciones de NetBIOS, como la resolución de nombres y la navegación en redes locales de Windows. Aunque SMB puede funcionar sin NetBIOS (como SMB sobre TCP/IP en el puerto 445), en algunos casos se utiliza en redes más antiguas o configuraciones que aún requieren compatibilidad con NetBIOS.
    
### Comprobación de puertos y servicio SMB con Nmap
Si quieres verificar si un servidor está corriendo Samba (o SMB), puedes usar `nmap` para escanear los puertos 445 y 139, y ver si están abiertos:
```bash
nmap -p 139,445 <dirección_IP_del_objetivo>
```
Este comando te mostrará si esos puertos están abiertos, lo que indicaría que el servidor está corriendo SMB o Samba. Además, se pueden usar scripts específicos de Nmap para enumerar los recursos SMB y obtener más detalles.

**Ejemplo:**
```bash
nmap -p 445 --script smb-enum-shares.nse <IP_del_objetivo>
```
Este script escaneará los recursos compartidos y te mostrará qué directorios y archivos están disponibles en el servidor SMB.
### Seguridad en SMB
- **SMBv1:** Es la versión más antigua de SMB y es conocida por ser vulnerable a varios ataques, como el famoso ataque de **EternalBlue** que aprovechó una vulnerabilidad en SMBv1 para propagar el ransomware WannaCry. Por esta razón, es recomendable deshabilitar SMBv1 y usar versiones más modernas, como SMBv2 o SMBv3.

- **Cifrado:** En versiones modernas de SMB (SMBv2 y SMBv3), se han añadido características como el cifrado para proteger los datos durante la transmisión. Si un servidor SMB está configurado adecuadamente, debería tener habilitado el cifrado para proteger los datos sensibles.

### Conclusión
- **Puerto 445:** El puerto principal de SMB y Samba, utilizado para la comunicación directa sobre TCP/IP.
- **Puerto 139:** Usado para SMB sobre NetBIOS, aunque hoy en día se usa menos.
- **Samba (smbd y nmbd):** Servicios que permiten la compartición de archivos e impresión en redes basadas en SMB.
- **Seguridad:** Es importante asegurarse de deshabilitar SMBv1 y habilitar medidas de seguridad adecuadas para proteger las transferencias de datos SMB.