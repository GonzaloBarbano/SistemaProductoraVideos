# Introduccion

-**Descripción del paradigma orientado a objetos:**

Es un paradigma de programación basado en la organización del código en torno a "objetos" que representan entidades del mundo real. Cada objeto encapsula datos y comportamientos que lo definen y lo hacen interactuar con otros objetos. Este enfoque permite mejorar la reutilización del código, la modularidad y la mantenibilidad de los sistemas.

# Fundamentos de la Programación Orientada a Objetos

-**Abstracción**

La abstracción facilita la creación de modelos simplificados de sistemas complejos, enfocándose en los aspectos esenciales. Permite ocultar los detalles internos y presentar una interfaz simple y comprensible.

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
Pero la motocicleta tiene motor, mientras que la bicicleta no.

-**Polimorfismo**

El polimorfismo permite que diferentes clases respondan de manera distinta a un mismo método.

Ejemplo:
Se puede tener una clase base Animal con un método hacerSonido(). Las clases Perro y Gato podrían heredar de Animal y redefinir el método hacerSonido() para que cada una haga su sonido específico ("Guau!" para Perro y "Miau!" para Gato). De esta forma, al llamar a hacerSonido() en un objeto Animal, el comportamiento actual será el de la subclase específica (Perro o Gato).

-**Requisitos Funcionales**

Gestión de Proyectos:

    ◦ Registrar nuevos proyectos con campos básicos como nombre, fechas estimadas de inicio y fin, responsable general del proyecto, estado (en curso, terminado, pausado) y observaciones generales.

    ◦ Cargar y gestionar múltiples proyectos simultáneamente.

    ◦ Visualizar un tablero de control o panel general que permita ver de un vistazo el estado de todos los proyectos (en curso, terminado o pausado).

    ◦ Filtrar la lista de proyectos por estado, responsable y tipo de proyecto (publicidad, videoclip, institucional, etc.).

• Gestión de Etapas y Tareas:

    ◦ Registrar etapas dentro de cada proyecto con campos como nombre de etapa, fechas estimadas de inicio y fin, responsable de etapa, estado de etapa (pendiente, en curso, finalizada) y observaciones específicas de etapa.

• Comunicación y Notificaciones:

    ◦ Notificaciones automáticas por email y WhatsApp cuando una etapa se completa y está lista para el siguiente responsable.

Almacenamiento y Enlaces:
◦ Permitir adjuntar enlaces a carpetas de Drive, Vimeo u otras plataformas donde se guarden archivos brutos, videos editados u otros materiales del proyecto.

-**Requisitos No Funcionales**

• Facilidad de Uso / Intuitividad:

    ◦ La interfaz debe ser simple y fácil de usar.
    ◦ Es una prioridad porque parte del equipo no es muy técnico.
    ◦ La interfaz debe incluir una lista de proyectos, filtros por estado y botones rápidos para cargar avances.

• Accesibilidad y Responsividad:

    ◦ El sistema debe ser una aplicación web.
    ◦ Debe ser accesible y funcional tanto desde computadoras como desde teléfonos celulares (responsivo).

• Persistencia de Datos:

    ◦ La información debe quedar guardada aunque se recargue la página.

# Casos de Uso

### Pedir Proyecto

-**Actor(es):** Cliente, asistente

-**Descripción:** El cliente le hara un pedido al asistente para la creación del proyecto y el asistente registrará dicho proyecto junto con sus características, su fecha de pedido y su fecha de finalización.

-**Flujo principal:**

1. El cliente entra en el contacto del asistente
2. El cliente le envia el pedido del proyecto al asistente
3. El asistente revisa si no hay un proyecto igual al pedido
4. El asistente registra el pedido
5. El asistente le confirma al cliente que su proyecto esta en realización

-**Precondiciones:** Que no haya ningun proyecto igual al pedido

-**Postcondiciones:** Que el cliente no cancele el pedido

### Crear proyecto

-**Actor(es):** Asistente, Administrador

-**Descripción:** El asistente le enviara el registro del pedido al administrador, el administrador revisara el pedido y creara el proyecto, designando al diseñador y el responsable de manejar las etapas del proyecto.

-**Flujo principal:**

1. El asistente registra el pedido
2. El asistente envia el pedido al administrador
3. El administrador revisa el pedido
4. El administrador designa los roles de diseñador y responsable de etapas
5. El administrador crea el proyecto

-**Precondiciones:** Que el pedido se haya enviado

-**Postcondiciones:** Que el pedido no sea cancelado

### Diseñar proyecto

-**Actor(es):** Diseñador, Responsable de etapa

-**Descripción:** El responsable de etapa cambia el estado de la etapa a "en curso" al proyecto, y el diseñador comienza a diseñarlo, cuando finaliza el diseño, se lo envia al administrador, y el responsable de etapa cambia el estado de la etapa a "finalizado"

-**Flujo principal:**

1. El responsable de etapa cambia el estado a "en curso"
2. El diseñador comienza el diseño del proyecto
3. El diseñador finaliza el diseño
4. El responsable de etapa cambia el estado a "finalizado"
5. El diseñador le envia el proyecto al administrador

-**Precondiciones:** Que el administrador haya dado las caracteristicas del diseño

-**Postcondiciones:** Que el pedido no sea cancelado

### Entregar proyecto

-**Actor(es):** Administrador, Asistente, Cliente

-**Descripción:** El administrador recibe el proyecto, lo revisa y se lo envia al asistente, el asistente luego le notifica al cliente que el proyecto ya esta finalizado y se lo entrega al cliente

-**Flujo principal:**

1. El administrador recibe el proyecto finalizado
2. El administrador revisa el proyecto
3. El administrador envia el proyecto al asistente
4. El asistente le notifica al cliente que su proyecto esta finalizado
5. El asistente le entrega el proyecto al cliente

-**Precondiciones:** Que el proyecto este finalizado correctamente

-**Postcondiciones:** Que el cliente no pida rehacer el proyecto

### Archivar proyecto

-**Actor(es):** Administrador

-**Descripción:** El administrador recibe el proyecto, lo revisa y lo archiva en la colección de proyectos del dia en que se finalizo

-**Flujo principal:**

1. El administrador recibe el proyecto finalizado
2. El administrador revisa el proyecto
3. El administrador va hacia la colección de proyectos
4. El administrador entra en la sección del dia en que se finalizo
5. El administrador archiva el proyecto en esa sección

-**Precondiciones:** Que el proyecto este finalizado correctamente

-**Postcondiciones:** Que el cliente no pida rehacer el proyecto.

# Boceto Inicial del Diseño de Clases

![boceto](../diagamas/01-diagrama.png)

[Ir a la sección Diagramas](https://drive.google.com/file/d/1A0j3wN0qF8jCNqg29rq2CDcZzCWzdf0H/view)


