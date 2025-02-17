## Descripción
John the Ripper (JtR) es una herramienta de cracking de contraseñas de código abierto. Se utiliza para realizar ataques de fuerza bruta, diccionario y ataques híbridos sobre contraseñas cifradas, utilizando diferentes algoritmos de cifrado y hash.
Tipos de Ataques con John the Ripper
- Ataque de Fuerza Bruta: Probar todas las combinaciones posibles de caracteres.
- Ataque de Diccionario: Usar una lista de contraseñas comunes o previamente conocidas.
- Ataque Híbrido: Combina los dos anteriores añadiendo variaciones al diccionario.

1. Uso Básico con Archivos de Contraseñas (Hashes)
- Cracking con un Diccionario:
```bash
john --wordlist=[ruta_diccionario] [archivo_hash]
```
Ejemplo:
```bash
john --wordlist=/usr/share/wordlists/rockyou.txt hash.txt
```

- Cracking con Fuerza Bruta:
```bash
john --incremental [archivo_hash]
```
--> Este ataque prueba todas las combinaciones posibles de caracteres según el conjunto (alfabético, alfanumérico, etc.).

2. Cracking de Hashes Específicos
John the Ripper soporta diferentes algoritmos de hash como MD5, SHA1, NTLM, etc. Puedes especificar el tipo de hash con la opción --format.
```bash
john --format=raw-md5 hash.txt
```
Ejemplo para NTLM:
```bash
john --format=ntlm hash.txt
```

3. Usar "John" en Modo Paralelo (para Velocidad Aumentada)
Para acelerar el proceso, podemos usar múltiples hilos:
```bash
john --wordlist=[ruta_diccionario] --fork=4 [archivo_hash]
```
--> Esto usará 4 hilos para intentar romper las contraseñas más rápido.

4. Visualizar el Progreso
John the Ripper permite ver el progreso del ataque en tiempo real:
```bash
john --status
```

5. Recuperar Contraseñas Crakeadas
Para ver las contraseñas que ya han sido desencriptadas:
```bash
john --show [archivo_hash]
```

## Ejemplo Completo de Uso
1. Crackear una lista de hashes con un diccionario:
```bash
john --wordlist=/usr/share/wordlists/rockyou.txt hash.txt
```
2. Crackear hashes NTLM:
```bash
john --format=ntlm hash.txt
```
3. Crackear contraseñas con fuerza bruta:
```bash
john --incremental hash.txt
```

## Conclusión
John the Ripper es una de las herramientas más poderosas en el campo del cracking de contraseñas. Su versatilidad y velocidad lo hacen esencial en pruebas de penetración para probar la robustez de las contraseñas en sistemas cifrados.
