# Proxy
## Teoría
#### Propósito
Tiene por objetivo desarrollar la función de ser un intermediario que agrega funcionalidad a una clase, sin tocar la misma.

#### Solución
Definir una clase Proxy con la misma interfaz que el objeto de servicio original. 
Después, se debe actualizar nuestra aplicación para que los clientes se comuniquen con el proxy y no con el servicio destino. Al recibir la solicitud de un cliente, el proxy le enviará al servicio, pero como intermediario podremos realizar operaciones antes o después de enviarle la solicitud.

#### Ventajas
* El proxy funciona incluso si el objeto de servicio no está listo o no está disponible.
* Principio de abierto/cerrado: Podemos introducir nuevos proxies sin cambiar el servicio o los clientes.

#### Desventajas
* Al agregar una capa más entre el cliente y el servicio real, la respuesta puede retrasarse.

## Ejercicios
### Ejercicio 1 - Spotify (clase 5)
El servicio de Spotify pago permite descargar canciones para escuchar offline. Cuando un usuario solicita descargar una canción, el servicio de Spotify comprueba si es un usuario premium, para darle acceso a esta funcionalidad. Los usuarios tienen un identificador y un Enum con el tipo de usuario (“Free”, “Premium”).
Implementar una clase servicioDescarga que permita descargar una canción y mediante el patrón proxy comprobar si es posible hacerlo. 
Crear los casos de prueba necesarios para garantizar la calidad del método descargar().

### Ejercicio 2 - Vacunas
En un centro de vacunación las personas inscriptas y con turno —además de conocer
su nombre, apellido y DNI— tienen asignada una fecha de vacunación y la vacuna que
se les aplicará. Estas pueden concurrir un día posterior a la a fecha asignada, por lo
cual cuando se vacuna es necesario informar, mediante el método vacunar(), que
esta ya fue aplicada. En el momento de la vacunación, se debe registrar la
confirmación con el DNI, fecha y vacuna. Para evitar que la información sea
inconsistente se debe controlar que la fecha sea igual o posterior a la fecha asignada.
Se debe utilizar un proxy para efectuar este control.

Para simplificar el ejercicio, si el registro es correcto se emite un mensaje con la
información registrada.

Crear los casos de prueba requeridos para garantizar la calidad del método vacunar().

### Ejercicio 3 - Movies (clase 6 mesas)
Como cliente, queremos que la aplicación nos permita hacer un pedido con el nombre de la serie y nos envíe el link de reproducción. El único límite impuesto a nuestra petición es que la cantidad de series no puede ser más de 5 por semana. Para poder saber cuántas ya fueron vistas se llevará un contador.
Se propone crear una estructuras de clases similar al ejercicio anterior, con las siguientes clases:

* Una interfaz ISerie que define un método getPelicula que recibe el nombre, devolviendo un string.
* Una clase Serie que implementa la interfaz ISerie y devuelve un string que representa el link y simplemente es el prefijo “www.”, seguido por el nombre de la serie. 
* Una clase SerieProxy con un atributo cantVistas que cuenta las veces que fue pedida una serie y le pide a Serie un link con getPelicula y verifica las veces que se reprodujo alguna serie. Si se supera el valor máximo, lanza una excepción del tipo SerieNoHabilitadaException, creada para tal fin.

En el método main, realizar pedidos de series con el nombre. Mostrar el link de la serie si está habilitada. Si no, mostrar un cartel de “Ha superado la cantidad de reproducciones permitidas”.
Codificar los casos de pruebas que sean requeridos para garantizar la calidad del método getPelicula().

### Ejercicio 4 - Grilla películas
Estamos desarrollando una aplicación de streaming, al estilo Netflix, con el objetivo de
que la usen usuarios de todo el mundo. Por el momento, solo estamos recibiendo
películas para Argentina, Brasil y Colombia. En este caso, necesitamos desarrollar una
funcionalidad en particular.
Como cliente, queremos que la aplicación nos permita hacer un pedido con el nombre
de la película y nos envíe el objeto película que posee el enlace de reproducción. Las
diferentes películas están habilitadas únicamente en uno de los países y nos permiten
verla si estamos en el país correspondiente.
Para poder saber en qué país se encuentra el cliente, se nos ocurrió utilizar la
dirección IP de la solicitud que nos envía. Dado que las direcciones IP tienen un
formato definido por 4 números (del 0 al 255) separados por puntos, quedando como:
255.255.255.255, podemos tomar el primer número de la dirección para saber de qué
país proviene:
* 0 a 49 -> Argentina
* 50 a 99 -> Brasil
* 100 a 149 -> Colombia

Se propone crear:
* Una interfaz IGrillaDePeliculas que define un método getPelicula que recibe el
nombre, devolviendo un objeto película.
* Una clase GrillaDePeliculas que implementa la interfaz IGrillaDePeliculas y
devuelve una película.
* Una clase GrillaDePeliculasProxy que posee un atributo IP y le pide a
GrillaDePeliculas una película —con getPelicula y la “filtra” según el país
(recordar cómo se encuentra el país desde la IP)—. Si no es posible enviarla a
ese país, lanza una excepción del tipo PeliculaNoHabilitadaException, creada
para tal fin.

Se utilizarán las clases:
* Película que posee un nombre, un país y un link de reproducción
—todos string—.
* IP que posee cuatro enteros (números de 0 a 255).

En el método main, realizar pedidos de películas con el nombre y la IP (haciéndolo con
ejemplos de los 3 países). Mostrar el link de la película si está habilitada. Si no, mostrar
un cartel de “Película no disponible en su país”.
Realizar las pruebas necesarias para garantizar la calidad del método getPelicula().


### Ejercicio 3 - Internet
Pensemos en un escenario de la vida real, en algunos lugares, como la universidad o el trabajo, la red que nos conecta a Internet está limitada y no tenemos acceso a todos los sitios. 
Puede ser que tengamos un proxy que esté restringiendo el acceso y en lugar de conectarnos directamente a Internet, estemos comunicándonos con el proxy y sea este el que finalmente se comunica con Internet.

