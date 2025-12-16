# Polimorfismo 

### Explicación del concepto:

El polimorfismo es un fundamento de la Programación Orientada a Objetos que permite que un mismo método o mensaje sea interpretado de distintas maneras según el tipo concreto del objeto que lo recibe. Esto implica que diferentes clases pueden implementar un mismo comportamiento de forma distinta, siempre que compartan una clase base o una interfaz común.

Este principio permite diseñar sistemas más flexibles y extensibles, ya que el comportamiento específico de un objeto se determina en tiempo de ejecución y no en tiempo de compilación.

### Relacion con los principios Solid: 

Principio Abierto/Cerrado (OCP): el polimorfismo permite extender el comportamiento del sistema mediante nuevas clases sin modificar el código existente.
Principio de Inversión de Dependencias (DIP): el código depende de abstracciones (clases base o interfaces) y no de implementaciones concretas.

### Relacion con los patrones de diseño:

El polimorfismo es fundamental en patrones de diseño como:
Observer, donde distintos observadores reaccionan de manera diferente ante un mismo evento.

Factory Method, al permitir que el código cliente trabaje con tipos abstractos y no con clases concretas.

Facade, al delegar internamente comportamientos polimórficos sin exponerlos al cliente.

## Ejemplo en el proyecto

En el Sistema de Gestión de Proyectos Audiovisuales, el polimorfismo se aplica en la jerarquía de usuarios del sistema.  
La clase Usuario define un comportamiento común que es implementado de manera distinta por las clases que representan roles específicos dentro del proyecto.

Las clases Administrador, Diseñador y Asistente heredan de Usuario y redefinen un mismo método para ejecutar acciones acordes a su responsabilidad.

![Polimorfismo](../../diagramas/01-diagrama-clases/Ejemplo-de-Polimorfismo(Santiago-Samitier).png)
- [Ejemplo de Polimorfismo (Codigo del diagrama UML)](../../diagramas/01-diagrama-clases/Ejemplo-de-Polimorfismo(Santiago-Samitier).puml)

### Relación con los diagramas de clase:

El fragmento del diagrama UML seleccionado muestra que las clases Administrador, Diseñador y Asistente heredan de la clase base Usuario y sobrescriben un mismo método. Aunque las clases comparten la misma operación, cada una implementa un comportamiento diferente, lo que evidencia el uso del polimorfismo.

### Justificación técnica del ejemplo (UML):

El diagrama UML muestra una jerarquía donde múltiples clases heredan de Usuario y redefinen un mismo método. Esta estructura permite que un mismo mensaje sea tratado de forma diferente según el tipo concreto del objeto, reflejando claramente el principio de polimorfismo y su correcta aplicación dentro del diseño del sistema.

## Ejemplo de codigo

```java
public abstract class Usuario {

    public abstract void ejecutarRol();
}

public class Administrador extends Usuario {

    @Override
    public void ejecutarRol() {
        // lógica de administración del sistema
    }
}

public class Diseñador extends Usuario {

    @Override
    public void ejecutarRol() {
        // lógica de diseño y revisión de contenidos
    }
}

public class Asistente extends Usuario {

    @Override
    public void ejecutarRol() {
        // lógica de asistencia operativa
    }
}
```


### Justificación técnica del código:

En este fragmento de código, la clase Usuario define un método abstracto que establece un comportamiento común para todos los tipos de usuarios. Las clases derivadas implementan dicho método de acuerdo con su rol específico, proporcionando distintas respuestas ante la misma invocación.

Desde el punto de vista técnico, el sistema puede manipular objetos de diferentes tipos concretos utilizando referencias del tipo Usuario. En tiempo de ejecución, el método ejecutarRol() ejecutado corresponde a la implementación de la subclase concreta, demostrando la aplicación del polimorfismo y permitiendo extender el sistema sin modificar el código existente.
