# Polimorfismo 

### Explicación del concepto:

El polimorfismo es un fundamento de la Programación Orientada a Objetos que permite que un mismo método o mensaje sea interpretado de distintas maneras según el objeto que lo recibe. Esto implica que diferentes clases pueden implementar un mismo comportamiento de forma distinta.

### Relacion con los principios Solid: 

El polimorfismo se vincula de forma directa con varios principios de SOLID. En particular, se relaciona con el Principio Abierto/Cerrado (OCP), ya que permite extender el comportamiento del sistema mediante nuevas clases que implementan o redefinen operaciones existentes, sin necesidad de modificar el código ya desarrollado.

Y tambien se asocia con el Principio de Sustitución de Liskov (LSP), dado que las clases derivadas deben poder sustituir a su clase base sin alterar el correcto funcionamiento del sistema. Esto garantiza que las distintas implementaciones polimórficas mantengan la coherencia del modelo y respeten los contratos definidos por la abstracción común.

### Relacion con los patrones de diseño:

El polimorfismo constituye un mecanismo central en numerosos patrones de diseño, ya que permite definir comportamientos generales que pueden ser implementados de distintas maneras por diferentes clases.

Observer: el polimorfismo permite que múltiples objetos observadores compartan una interfaz común y reaccionen de forma diferente ante un mismo evento o notificación emitida por el sujeto. Cada observador implementa su propia lógica sin que el emisor necesite conocer los detalles concretos.

Factory Method: este patrón se apoya directamente en el polimorfismo al trabajar con tipos abstractos o interfaces. El código cliente manipula objetos a través de una abstracción común, mientras que las subclases determinan qué tipo concreto de objeto se instancia.

## Ejemplo en el proyecto

En el Sistema de Gestión de Proyectos Audiovisuales, el polimorfismo se manifiesta en la interacción con los distintos tipos de usuarios del sistema. Aunque todos los usuarios comparten una estructura común definida por la clase base Usuario, cada rol del sistema puede redefinir o especializar determinados comportamientos según sus responsabilidades específicas.

Por ejemplo, diferentes tipos de usuarios —como Productor o ResponsableEtapa— pueden implementar de manera distinta operaciones heredadas o comunes, permitiendo que el sistema invoque los mismos métodos sobre objetos conceptualmente similares, pero obteniendo resultados acordes al tipo concreto de cada instancia.

De esta forma, el sistema puede trabajar con referencias del tipo general Usuario sin depender de las clases específicas, delegando el comportamiento en tiempo de ejecución. Este enfoque reduce el acoplamiento, favorece la extensibilidad y permite incorporar nuevos roles sin alterar la lógica existente.

![Polimorfismo](../../diagramas/01-diagrama-clases/Ejemplo-de-Polimorfismo(Santiago-Samitier).png)
- [Ejemplo de Polimorfismo (Codigo del diagrama UML)](../../diagramas/01-diagrama-clases/Ejemplo-de-Polimorfismo(Santiago-Samitier).puml)

### Relación con los diagramas de clase:

El polimorfismo se refleja en el diagrama de clases a través de la jerarquía de generalización establecida entre la clase abstracta Usuario y sus clases derivadas (Administrador, Diseñador, ResponsableDelProyecto , Asistente y responsableEtapa).

En dicho diagrama, Usuario define atributos y comportamientos comunes a todos los actores del sistema, constituyendo una abstracción que representa el concepto general de usuario. Las clases especializadas heredan esta estructura y pueden proporcionar implementaciones particulares de los métodos definidos en la superclase, o bien extender su comportamiento mediante nuevas operaciones.

### Justificación técnica del ejemplo (UML):

El polimorfismo se justifica técnicamente en la jerarquía de herencia entre la clase abstracta Usuario y sus subclases. Esta estructura permite manipular distintos tipos de usuarios mediante una referencia común, delegando el comportamiento concreto en la implementación específica de cada clase derivada.

El diagrama evidencia cómo un mismo mensaje puede producir resultados diferentes según el tipo real del objeto, garantizando flexibilidad, bajo acoplamiento y facilidad de extensión del sistema.

## Ejemplo de codigo

```java
public abstract class Usuario {

    protected String nombre;
   protected String correo;

    public Usuario(String nombre, String correo) {
        this.nombre = nombre;
        this.correo = correo;
    }

    public abstract void mostrarPanel();
}

public class Productor extends Usuario {

    public Productor(String nombre, String correo) {
        super(nombre, correo);
    }

    @Override
    public void mostrarPanel() {
        System.out.println("Panel del productor: creación y gestión de proyectos");
    }
}

public class ResponsableDeEtapa extends Usuario {

    public ResponsableDeEtapa(String nombre, String correo) {
        super(nombre, correo);
    }

    @Override
    public void mostrarPanel() {
        System.out.println("Panel del responsable de etapa: seguimiento y control de tareas");
    }
}

```


### Justificación técnica del código:

Este fragmento demuestra el polimorfismo mediante la clase abstracta Usuario, que define el método abstracto mostrarPanel(). Las clases Productor y ResponsableDeEtapa heredan de esta abstracción e implementan dicho método de acuerdo con su responsabilidad específica dentro del sistema.

Aunque ambos objetos pueden manipularse a través de referencias del tipo Usuario, el comportamiento ejecutado depende del tipo concreto del objeto en tiempo de ejecución. De esta forma, un mismo mensaje (mostrarPanel) produce resultados diferentes según la clase que lo reciba.
