# Principio de Inversión de Dependencias (DIP)

## Propósito y Tipo del Principio SOLID

El Principio de Inversión de Dependencias (DIP) establece que los módulos de alto nivel no deben depender de los de bajo nivel, sino ambos de abstracciones.

---

## Motivación

En el sistema, la clase **Proyecto** dependía directamente de la clase concreta **Notificación**, encargada de enviar mensajes a los usuarios.
Esto generaba acoplamiento fuerte: si cambiaba la forma de enviar las notificaciones (por ejemplo, incorporar correo o WhatsApp), era necesario modificar el código del Proyecto.  
Esto genera rigidez: cualquier cambio en un canal afecta directamente al proyecto.

Con DIP, **Proyecto** depende de una abstracción (**INotificacion**) y no de clases concretas.  
De esta forma, se pueden agregar nuevos canales sin modificar la lógica del proyecto.

---

## Explicación de Clases Abstractas e Interfaces:

Una clase abstracta es una clase que no se puede instanciar directamente y sirve como plantilla para otras subclases. Características principales:

- No puedes crear objetos directamente de ella
- Puede tener métodos abstractos (sin implementación) y métodos concretos (con implementación)
- Puede tener atributos y constructores
- Una clase solo puede heredar de una clase abstracta

En cuanto a las Interface podemos mencionar que es un contrato puro que define qué debe hacer una clase, pero no cómo lo hace. Es como un conjunto de promesas que una clase debe cumplir. Características principales:

- Solo define métodos (tradicionalmente sin implementación, aunque lenguajes modernos permiten métodos default)
- No puede tener atributos de instancia (solo constantes)
- Una clase puede implementar múltiples interfaces
- Define capacidades o comportamientos que una clase puede tener

La Inversión de Dependencias es un principio de diseño que establece que los módulos de alto nivel (la lógica de negocio importante) NO deben depender de los módulos de bajo nivel (los detalles de implementación). En cambio, ambos deben depender de abstracciones.

Invertir la dependencia significa cambiar la dirección de esa relación, insertar una abstracción (interfaz o clase abstracta) en el medio, de tal forma que:

- La clase de alto nivel depende de la abstracción
- La clase de bajo nivel también depende de (implementa) la abstracción

La "inversión" está en que ahora la clase concreta de bajo nivel debe adaptarse a lo que la abstracción define, en lugar de que la clase de alto nivel se adapte a los detalles concretos.

---

## Estructura de Clases

![DIP](../../diagramas/01-diagrama-clases/01-solid-05-dip.png)

---

## Justificación Técnica

Con DIP:

- **Proyecto** no conoce detalles de cada notificación, solo depende de la abstracción **INotificacion**.

- Nuevos canales se integran implementando la interfaz, sin modificar la lógica de **Proyecto**.

Esto mejora la extensibilidad, reduce el acoplamiento y cumple el principio SOLID de inversión de dependencias.
