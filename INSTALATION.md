# Indicaciones generales
## Estructura de Tryton ERP
- trytond
Trytond es el núcleo principal del proyecto es el encargado de levantar el servicio y crear las tablas en la base de datos.
- tryton 
Es un cliente de escritorio desarrollado en Python usando GTK como interfaz gráfica.
- sao
Es un cliente web que usa node.

Para levantar el todo el stack es necesario por lo menos trytond y sao.

## Pasos para la instalación
Los siguientes pasos se han ejecutado en un sistema operativo OSX y Ubuntu 18.04
1. Instalar las siguientes herramientas
- python3
- virtualenv
- virtualenvwrapper (recomendado)
- node
- git
- grunt
- VisualCode o Pycharm (opcional)
2. Crear un directorio donde se almacenará el proyecto Ejemplo `/home/lugo/lapillaga/Documents/FOLDER_NAME`
3. Clonar trytond desde el repositorio oficial de Tryton o de sus Mirrors dentro de la carpeta creada.
- Mercurial (Repositorio Oficial)
- Gituhub (Mirror de Mercurial)
- Bitbucket (Mirror de Mercurial)
Un mirror es una imagen exacta del repositorio principal para este ejemplo usaremos Github cuyo repositorio se encuentra en
https://github.com/tryton/trytond
4. Después de clonar puedes cambiarte a la rama que desees por default develop.
Actualmente tryton esta en la versión 5.4, pero se encontrará otras versiones.
- LTS (Soporte de 5 años) Versiones: X.0
- Duracción de un año de soporte Versiones: X.2, X.4, X.N
Para ejemplo nos cambiaremos de rama a 5.0 con `git checkout -b 5.0`
5. Crear una base de datos en postgres que se usará en el archivo .conf de configuración.
6. Crear archivo de configuración de tryton y el archivo requirements.txt dentro de la carpeta creada en el paso 2.
Para la ejecución de trytond es necesario crear un archivo con la extensión .conf en el que se indican los parametros
de configuración del server. Documentación: https://docs.tryton.org/projects/server/en/latest/topics/configuration.html#topics-configuration
El archivo requirements.txt será utilizado en los siguientes pasos para instalar las dependencias del entorno virtual.
Los dos archivos se los puede encontrar en el siguiente link.
https://drive.google.com/drive/folders/1BjCSQModuybKm0z6HuG9L7Rmx3Nq9F4S?usp=sharing
7. Abrir el directorio de trytond con el editor de código de preferencia.
8. Crear un entorno virtual con virtualenv con python 3.6 o python 3.7 otro paso alternativo es crear uno desde pycharm en file/settings/build and enviroment/project-interpreter
9. Activar el entorno virtual instalado si usas virtualenvwrapper colocar el comando workon NOMBRE_AMBIENTE_VIRTUAL
Cuando el ambiente este activo se vera el nombre en la consola con unos parentesis (NOMBRE_AMBIENTE_VIRTUAL)
10. Instalar las dependencias del archivo requirements.txt
`pip install -r requirements.txt`
### Instalación de SAO
1. Clonar el proyecto desde https://github.com/tryton/sao dentro de la carpeta creada en el paso 2 de la sección anterior.
2. Cambiarse a la misma rama de trytond en este caso 5.0
3. Instalar node modules con `npm install --production` dentro de la carpeta sao
4. Colocar el comando `grunt`
5. Dentro del archivo de configuración .conf deberá buscar la siguiente linea
root = /home/lugo/Documents/projects/clean/sao
y remplazarla con el directorio donde clono su proyecto sao

### Correr el stack
1. Dentro de una terminal colocar los siguientes comandos
`cd PATH_TO_TRYTOND`
`bin/trytond-admin -c ../tryton.conf -d NOMBRE_BASE_DATOS --all` Con este comando creas las tablas y tambien te pedira un email y una clace.
`bin/trytond -c ../tryton.conf

### Ultimos pasos 
Tryton posee varios modulos previamente desarrollados los mismos que se encuentran en 
https://github.com/tryton/
Para instalarlos deberas clonarlos dentro de la carpeta modules y correr el comando 
`bin/trytond-admin -c ../tryton.conf -d NOMBRE_BASE_DATOS --all` 
recuerda que algunos son modulos dependientes para efectos de prueba puedes clonar country y party.
LISTO!!!!

Happy Codding!!!!

