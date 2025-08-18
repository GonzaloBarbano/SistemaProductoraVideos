# Introduccion

-**Descripción del paradigma orientado a obejtos:**

Es un paradigma de programación basado en la organización del código en torno a "objetos" que representan entidades del mundo real. Cada objeto encapsula datos y comportamientos que lo definen y lo hacen interactuar con otros objetos. Este enfoque permite mejorar la reutilización del código, la modularidad y la mantenibilidad de los sistemas.

# Fundamentos de la Programacion Orientada a Objetos

-**Abstracción**

La abstraccion facilita la creación de modelos simplificados de sistemas complejos, enfocándose en los aspectos esenciales. Permite ocultar los detalles internos y presentar una interfaz simple y comprensible.

Ejemplo:
Un ejemplo clásico es un coche: para conducir, solo necesitas interactuar con el volante, el acelerador y el freno, sin necesidad de entender cómo funciona el motor o la transmisión.

-**Encapsulamiento**

El encapsulamiento consiste en ocultar los detalles internos de un objeto y exponer solo lo necesario. Solo se pueden modificar o consultar mediante métodos definidos. Esto evita errores y protege la integridad de los datos.

Ejemplo:
Una cuenta bancaria, la cuenta tiene atributos internos como el saldo y el número de cuenta, que son privados y no accesibles directamente desde fuera de la clase. En cambio, se proporciona métodos públicos para depositar, retirar y consultar el saldo.

-**Herencia**

La herencia permite que una clase derive de otra, reutilizando atributos y métodos. Esto permite crear una jerarquía de clases donde las más específicas amplían o especializan a las más generales.

Ejemplo:
Imagina que tienes una bicicleta y una motocicleta.
Ambas tienen ruedas, manubrio y frenos (atributos comunes).
Pero la motocicleta tiene motor, mientras que la bicicleta no

-**Polimorfismo**

El polimorfismo permite que diferentes clases respondan de manera distinta a un mismo método.

Ejemplo:
Se puede tener una clase base Animal con un método hacerSonido(). Las clases Perro y Gato podrían heredar de Animal y redefinir el método hacerSonido() para que cada una haga su sonido específico ("Guau!" para Perro y "Miau!" para Gato). De esta forma, al llamar a hacerSonido() en un objeto Animal, el comportamiento actual será el de la subclase específica (Perro o Gato).
