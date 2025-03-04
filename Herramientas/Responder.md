## Descripción
Responder es una herramienta utilizada en auditorías de seguridad y pruebas de penetración para realizar ataques en redes locales, especialmente en redes Windows. Responder se utiliza para capturar credenciales de autenticación NTLM y otros datos de red al hacer spoofing de servicios comunes, como NetBIOS, DNS y HTTP. Es especialmente útil para obtener hashes de contraseñas y realizar ataques de Pass-the-Hash.
Lo uso por primera vez en [[4. Responder - Web (Local File Inclusion), Responder, John the Ripper y Evil-WinRM]].

## Usos Comunes de Responder
1. Spoofing de Servicios de Red (SMB, HTTP, DNS, etc.)
Responder puede realizar spoofing de servicios comunes de red, como Samba (SMB), NetBIOS y DNS. Esto permite que las máquinas en la red intenten autenticarse contra un servidor falso que responderá con una solicitud de autenticación, capturando así los hashes de contraseñas NTLM.

2. Captura de Hashes de Contraseña NTLM
Una de las funcionalidades más comunes de Responder es capturar los hashes NTLM cuando un cliente intenta autenticarse contra el servidor malicioso montado por la herramienta. Estos hashes pueden ser posteriormente utilizados para realizar un ataque de Pass-the-Hash o ser crackeados usando herramientas como John the Ripper.

3. Montar un Servidor SMB Malicioso
Responder permite montar un servidor SMB malicioso que se presenta como un recurso compartido legítimo en la red. Cuando un cliente intenta acceder a este servidor falso, Responder captura la autenticación NTLM, que puede ser utilizada para realizar ataques de escalada de privilegios.

4. Ejecución de Ataques de Pass-the-Hash
Una vez que Responder ha capturado un hash de autenticación NTLM, el atacante puede usar este hash en lugar de la contraseña real para acceder a otros servicios en la red, como WinRM o RDP, mediante un ataque de Pass-the-Hash.

## Ejemplo de Uso en un Ataque de SMB Falso y Captura de Hash NTLM
1. Ejecutar Responder en una Red Local
```bash
sudo responder -I eth0
```
--> Esto pone a Responder en modo escucha en la interfaz de red especificada (en este caso, eth0), capturando todas las solicitudes de autenticación que pasen por la red.

2. Capturar un Hash NTLM
Cuando un cliente intenta acceder a un recurso compartido SMB o cualquier otro servicio de red en la red local, Responder responderá con una solicitud de autenticación falsa, capturando el hash NTLM.

3. Crackear el Hash NTLM con John the Ripper
Una vez que se ha capturado el hash, puede ser crackeado con herramientas como John the Ripper para obtener la contraseña en texto claro.
```bash
john --wordlist=rockyou.txt hash.txt
```

4. Acceder con Pass-the-Hash mediante Evil-WinRM
Una vez que tienes el hash de la contraseña, puedes usar herramientas como Evil-WinRM para acceder a la máquina remota utilizando el hash, sin necesidad de conocer la contraseña en texto claro.

## Conclusión
Responder es una herramienta potente y flexible para realizar ataques en redes locales, especialmente en entornos Windows. Su capacidad para capturar hashes NTLM mediante spoofing de servicios de red como SMB y DNS la hace fundamental en auditorías de seguridad y pruebas de penetración, permitiendo la escalada de privilegios a través de ataques como Pass-the-Hash.
