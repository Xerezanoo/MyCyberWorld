**Descripción**:  
HTTP es el protocolo fundamental utilizado para la transferencia de recursos, como páginas web y otros contenidos, a través de la web. Es un protocolo sin cifrar, lo que significa que la información, incluidas las credenciales y los datos sensibles, se transmite en texto claro. Debido a esto, las aplicaciones web basadas en HTTP son vulnerables a varios tipos de ataques.

**Características**:
- **Sin cifrado**: HTTP no cifra la información durante la transmisión, lo que lo hace vulnerable a ataques como **sniffing** o **man-in-the-middle**.
- **Transferencia de recursos**: HTTP es utilizado por los navegadores y servidores web para enviar y recibir información en la web.

**Vulnerabilidades comunes en HTTP**:
1. **Authentication and Authorization**:  
    Errores en la implementación de la autenticación y autorización pueden permitir a los atacantes acceder a recursos que no deberían estar disponibles para ellos.
    
2. **Injection Flaws**:  
    Son vulnerabilidades que ocurren cuando el atacante puede inyectar comandos maliciosos en una aplicación web.
    - **SQL Injection**: Inyección de código SQL a través de formularios de entrada o URLs, lo que permite a un atacante acceder o manipular bases de datos.  
        **Ejemplo**: [[1. Appointment - Web (SQL Injection, Gobuster dir)]]
    - **LDAP Injection**: Inyección de comandos LDAP, a menudo utilizada para manipular consultas de directorios y obtener información no autorizada.
    - **XML Injection**: Inyección de datos XML maliciosos, aprovechando vulnerabilidades en la forma en que se procesan los documentos XML.
3. **Broken Authentication**:  
    Ocurre cuando las aplicaciones no implementan adecuadamente la autenticación, permitiendo a los atacantes eludir el proceso de inicio de sesión o robar sesiones.
    
4. **Cross-Site Scripting (XSS)**:  
    Permite a los atacantes inyectar scripts maliciosos en las páginas web vistas por otros usuarios, lo que puede llevar al robo de cookies, secuestro de sesiones o ejecución de acciones no autorizadas.
    
5. **Cross-Site Request Forgery (CSRF)**:  
    Este ataque aprovecha la confianza que un sitio web tiene en el navegador del usuario, haciendo que el navegador realice acciones no deseadas (como cambiar contraseñas o realizar compras) en el sitio web de un usuario autenticado sin su consentimiento.

**Consideraciones de seguridad**:  
Para mitigar las vulnerabilidades asociadas con HTTP, se recomienda:
- **Usar HTTPS (Puerto 443)**: HTTPS cifra la comunicación entre el navegador y el servidor, protegiendo la información sensible.
- **Implementar medidas de validación y sanitización**: Evitar la inyección de código mediante la validación adecuada de entradas de usuario.
- **Autenticación robusta**: Usar autenticación de múltiples factores (MFA) y gestionar sesiones de manera segura.
- **Protección contra XSS y CSRF**: Implementar medidas para prevenir la inyección de scripts y la falsificación de solicitudes entre sitios.