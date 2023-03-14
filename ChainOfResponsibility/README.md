# Responsibility Chain
## Teoría
#### Propósito
Es un patrón de diseño de comportamiento que permite pasar solicitudes a lo largo de una cadena de manejadores. 
Al recibir una solicitud, cada uno de ellos, decide si la procesa o la pasa al siguiente manejador.

#### Solución
Crear una cadena con las clases manejadores para que procesen la solicitud del cliente. Cada uno tiene un campo para almacenar una referencia al siguiente manejador de la cadena. 
La solicitud viaja por la misma hasta que todos los manejadores hayan tenido la oportunidad de procesarla
(los manejadores pueden decidir no pasar la solicitud y detener el procedimiento).


#### Ventajas
* Mayor flexibilidad para procesar las peticiones del cliente. Es posible agregar objetos que sepan resolver nuevas responsabilidades o modificar las actuales sin afectar al cliente.
* Menor acoplamiento. Permite que un objeto envíe una petición y sepa que va a ser tratada, pero tanto el emisor como el receptor no conocen nada del otro.

#### Desventajas
* Puede ser complejo implementar la cadena, y si no está bien configurada, puede que no se cubran todas las peticiones.

## Ejercicios
### Ejercicio 1 - calidad de producto
En una empresa se desea controlar la calidad de un producto. Se pasa por tres controles diferentes y en cada uno se verifica si cumple con los estándares de calidad. Según los controles:
* Lote: debe estar entre 1000 y 2000.
* Peso: debe estar entre 1200 y 1300.
* Envase: debe ser igual a “sano” o “casi sano”. 

En caso de que no cumpla con algún criterio debe informarse que fue rechazado. Si cumple con todos los requisitos, debe informarse que fue aceptado.
El artículo pertenece a una clase artículo que tiene cuatro datos:
1. **Nombre**: string.
2. **Lote**: int.
3. **Peso**: int.
4. **Envasado**: string (“sano”, “casi sano”, etc.)

Se desea que una clase AnalistaDeCalidad vaya enviando el artículo a cada uno de los controles. Primero el de lote, si este es correcto, pasará al de control de peso. Si no es correcto, informa que está mal el lote. La secuencia de cada control continúa hasta que, al pasar todos los controles, debe informar que está correcto.
Por último, se debe hacer una clase que cree un artículo y le pida a CompruebaCalidad que lo verifique.
Realizar los casos de prueba necesarios para garantizar la calidad del método validarCalidadDelProducto()


### Ejercicio 2 - Mails
En la empresa llamada Colmena hay tres departamentos: gerencia, comercial y técnico.
Cuando reciben un correo electrónico (en su dominio colmena.com) quieren que se
controle de acuerdo con las reglas de inteligencia artificial de la empresa y enviarlo al
departamento que corresponda.
Nosotros vamos a simular este control suponiendo que:

Para ello vamos a mostrar por pantalla dónde se recibe el pedido en cada caso. El correo
electrónico pertenece a una clase mail que tiene tres datos tipo string: el origen, el
destino y el tema (o subject).
Se desea hacer una clase CompruebaMail que cree una cadena de responsabilidades.
Esta funcionará chequeando cada elemento (parte de la cadena). Si el mail es para
Gerencia, lo informará. Si no, continúa con el siguiente chequeo que prueba si es para
Técnica, y así continuará hasta saber a quién le corresponde. Si no es de nadie, se
marcará como spam.
Por último, desde una clase ProcesaMail, se crea un mail y se le pide a CompruebaMail
que lo procese e informe donde debe ir.
Realizar los casos de prueba necesarios para garantizar la calidad del método
comprobarMail() de la clase CompruebaMail.
