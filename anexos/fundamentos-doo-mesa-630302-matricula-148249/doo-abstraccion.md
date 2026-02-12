# Abstracción

### Explicación del fundamento: 
La abstracción consiste en modelar únicamente las características y comportamientos esenciales de un objeto, ocultando los detalles internos de implementación para reducir la complejidad y mejorar la comprensión del sistema.

### Relación con SOLID y patrones de diseño:

La abstracción se vincula de manera directa con el Principio de Inversión de Dependencias (DIP), ya que promueve que los módulos de alto nivel dependan de conceptos abstractos del dominio en lugar de implementaciones concretas. Esto contribuye a reducir el acoplamiento y aumentar la flexibilidad del sistema.

Asimismo, se relaciona con el Principio Abierto/Cerrado (OCP), dado que el uso de abstracciones facilita la extensión del comportamiento del sistema sin necesidad de modificar las estructuras existentes.

Desde la perspectiva de los patrones de diseño, la abstracción constituye un fundamento esencial en el patrón Facade, donde se expone una interfaz simplificada que oculta la complejidad interna del subsistema, permitiendo que los clientes interactúen con conceptos de alto nivel sin depender de los detalles de implementación.

## Ejemplo en el proyecto
En el Sistema de Gestión de Proyectos Audiovisuales, la clase Proyecto actúa como una abstracción del concepto de proyecto dentro del dominio del sistema. Esta clase define los atributos y comportamientos esenciales que todo proyecto debe poseer, ocultando los detalles internos de implementación y concentrándose en operaciones significativas para el funcionamiento del sistema.

Las demás clases del sistema —como `Cliente`, los servicios de aplicación o los distintos roles de `Usuario`— interactúan con `Proyecto` exclusivamente a través de sus métodos públicos, sin conocer ni depender de la lógica interna utilizada para gestionar estados o realizar cálculos.

![Abstracción](../../diagramas/01-diagrama-clases/Ejemplo-de-abstracción(Santiago-Samitier).png)
- [Ejemplo de abstracción (Codigo del diagrama UML)](../../diagramas/01-diagrama-clases/Ejemplo-de-abstracción(Santiago-Samitier).puml)

### Relación con el diagrama de clases:

El fragmento del diagrama UML seleccionado muestra cómo la clase `Proyecto` encapsula información relevante del dominio, como el estado y las duraciones, y expone únicamente operaciones de alto nivel como `actualizarEstado()`, `calcularDesviacion()` y `estaRetrasado()`.

Esto refleja claramente la aplicación del principio de abstracción, ya que las clases consumidoras utilizan estas operaciones sin acceder a los atributos internos ni depender de los mecanismos de cálculo, interactuando únicamente con el comportamiento observable de la entidad.

### Justificación técnica del ejemplo (UML):

Desde el punto de vista técnico, la abstracción se aplica al definir a Proyecto como un modelo del dominio que concentra la lógica y los datos esenciales relacionados con la gestión de un proyecto audiovisual. Otras clases del sistema interactúan con esta abstracción a través de métodos bien definidos, sin depender de cálculos internos, estructuras de datos o reglas de negocio específicas. Esto permite modificar o extender la lógica interna del proyecto (por ejemplo, cambiar la forma de calcular la duración o el estado) sin impactar en las clases que lo utilizan, cumpliendo con los principios de bajo acoplamiento y alta cohesión.

## Ejemplo de Código


```java
public class Proyecto {

    private String estado;
    private int duracionPlanificada;
    private int duracionReal;

    public void actualizarEstado(String nuevoEstado) {
        this.estado = nuevoEstado;
    }

    public int calcularDesviacion() {
        return duracionReal - duracionPlanificada;
    }

    public boolean estaRetrasado() {
        return duracionReal > duracionPlanificada;
    }
}

```


### Justificación técnica del código:

Este fragmento de código evidencia la abstracción al exponer operaciones de alto nivel que representan comportamiento del dominio (calcularDesviacion, estaRetrasado), ocultando los detalles internos de cálculo y gestión del estado.

Las clases consumidoras interactúan con la entidad Proyecto mediante estos métodos, sin depender de la representación interna de los datos ni de la lógica utilizada, lo que reduce el acoplamiento y mejora la mantenibilidad del sistema.
