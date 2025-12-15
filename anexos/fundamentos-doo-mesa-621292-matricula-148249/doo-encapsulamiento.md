# Encapsulamiento 

Explicación del concepto:

El encapsulamiento es un fundamento de la Programación Orientada a Objetos que consiste en ocultar el estado interno de un objeto y permitir el acceso a sus datos únicamente a través de métodos públicos bien definidos. De esta forma, se controla cómo se leen o modifican los atributos de una clase, evitando accesos directos que puedan comprometer la consistencia del objeto.

Este principio permite proteger la información interna, reducir el acoplamiento entre clases y garantizar que los cambios de estado se realicen de manera controlada y coherente con las reglas del negocio.

Relacion con los principios SOLID: 

 Principio de Responsabilidad Única (SRP): la clase es responsable de gestionar y proteger su propio estado.

 Principio de Inversión de Dependencias (DIP): las clases consumidoras dependen de métodos públicos y no de los detalles internos de implementación.

Relacion con los patrones de diseño:

El encapsulamiento es un principio fundamental en patrones de diseño como:

Facade, donde se oculta la complejidad interna de un subsistema y se expone una interfaz simple.

Observer, donde los objetos observadores interactúan con el sujeto a través de métodos públicos, sin acceder directamente a su estado interno.

## Ejemplo en el Proyecto 

En el Sistema de Gestión de Proyectos Audiovisuales, el encapsulamiento se aplica en la clase Proyecto, la cual protege sus atributos internos y controla el acceso y la modificación de su estado mediante métodos públicos.

Las demás clases del sistema interactúan con Proyecto exclusivamente a través de estos métodos, sin acceder directamente a sus atributos internos.

![encapsulamiento](../../SistemaProductoraVideos/diagramas/01-diagrama-clases/Ejemplo-de-Encapsulamiento(Santiago-Samitier).png)
- [Ejemplo de encapsulamiento (Codigo del diagrama UML)](../../SistemaProductoraVideos/diagramas/01-diagrama-clases/Ejemplo-de-Encapsulamiento(Santiago-Samitier).puml)

Relación con el diagrama de clases:

El fragmento del diagrama UML seleccionado muestra que los atributos de la clase Proyecto se definen con visibilidad privada, mientras que las operaciones públicas permiten consultar o modificar el estado del objeto. Esto asegura que las reglas de negocio se apliquen correctamente y que el estado interno no pueda ser alterado de forma incorrecta desde el exterior.

Justificación técnica del ejemplo (UML):

El diagrama UML evidencia el uso del encapsulamiento al mostrar los atributos con visibilidad privada y los métodos públicos que controlan el acceso al estado interno del objeto. Esta separación entre estado y comportamiento expuesto garantiza la integridad de los datos y una interacción segura entre las clases del sistema.

## Ejemplo de Código


```java
public class Proyecto {

    private String estado;
    private int duracionPlanificada;
    private int duracionReal;

    public String getEstado() {
        return estado;
    }

    public void actualizarEstado(String nuevoEstado) {
        this.estado = nuevoEstado;
    }

    public int getDuracionPlanificada() {
        return duracionPlanificada;
    }

    public int calcularDuracionReal() {
        return duracionReal;
    }
}
```


Justificación técnica del código:

En este fragmento de código, los atributos de la clase Proyecto se declaran como privados, impidiendo el acceso directo desde otras clases del sistema. El estado del objeto solo puede ser consultado o modificado a través de métodos públicos, como actualizarEstado() o los métodos de acceso.

Este enfoque garantiza que cualquier cambio en el estado del proyecto se realice de forma controlada y coherente con las reglas del negocio. Además, permite modificar la implementación interna de la clase sin afectar a las clases consumidoras, favoreciendo un diseño con bajo acoplamiento y alta cohesión, y aplicando correctamente el principio de encapsulamiento.