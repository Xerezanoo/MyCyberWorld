## Descripción
Patator es una herramienta de fuerza bruta modular, diseñada para realizar ataques de autenticación automatizados en una variedad de servicios, como SSH, HTTP, FTP y otros. Su flexibilidad y capacidad para gestionar múltiples módulos y configuraciones la hacen ideal para realizar pruebas de penetración, especialmente en auditorías de seguridad de contraseñas.

## Usos Comunes de Patator
1. Ataques de Fuerza Bruta a SSH
Patator puede ser utilizado para realizar un ataque de fuerza bruta sobre un servicio SSH. Para ello, se emplea el siguiente comando básico:
```bash
patator ssh_login host=[IP_o_dominio] user=[usuario] password=FILE0 0=<wordlist>
```
--> En este caso, se utiliza una lista de palabras (wordlist) para probar combinaciones de contraseñas contra un usuario específico.

2. Ataques a HTTP (Autenticación HTTP Básica)
Patator puede hacer un ataque de fuerza bruta contra formularios de autenticación básica HTTP.
```bash
patator http_fuzz url="http://[IP_o_dominio]/login" user=FILE0 password=FILE1 0=<usuarios_wordlist> 1=<contraseñas_wordlist>
```
--> Este comando atacará la página de login con las combinaciones de usuario y contraseña que se encuentran en los wordlists proporcionados.

3. Ataques FTP
Patator también puede ser utilizado para realizar un ataque de fuerza bruta a un servicio FTP, probando diferentes combinaciones de usuario y contraseña.
```bash
patator ftp_login host=[IP_o_dominio] user=FILE0 password=FILE1 0=<usuarios_wordlist> 1=<contraseñas_wordlist>
```

4. Ataques a Otros Servicios
Además de SSH, HTTP y FTP, Patator soporta una gran cantidad de otros servicios como SMTP, POP3, Telnet, MySQL y muchos más. Para usarlo en estos casos, simplemente cambian los módulos y los parámetros específicos para el servicio.

## Opciones de Patator
`-h`: Muestra la ayuda general.
`user=FILE0`: Especifica el archivo de lista de usuarios.
`password=FILE1`: Especifica el archivo de lista de contraseñas.
`0=<wordlist>`: Archivo de palabras para el primer parámetro (usuario o palabra clave).
`1=<wordlist>`: Archivo de palabras para el segundo parámetro (contraseña).

## Ejemplo Completo de Uso
1. Ataque de fuerza bruta a SSH con lista de usuarios y contraseñas:
```bash
patator ssh_login host=192.168.1.10 user=FILE0 password=FILE1 0=usuarios.txt 1=contraseñas.txt
```

2. Ataque de fuerza bruta a un formulario HTTP con login básico:
```bash
patator http_fuzz url="http://192.168.1.10/login" user=FILE0 password=FILE1 0=usuarios.txt 1=contraseñas.txt
```

## Conclusión
Patator es una herramienta extremadamente poderosa y flexible para realizar ataques de fuerza bruta a una amplia variedad de servicios, especialmente útil en auditorías de seguridad y pruebas de penetración. Su capacidad para trabajar con múltiples protocolos la convierte en una opción ideal para los profesionales de la ciberseguridad que necesitan probar la robustez de los sistemas de autenticación.
