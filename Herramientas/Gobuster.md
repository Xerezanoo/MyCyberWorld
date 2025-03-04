## Descripción
Gobuster es una herramienta rápida y eficiente para fuerza bruta en aplicaciones web. Se usa principalmente para descubrir directorios ocultos, archivos y subdominios mediante listas de palabras (wordlists).
Lo uso por primera vez en [[1. Appointment - Web (SQL Injection, Gobuster dir)]].

1. Uso para Descubrir Directorios y Archivos
```bash
gobuster dir -u http://[IP/TARGET] -w /usr/share/wordlists/[WORDLIST]
```
Ejemplo:
```bash
gobuster dir -u http://10.10.10.100/ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
```
- Opciones útiles:
    - `-x php,txt,html` → Busca extensiones específicas.
    - `-t 50` → Define el número de hilos (por defecto 10).
    - `--wildcard` → Detecta respuestas dinámicas (subdominios wildcard).

Ejemplo buscando archivos .php y .txt:
```bash
gobuster dir -u http://10.10.10.100/ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x php,txt
```

2. Uso para Fuerza Bruta de Subdominios
```bash
gobuster dns -d [DOMINIO] -w /usr/share/wordlists/[WORDLIST]
```
Ejemplo:
```bash
gobuster dns -d example.com -w /usr/share/wordlists/dns/subdomains-top1million-5000.txt
```
--> Esto intentará encontrar subdominios como admin.example.com, dev.example.com, etc.

3. Uso para Enumerar Parámetros en APIs o Web Apps
```bash
gobuster fuzz -u http://[IP/TARGET]/index.php?FUZZ=test -w /usr/share/wordlists/[WORDLIST]
```
Ejemplo buscando parámetros ocultos en un sitio:
```bash
gobuster fuzz -u http://10.10.10.100/index.php?FUZZ=test -w /usr/share/wordlists/parameters.txt
```

## Ejemplo de Uso Completo
1. Escaneo de directorios con extensiones:
```bash
gobuster dir -u http://10.10.10.100/ -w /usr/share/wordlists/common.txt -x php,txt,html -t 50
```
2. Búsqueda de subdominios:
```bash
gobuster dns -d example.com -w /usr/share/wordlists/dns/subdomains-top1million-5000.txt
```
3. Fuerza bruta en parámetros web:
```bash
gobuster fuzz -u http://10.10.10.100/index.php?FUZZ=test -w /usr/share/wordlists/parameters.txt
```
