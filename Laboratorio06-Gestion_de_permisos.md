# Actividad: Trabajando con Permisos en Linux

## Objetivo

Esta actividad tiene como objetivo que los estudiantes comprendan y practiquen la gestión de permisos en Linux, utilizando los comandos `chmod`, `chown` y `ls`.

## Instrucciones

### 1. Preparación

1. Abrí una terminal en tu distribución de Linux.
2. Crea un directorio llamado `actividad_permisos` y accede a él.

```sh
bazan-darczuk@bazandarczuk-VirtualBox:~/Escritorio$ mkdir actividad_permisos
bazan-darczuk@bazandarczuk-VirtualBox:~/Escritorio$ cd actividad_permisos/
```
### 2. Creación de Archivos y Directorios
Dentro del directorio actividad_permisos, crea los siguientes archivos y un subdirectorio:
```sh
bazan-darczuk@bazandarczuk-VirtualBox:~/Escritorio/actividad_permisos$ touch archivoA.txt archivoB.txt archivoC.txt
bazan-darczuk@bazandarczuk-VirtualBox:~/Escritorio/actividad_permisos$ mkdir subdirectorio
```
### 3. Exploración de Permisos
Usa el comando ls -l para ver los permisos actuales de los archivos y directorios creados.
```sh
bazan-darczuk@bazandarczuk-VirtualBox:~/Escritorio/actividad_permisos$ ls -l
total 4
-rw-rw-r-- 1 bazan-darczuk bazan-darczuk	0 jun 24 00:00 archivoA.txt
-rw-rw-r-- 1 bazan-darczuk bazan-darczuk	0 jun 24 00:00 archivoB.txt
-rw-rw-r-- 1 bazan-darczuk bazan-darczuk	0 jun 24 00:00 archivoC.txt
drwxrwxr-x 2 bazan-darczuk bazan-darczuk 4096 jun 24 00:00 subdirectorio
bazan-darczuk@bazandarczuk-VirtualBox:~/Escritorio/actividad_permisos$

```
2. Anota los permisos actuales de cada archivo y directorio en la siguiente tabla:

| **Nombre**      | **Permisos Actuales**                  |
|-----------------|----------------------------------------|
| archivoA.txt	  |-rw-rw-r-- 1 |
| archivoB.txt    |-rw-rw-r-- 1 |
| archivoC.txt    |-rw-rw-r-- 1 |
| subdirectorio   |drwxrwxr-x 2 |

### 4. Modificación de Permisos
Cambia los permisos de archivoA.txt para que el usuario tenga permisos de lectura y escritura, el grupo solo lectura y otros no tengan permisos.
```sh
bazan-darczuk@bazandarczuk-VirtualBox:~/Escritorio/actividad_permisos$ chmod 640 archivoA.txt
```
Cambia los permisos de archivoC.txt para que el usuario tenga todos los permisos, el grupo solo lectura y otros solo ejecución.
```sh
bazan-darczuk@bazandarczuk-VirtualBox:~/Escritorio/actividad_permisos$ chmod 751 archivoC.txt
```
Cambia los permisos del subdirectorio para que el usuario tenga todos los permisos, el grupo y otros solo tengan permisos de lectura y ejecución.
```sh
bazan-darczuk@bazandarczuk-VirtualBox:~/Escritorio/actividad_permisos$ chmod 755 subdirectorio
bazan-darczuk@bazandarczuk-VirtualBox:~/Escritorio/actividad_permisos$ ls -ld subdirectorio
drwxr-xr-x 2 bazan-darczuk bazan-darczuk 4096 jun 24 00:00 subdirectorio
```
### 5. Verificación de Cambios
```sh
bazan-darczuk@bazandarczuk-VirtualBox:~/Escritorio/actividad_permisos$ ls -l
total 4
-rw-r----- 1 bazan-darczuk bazan-darczuk	0 jun 24 00:00 archivoA.txt
-rw-rw-r-- 1 bazan-darczuk bazan-darczuk	0 jun 24 00:00 archivoB.txt
-rwxr-x--x 1 bazan-darczuk bazan-darczuk	0 jun 24 00:00 archivoC.txt
drwxr-xr-x 2 bazan-darczuk bazan-darczuk 4096 jun 24 00:00 subdirectorio
```
Anota los nuevos permisos de cada archivo y directorio en la siguiente tabla:

| **Nombre**      | **Permisos Actuales**                  |
|-----------------|----------------------------------------|
| archivoA.txt	  |-rw-r----- 1 |
| archivoB.txt    |-rw-rw-r-- 1 |
| archivoC.txt    |-rwxr-x--x 1 |
| subdirectorio   |drwxr-xr-x 2 |

### 6. Cambio de Propietarios
1. Cambia el propietario de archivoA.txt a otro usuario (reemplaza otro_usuario con el nombre de un usuario existente en el sistema o crealo).
```sh
bazan-darczuk@bazandarczuk-VirtualBox:~/Escritorio/actividad_permisos$ sudo chown venus archivoA.txt
```
3. Cambia el grupo de archivoB.txt a otro grupo (reemplaza otro_grupo con el nombre de un grupo existente en el sistema o crealo).
```sh
bazan-darczuk@bazandarczuk-VirtualBox:~/Escritorio/actividad_permisos$ sudo chgrp foot archivoB.txt
```
5. Cambia el propietario y grupo de archivoC.txt a otro_usuario y otro_grupo.
```sh
bazan-darczuk@bazandarczuk-VirtualBox:~/Escritorio/actividad_permisos$ sudo chown serena archivoC.txt
bazan-darczuk@bazandarczuk-VirtualBox:~/Escritorio/actividad_permisos$ sudo chgrp tennis archivoC.txt
```
### 7. Verificación de Cambios de Propietarios
1. Usa el comando ls -l para verificar los cambios en los propietarios y grupos.
```sh
bazan-darczuk@bazandarczuk-VirtualBox:~/Escritorio/actividad_permisos$ ls -l
total 4
-rw-r----- 1 venus     	bazan-darczuk	0 jun 24 00:00 archivoA.txt
-rw-rw-r-- 1 bazan-darczuk foot         	0 jun 24 00:00 archivoB.txt
-rwxr-x--x 1 serena    	tennis       	0 jun 24 00:00 archivoC.txt
drwxr-xr-x 2 bazan-darczuk bazan-darczuk 4096 jun 24 00:00 subdirectorio
bazan-darczuk@bazandarczuk-VirtualBox:~/Escritorio/actividad_permisos$
```

2. Anota los nuevos propietarios y grupos de cada archivo en la siguiente tabla:

| **Nombre**      | **Nuevo propietario** | **Nuevo grupo**|
|-----------------|-----------------|-----------------------|
| archivoA.txt	  |venus            |bazan-darczuk          |
| archivoB.txt    |bazan-darczuk    |foot                   |
| archivoC.txt    |serena           |tennis                 |
| subdirectorio   |bazan-darczuk    |bazan-darczuk          |

### 8. Reflexión
¿Qué diferencias observaste en el comportamiento de los archivos y directorios al cambiar sus permisos y propietarios?
¿Por qué es importante gestionar correctamente los permisos en un sistema Linux?
Gestionar correctamente los permisos y propietarios en un sistema Linux es crucial por varias razones clave: garantiza la seguridad al controlar quién puede acceder y modificar archivos, protege la integridad de los datos evitando modificaciones no autorizadas, facilita la colaboración al permitir accesos controlados en entornos compartidos, y asegura el cumplimiento normativo al establecer políticas de acceso adecuadas. Esto no solo fortalece la seguridad del sistema, sino que también mejora la eficiencia operativa al prevenir errores y facilitar la gestión administrativa de recursos.
