## Descripción
Nikto es una herramienta de escaneo de vulnerabilidades web de código abierto, diseñada para detectar una amplia gama de vulnerabilidades en servidores web. Su funcionalidad incluye la identificación de configuraciones incorrectas, fallos en la seguridad, y la exposición a posibles ataques. Nikto es útil para realizar auditorías de seguridad web y es capaz de identificar más de 6,700 vulnerabilidades conocidas.

## Usos Comunes de Nikto
1. **Escanear un Servidor Web Básico**
Nikto se utiliza para escanear un servidor web y detectar posibles vulnerabilidades. El comando básico es el siguiente:
```bash
nikto -h http://[IP_o_dominio]
```
--> Esto escaneará el servidor web especificado y buscará una serie de vulnerabilidades conocidas.

2. **Escaneo con Detalles Extremos (Ver más información)**
Para realizar un escaneo más detallado, puedes usar la opción -v para obtener más información durante el escaneo:
```bash
nikto -h http://[IP_o_dominio] -v
```

3. **Escanear un Puerto Específico**
Si el servidor web está escuchando en un puerto distinto al predeterminado (80), se puede especificar el puerto con la opción -p:
```bash
nikto -h http://[IP_o_dominio]:[puerto]
```

4. **Guardar el Reporte en un Archivo**
Para guardar los resultados de un escaneo en un archivo, utiliza la opción -o seguida del nombre del archivo:
```bash
nikto -h http://[IP_o_dominio] -o reporte.txt
```

5. **Escaneo de Vulnerabilidades Específicas**
Nikto permite buscar vulnerabilidades específicas en las cabeceras HTTP o en los métodos utilizados por un servidor web:
```bash
nikto -h http://[IP_o_dominio] -Tuning 1
```
--> Esto limitará el escaneo a ciertas pruebas específicas.

## Ejemplo Completo de Uso
1. Escanear un servidor web en su puerto predeterminado (80):
```bash
nikto -h http://192.168.1.10
```

2. Escanear un servidor web en un puerto específico (8080) y guardar el reporte:
```bash
nikto -h http://192.168.1.10:8080 -o reporte.html
```

3. Escanear con opciones de más detalle:
```bash
nikto -h http://192.168.1.10 -v
```

## Conclusión
Nikto es una herramienta extremadamente útil en pruebas de penetración web. Permite a los auditores de seguridad identificar vulnerabilidades y configuraciones inseguras en servidores web rápidamente, proporcionando una primera línea de defensa en el análisis de la seguridad de aplicaciones web.
