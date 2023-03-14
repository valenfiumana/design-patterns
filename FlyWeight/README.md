# Flyweight
## Teoría
#### Propósito
El patrón logra lo dicho anteriormente compartiendo partes del estado del objeto entre varios objetos. Es decir, abstrae las partes reutilizables y, en lugar de crear objetos cada vez que sea requerido, podemos reutilizar objetos creados por otras instancias. Esto permite  reducir la capacidad de memoria requerida por la aplicación.

#### Solución
Este patrón cuenta con varios componentes: el cliente es el objeto que dispara la ejecución.
* El FlyweightFactory es la fábrica que utilizaremos para crear los objetos flyweight u objetos ligeros. 
* El flyweight corresponde a los objetos que deseamos reutilizar para que estos sean más ligeros.


#### Ventajas
* Reduce una gran cantidad el peso de los datos en el servidor. 

#### Desventajas
* Consume un poco más de tiempo para realizar las búsquedas.

## Ejercicios
### Ejercicio 1 - Recetario (ComidaFly)
Supongamos que tenemos un recetario que contiene recetas que están en diferentes colecciones como carne; sopas; ensaladas; o en diferentes categorías como comida italiana; mexicana; argentina; rápidas.

La receta para una hamburguesa podría estar en varias secciones: americana, carnes, rapidas, etc. Si necesitáramos tener un objeto receta hamburguesa en cada una de las colecciones sería muy poco performante y se usaría mucha memoria.

Entonces, el cliente pide un objeto a la FlyweightFactory, esta se fija si existe en el caché y en caso contrario crea uno nuevo. Flyweight comparte el estado de los objetos.

### Ejercicio 2 - Bosques (clase7-Flyweight/src/mesas/)
En un negocio necesitan crear árboles para poder ver cuánto lugar ocuparían. El programa que tiene actualmente posee un elevado consumo de los recursos. Necesita crear 1.000.000 árboles. El proceso para crear los árboles son, cada árbol tiene un Alto, Ancho, color y tipo de árbol. Los tipos de árboles que hay son:
* Ornamentales
    * Alto: 200.
    * Horizontal: 400.
    * Color: verde.
* Frutales
    * Alto: 500.
    * Horizontal: 300.
    * Color: rojo.
* Florales
    * Alto: 100.
    * Horizontal: 200.
    * Color: celeste.

El bosque es un conjunto de árboles y permitirá plantar los árboles. ArbolFactory será el lugar donde se almacenarán los diferentes tipos de árboles. Permitirá, antes de crear el objeto, validar si ya existe uno idéntico al que se le está solicitando. De ser así, regresa el objeto existente; de no existir, crea el nuevo objeto y lo almacena en caché para ser reutilizado más adelante.
Se necesita un sistema que muestre 1.000.000 de árboles la mitad rojo y la otra mitad verde y que luego informe por pantalla los árboles y cuanta memoria se está usando.
Usando esta sentencia se podrá ver la memoria usada:
```java
Runtime runtime = Runtime.getRuntime();
System.out.println("Memoria usada: " + (runtime.totalMemory() - runtime.freeMemory()) / (1024 * 1024));

```

### Ejercicio 3 - Computadoras
Un negocio necesita generar computadoras con distintas especificaciones, así como
también reutilizar las mismas especificaciones. Los tipos de computadoras que hay son :
* Windows
    * RAM: 2
    * Disco Duro: 128
* Mac
    * RAM: 16
    * Disco Duro: 500

Es necesario que la aplicación no genere altos costos en en los recursos: tiene que estar
optimizada. Las computadoras tendrán los siguiente atributos:
* Ram
* Disco Duro
* Id
* Contador(servirá para almacenar el número de instancias)

ComputadoraFactory va ser el contenedor de computadoras que almacenará los
diferentes tipos. Se necesitará aplicar si el la computadora existe obtenerla sino generarla.
Necesitamos que nos informe las computadoras creadas.