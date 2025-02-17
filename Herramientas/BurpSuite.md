## Descripción
Burp Suite es una herramienta de seguridad utilizada para analizar y manipular el tráfico web. Se emplea en pruebas de penetración (pentesting) para identificar y explotar vulnerabilidades en aplicaciones web.

## Principales Características
- **Interceptar tráfico HTTP/HTTPS**: Modifica peticiones y respuestas antes de que lleguen al servidor o al cliente.
- **Scanner de vulnerabilidades**: Detecta fallos como XSS, SQLi, y CSRF.
- **Repeater**: Reenvía y edita peticiones manualmente para analizar el comportamiento del servidor.
- **Intruder**: Automatiza ataques de fuerza bruta y fuzzing.
- **Decoder/Comparer**: Decodifica, codifica y compara datos enviados y recibidos.

## Uso Básico en Hacking Ético
1. **Configuración del Proxy en el Navegador**
Para interceptar tráfico, configuramos el navegador para usar Burp Suite como proxy (por defecto, en 127.0.0.1:8080).

2. **Capturar y Modificar Peticiones**
    1. Activamos Intercept en la pestaña Proxy.
    2. Navegamos a un sitio web y capturamos la petición.
    3. Modificamos parámetros (ejemplo: cambiar un valor en una cookie).
    4. Enviamos la petición modificada.

3. **Escaneo de Vulnerabilidades**
    - Vamos a la pestaña Target > Site Map y seleccionamos un objetivo.
    - Botón derecho → Actuar como objetivo de escaneo.
    - En Scanner, analizamos la web en busca de fallos de seguridad.

4. **Ataque con Intruder (Fuerza Bruta/Fuzzing)**
    - Capturamos una petición de login.
    - La enviamos a Intruder y marcamos el campo del usuario o contraseña como parámetro dinámico.
    - Cargamos una lista de palabras (rockyou.txt, por ejemplo).
    - Ejecutamos el ataque para probar credenciales.

5. **Exploiting XSS y SQL Injection**
    - En Repeater, enviamos manualmente una petición con un payload de prueba (<script>alert(1)</script> o ' OR 1=1 --).
    - Comprobamos si la web devuelve un resultado inesperado o ejecuta código malicioso.

## Ejemplo de Uso Rápido (Interceptar y Modificar una Petición)
1. Abrimos Burp Suite y configuramos el navegador con proxy 127.0.0.1:8080.
2. Vamos a la pestaña Proxy > Intercept y activamos la captura de tráfico.
3. Visitamos una web, por ejemplo, http://victima.htb/login.php.
4. Capturamos la petición y modificamos el parámetro username=admin → username=admin' OR 1=1 --.
5. Enviamos la petición modificada y observamos si obtenemos acceso.
