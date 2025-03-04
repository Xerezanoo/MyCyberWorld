**Descripción**:  
FTP es un protocolo de red utilizado para transferir archivos entre sistemas a través de una red TCP/IP. Aunque es ampliamente utilizado, no es seguro por sí mismo, ya que transmite los datos, incluidas las credenciales, en texto claro.

**Tipos de FTP**:
1. **Anonymous FTP**:  
    Es una forma básica de FTP que permite transferencias de archivos sin requerir autenticación. No utiliza cifrado, lo que lo convierte en un riesgo de seguridad, ya que tanto los datos como las credenciales (si se usan) se transmiten en texto claro.
    - **Ejemplo**: Este tipo de FTP es común en sitios públicos donde se permite la descarga de archivos sin necesidad de credenciales, pero es inseguro.
    - **Ejemplo de máquina**: [[2. Fawn - FTP]]
2. **Password-protected FTP**:  
    Requiere un nombre de usuario y una contraseña para acceder al servidor FTP. Aunque proporciona un nivel básico de protección, la transmisión de credenciales sigue siendo en texto claro a menos que se use cifrado.
    
3. **FTP over Explicit SSL/TLS (FTPES)**:  
    En este tipo de FTP, la conexión se establece de manera explícita mediante SSL/TLS, proporcionando cifrado para la transferencia de datos y las credenciales. Es una versión más segura de FTP y se utiliza comúnmente en sitios web para permitir transferencias de archivos de manera segura.

**Consideraciones de seguridad**:
- FTP sin cifrado es vulnerable a ataques de **sniffing** y **man-in-the-middle**, lo que puede comprometer la integridad y la confidencialidad de los datos.
- Usar **FTPES** o **SFTP** (FTP sobre SSH) es altamente recomendable para proteger las transferencias de archivos en redes inseguras.
