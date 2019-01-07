# Ejercicio para evaluación de candidatos para Developers Java - Nivel Intermedio

## Requisitos

* Recomendado [Java Platform (JDK) 8](http://www.oracle.com/technetwork/java/javase/downloads/index.html)
* [Apache Maven 3.x](http://maven.apache.org/)
* IDE favorito
* Git

## Descripción de la Evaluación

Se proveen dos ejercicios de distinta dificultad. Leer antentamente lo que se pide en cada ejercicio 
y empezar por el que sea más sencillo.


## Ejercicio 1 - Manejador de tareas

Esta aplicación es para un manejador de tareas. 

La intención de la aplicación es la de proveer un CRUD de tareas que son manejadas desde una base 
de datos relacional. 


### Tareas de Backend

Agregar servicios REST para consultar, agregar, actualizar y borrar tareas. 

El servicio debe responder a las siguientes URLs:

*   `api/tasks` - lista todas las tareas con sus asignados
*   `api/tasks/<id>` - detalles de una tarea identificada por su *id*

**Requerimientos de tecnología**: 

*  Los servicios REST pueden ser implementados usando [JAX-RS](https://jax-rs-spec.java.net/) 
   o anotaciones de Spring MVC.

*  Las tareas deben ser modificadas y consultadas a partir de tablas en base de datos. 
   Para el acceso a base de datos se puede usar repositorios de Spring Boot o bien alguna otra 
   tecnología estándar JEE.   

**Requerimientos funcionales**:

*   El servicio que permite actualizar una tarea debe también permitir asignar la tarea a una persona.

*   No se debe de poder asignar a una persona más de 5 tareas (para evitarle la fatiga :-)). 
    La aplicación debe lanzar un error en caso de que se quiera asignar más de 5 tareas a una persona. 

*   El servicio que permite listar tareas también se debe de poder mostrar sus asignados. 
    Es decir, debe haber una relación entre tareas y asignados y el servicio de listado debe 
    reflejar esto.     


### Tareas de Test Unitarios

Escribir un test unitario que verifique el siguiente **requerimiento funcional** mencionado arriba:

>> No se debe de poder asignar a una persona más de 5 tareas (para evitarle la fatiga :-)). 
   La aplicación debe lanzar un error en caso de que se quiera asignar más de 5 tareas a una persona. 

### Guías generales

Las URLs para los servicios REST deben tener el verbo HTTP apropiado para cada operación.

Los servicios deben aceptar y responder en formato JSON. Diseñar el esquema JSON que se crea apropiado dado la estructura de datos proporcionada.
 

## Exercise 2 - Profanity check

You should't allow the user to add task with bad words in their description, but we
don't want to implement this filter, so we need to use a external service.

**Technology requirements**

* You must invoke an external service to check for profanity, here are some simple
  online services:
  * https://www.purgomalum.com/
  * https://www.noswearing.com/index.php
  * https://github.com/insmo/profanity
  
* You must use the spring `RestTemplate` to make the invocations.
* You must provide a test with a mocked response.

**Functional requirements**
 
 * All tasks must be verified
 * No profanity word should appear in the database.
 * You must notify the user when a task has been automatically replaced.

   

# Criterios de evaluación

1.  Correctitud de la solución

    Naturalmente, el proyecto entregado debe ser funncional y compilar. 
    También se va a evaluar *como* la solución presentada resuelve cada problema.
    
2.  Conocmiento de la plataforma Java

    ¿Tu código demuestra conocimiento de las capacidades de la plataforma Java o JavaEE y sus recursos?
    ¿Se supo qué librerias o anotaciones usar para cada caso?

3.  Coding style

    ¿Es bueno tu estilo de código? ¿Encaja con el código base proporcionado?
    ¿Es idiomático de tal forma en que va a ser fácilmente entendido por cualquier Java developer?
    ¿Está adecuadamente (pero no en exceso) documentado?
    
4.  Entendimiento de la especificación

    Se debería poder completar las tareas pedidas solamente leyendo la especificación en este repositorio.
    Las soluciones a las tareas deben ser de acuerdo a lo pedido en este README.
    
5.  Facilidad en probar la solución
    
    ¿Se provee todo lo necesario para ejecutar la solución entregada? Ya sea drivers, documentación 
    adicional de pasos para deploy o ejecución, etc.


# Pasos iniciales

### Clonar el proyecto a tu máquina

Probablmente estas leyendo esto en Github. Si no, puedes encontrar el proyecto 
[en GitHub](https://www.github.com/avolpe/test-java-intermediate).

Para empezar a trabajar, empieza por clonar el repositorio en tu máquina. 
Haz tu trabajo localmente y haz un commit de tus cambios a tu repositorio 
local git a medida que vayas avanzando.


### Ejecutar el proyecto

El proyecto se inicia ejecutando la clase `works.fintech.Application` desde el IDE,
o utilizando maven `mvn spring-boot:run`.


### Manejando la base de datos

Se provee en la carpeta `src/main/resources/db/migration` scripts de creación de 
tablas para los ejercicios.


# Enviando tu código para evaluación

Cuando termines y estes listo para enviar tu enviar tu trabajo, haz un commit de tus 
cambios y utiliza el siguiente comando para generar una serie de archivos `patch` 
con todos tus cambios.

    git format-patch origin/master

Esto va a crear uno o más archivos con extensión `.patch`.

Envia un email con los archivos patch a la persona que te envió este test.
