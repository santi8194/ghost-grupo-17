# Reporte Entrega Semana 1 - Curso Pruebas Automatizadas

**Fecha:** 01/04/2023

**Integrantes - Grupo 22:**
- Santiago Alvarez Soto
- Camilo Ramírez Restrepo

**Repositorio:** [*ghost-grupo-22*](https://github.com/santi8194/ghost-grupo-22)
***

## Despliegue de la Aplicación
Se hizo uso de la herramienta *Docker* y *Docker Compose* para desplegar la aplicación *Ghost*, se decidió por el uso de esta herramienta para garantizar uso de las mismas versiones de la aplicación por parte de los miembros del equipo. 

### *Docker Compose*
A continuación se presenta la estructura del archivo *Docker-compose.yml* utilizado para el despliegue de *Ghost*.

    version: '3'
    services:
        ghost-service:
            image: ghost:3.41.1-alpine
            container_name: testing-ghost
            environment:
                - NODE_ENV=development
                - url=http://localhost:3001
            ports:
                - "3001:2368"

### Pasos para Acceder
Para acceder a la interfaz de administrador de *Ghost* es necesario seguir los siguientes pasos:

**NOTA:** Tenga en cuenta que estos pasos requieren que tenga instalado *Docker* y *Docker Compose* en su computador.

1.	Clone el repositorio del grupo, el cual se encuentra disponible en el siguiente [enlace.]( https://github.com/santi8194/ghost-grupo-22)
2.	Abra una terminal en el directorio donde clonó el repositorio.
3.	En la terminal ingrese el comando `docker-compose up --log-level=debug`, este comando le permitirá observar los *logs* generados por el contenedor de *Ghost* que se crea.
4.	Dentro de los *logs* generados en la terminal el contenedor le indicará la *url* asignada, cuando eso pase, abra su navegador de internet e ingrese a la dirección `http://localhost:3001/ghost/` para ingresar a la interfaz de administrador de la aplicación *Ghost*. 

## Lenguajes de Programación y Versiones

En las siguiente tabla se enlista los lenguajes de programación utilizados y en que proporción en la aplicación *Ghost* (Los valores fueron obtenidos del [repositorio](https://github.com/TryGhost/Ghost/tree/3.41.1) de la versión 3.41.1).

<div style="text-align: center;">

|Lenguaje de Programación|Porcentaje de aplicación|
|------------------------|------------------------|
|*JavaScript*|80.1%|
|*Handlebars js*|10.4%|
|*CSS*|8.3%|
|*HTML*|1.2%|
</div>

En cuanto a las versiones utilizadas para la creación de la imagen de *Docker*, en la siguiente imagen se muestran las que fueron utilizadas para la construcción de la imagen [*ghost:3.41.1-alpine*]( https://hub.docker.com/layers/library/ghost/3.41.1-alpine/images/sha256-5303edd44015485fcabe5cca511ac80e151f2f50e0b39abbfa07c148b8873795?context=explore).

<div style="text-align: center;">

|Objeto|Versión|
|-----|--------|
|*Node.js*| 10.20.1|
|*Yarn*| 1.22.5|
|*Ghost-CLI*| 1.15.3|
|*Ghost*| 3.41.1|
</div>

## Arquitectura
A continuación se presentan los aspectos encontrados después de hacer la revisión del código fuente de la aplicación.

### Arquitectura de la Aplicación

***Acá hay que detallar bien y organizar mejor***
- Basada en servicios.
- Core es un RESTFUL JSON API
- Bookshelf ORM
- Custom Storage Adapters

### Modelo de Dominio 
Diagrama de clases UML con las entidades, atributos, tipos de datos y relaciones principales encontradas durante la exploración del código fuente.

<p style="text-align:center">
  <img src="../ghost-grupo-22/imagenes/DiagramaClases.PNG"> </img>
</p>

### Modelo de *GUI*
***Acá va el modelo gui ....***

## Funcionalidades
Se enlistan acá algunas de las funcionalidades de la aplicación encontradas después de hacer una exploración:

1. **Tutorial explicativo de botones y flujo de trabajo**: 
   Al iniciar la aplicación se le muestra al usuario una descripción corta de los botones uno por uno al darle clic en siguiente. 

2. **Editor de contenido para *Posts* y para *Pages***:
    - Editar el contenido del Post usando *Markdown*.
    - Opciones para insertar imagen, *markdown*, *html*, una galería de imágenes, un divisor, marcador, contenido visible únicamente por *email*. 
    - Opciones para embedir contenido de las fuentes: *youtube, twitter, unsplash, vimeo, codepen, spotify, soundcloud* o una *url*. 

3. **Administrar Posts CRUD:**
   - Utilizar el editor de contenido.
   - Editar la información SEO para el Post.
   - Agendar una fecha para la publicación de un Post
   - Guardar como borrador.
   - Inyectar código a la cabecera y el *footer* del Post.

4. **Administrar Pages CRUD:**
   - Utilizar el editor de contenido.
   - Editar la información SEO para el Post.
   - Agendar una fecha para la publicación de un Page. 
   - Guardar como borrador. 
   - Inyectar código a la cabecera y el *footer* del Page. 

5. **Administrar Tags CRUD:**
   - Formulario para información general del Tag.
   - Editar la información SEO para el Tag. 
   - Inyectar código a la cabecera y el **footer** del Tag. 

6. **Administrar usuarios Staff:**
   - Invitar usuario usando correo electrónico y asignando un *Role (Administrador, Editor, Author, Contributor)*. 
   - Editar información general del usuario. 
   - Subir una foto de perfil y de portada. 
   - Cambiar contraseña verificando la nueva. 
   - Mostrar *token* de acceso. 
   - Regenerar *token* de acceso. 

7. **Administrar configuración general de la aplicación:**
   - Editar el titulo y descripción del sitio. 
   - Configurar la zona horaria que se usará en todas las publicaciones. 
   - Configurar el lenguaje que se usará en toda la plataforma. 
   - Subir icono para el sitio web. 
   - Subir logo del sitio web. 
   - Subir foto de portada para el sitio web. 
   - Editar meta-información para SEO. 
   - Asociar redes sociales. 
   - Opción para hacer el sitio privado requiriendo una contraseña para acceder o que sea público.

8. **Administrar configuración de diseño:**
   - Crear una cantidad N de enlaces para la navegación. 
   - Crear una cantidad N de enlaces para la navegación secundaria. 
   - Mostrar 4 plantillas que el usuario podrá instalar. 
   - Dar enlace a mercado de plantillas. 
   - Dar enlace a documentación para desarrolladores de plantillas. 
   - Mostrar plantilla instalada con opción para descargar el código. 
   - Botón para subir y utilizar una plantilla. 

9. **Administrar las integraciones:** 
    - Mostrar las 6 integraciones principales que se pueden configurar. 
    - Mostrar un botón con un enlace a mercado de integraciones para **ghost**. 
    - Mostrar la lista de integraciones que están preinstaladas. 
    - Configurar cada integración.

10. **Crear una integración customizada:** 
    - Editar nombre y descripción. 
    - Dar claves de API de contenido, admin y la *url* del API. 
    - Configurar *webhooks* con nombre, evento, y *url *destino. 

