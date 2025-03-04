## Wappalyzer (Extensión de navegador)
### Descripción
Wappalyzer es una herramienta que permite identificar las tecnologías utilizadas en un sitio web, como servidores web, frameworks, bibliotecas JavaScript, sistemas de gestión de contenido (CMS), plataformas de comercio electrónico, y muchas más. Es especialmente útil en pruebas de penetración y auditorías de seguridad para mapear las tecnologías detrás de una página web y encontrar posibles vectores de ataque.

### Usos Comunes de Wappalyzer
1. Detección de Tecnologías Web
Wappalyzer permite descubrir qué tecnologías están siendo utilizadas en un sitio web al realizar un análisis de la página. Esto incluye detectar si la página está usando tecnologías como WordPress, Joomla, Magento, frameworks como React, Angular, y otras bibliotecas o servidores.

2. Auditoría de Seguridad
Al identificar las tecnologías utilizadas, Wappalyzer ayuda a los pentesters a focalizar sus esfuerzos en las posibles vulnerabilidades de las herramientas, CMS o servidores utilizados. Por ejemplo, si identifica un CMS desactualizado o vulnerable, se pueden realizar pruebas para explotarlo.

3. Análisis de Competencia
Es útil también para obtener información sobre los competidores, al analizar qué tecnologías utilizan en sus plataformas web y poder así mejorar nuestras propias implementaciones.

### Ejemplo de Uso de Wappalyzer
1. Uso en Navegador (Extensión)
Puedes instalar Wappalyzer como una extensión en el navegador (Chrome, Firefox) y simplemente navegar por cualquier sitio web. La extensión mostrará las tecnologías detectadas en la barra de herramientas del navegador.

2. Uso en Línea de Comandos (CLI)
Wappalyzer también tiene una versión de línea de comandos que puedes usar para escanear un sitio web:
```bash
wappalyzer https://example.com
```
--> Esto devolverá una lista de las tecnologías detectadas en el sitio.

## WhatWeb (Línea de comandos)
### Descripción
WhatWeb es una herramienta similar a Wappalyzer, pero con un enfoque más detallado y flexible. Permite detectar tecnologías, servidores web, frameworks, sistemas de gestión de contenido (CMS), y más, mediante el análisis del comportamiento de un sitio web y la respuesta de sus cabeceras HTTP. Es especialmente útil en pruebas de penetración y auditorías de seguridad.

### Usos Comunes de WhatWeb
1. Detección Exhaustiva de Tecnologías Web
WhatWeb puede detectar una gran variedad de tecnologías, incluidos servidores web, CMS, frameworks, herramientas de análisis web y mucho más. Además de las tecnologías estándar, WhatWeb también puede identificar tecnologías menos comunes o incluso personalizadas.

2. Auditoría de Seguridad Avanzada
WhatWeb permite realizar auditorías detalladas al identificar tecnologías desactualizadas o vulnerables. Esto es útil para penetration testing ya que permite centrar el análisis en las herramientas o servicios que pueden tener vulnerabilidades conocidas.

3. Configuración Personalizada
A diferencia de Wappalyzer, WhatWeb permite un alto grado de personalización, lo que lo convierte en una herramienta más flexible. Puedes configurar plugins o hacer un escaneo más profundo, lo que puede ser útil para auditar plataformas complejas o sistemas personalizados.

### Ejemplo de Uso de WhatWeb
1. Escaneo Básico de un Sitio Web
Para obtener información sobre las tecnologías de un sitio web, se puede utilizar el siguiente comando:
```bash
whatweb https://example.com
```

2. Escaneo Detallado con Plugins
WhatWeb también soporta plugins que pueden ayudar a identificar tecnologías más específicas:
```bash
whatweb -v --plugins=wordpress https://example.com
```
--> Esto proporcionará detalles más profundos sobre la tecnología de un sitio web, como si está utilizando WordPress y qué versión podría estar en uso.

## Conclusión
Tanto Wappalyzer como WhatWeb son herramientas poderosas para identificar tecnologías web y realizar auditorías de seguridad. Wappalyzer es más fácil de usar y está más orientado al análisis general de tecnologías, mientras que WhatWeb ofrece un enfoque más detallado y configurable, lo que lo hace ideal para pentesters que necesitan realizar un análisis exhaustivo de los sitios web objetivo.
