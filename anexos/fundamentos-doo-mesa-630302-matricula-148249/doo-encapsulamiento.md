# Encapsulamiento 

### Explicación del concepto:

El encapsulamiento es un fundamento de la Programación Orientada a Objetos que consiste en ocultar el estado interno de un objeto y permitir el acceso a sus datos únicamente a través de métodos definidos. De esta forma, se controla cómo se leen o modifican los atributos de una clase, evitando accesos directos que puedan comprometer la consistencia del objeto.

Este principio permite proteger la información interna y garantizar que los cambios de estado se realicen de manera controlada y coherente con las reglas del negocio.

### Relacion con los principios SOLID: 

 Principio de Responsabilidad Única (SRP): El encapsulamiento refuerza este principio al asignar a cada clase la responsabilidad de gestionar y validar su propio estado interno, evitando que otras clases manipulen directamente sus datos.

 Principio de abierto/cerrado (OCP): Al ocultar los detalles internos de implementación, los cambios en la lógica interna de una clase pueden realizarse sin afectar a las clases que la utilizan, favoreciendo la extensibilidad del sistema.

### Relacion con los patrones de diseño:

El encapsulamiento es un principio clave en varios patrones de diseño, ya que permite controlar el acceso a la información interna y proteger la consistencia del sistema.

Facade:
Este patrón oculta la complejidad interna de un subsistema y proporciona una interfaz simple para los clientes, asegurando que las operaciones sobre los objetos internos se realicen de manera controlada y consistente.

## Ejemplo en el Proyecto 

En el Sistema de Gestión de Proyectos Audiovisuales, el principio de encapsulamiento se materializa en la clase Proyecto, la cual mantiene sus atributos internos ocultos y gestiona su acceso mediante una interfaz pública controlada. De este modo, el estado del objeto no puede ser modificado de manera directa, sino únicamente a través de operaciones definidas por la propia clase.

Las demás clases del sistema interactúan con la entidad Proyecto exclusivamente mediante sus métodos públicos, sin acceder ni depender de la representación interna de sus datos. Este enfoque garantiza la integridad del estado del objeto y asegura que cualquier modificación se realice de forma coherente con la lógica del dominio.

![encapsulamiento](../../diagramas/01-diagrama-clases/Ejemplo-de-Encapsulamiento(Santiago-Samitier).png)
- [Ejemplo de encapsulamiento (Codigo del diagrama UML)](../../diagramas/01-diagrama-clases/Ejemplo-de-Encapsulamiento(Santiago-Samitier).puml)

### Relación con el diagrama de clases:

El fragmento del diagrama UML seleccionado evidencia la aplicación del encapsulamiento al definir los atributos de la clase Proyecto con visibilidad privada, restringiendo el acceso directo al estado interno del objeto. En contraposición, la clase expone un conjunto de operaciones públicas que actúan como una interfaz controlada para consultar y modificar dichos atributos.

Este diseño garantiza que cualquier interacción con el estado del objeto se realice de manera segura y coherente, ya que las modificaciones quedan sujetas a la lógica implementada en los métodos de la clase. De esta forma, se preserva la integridad de los datos y se evita que otras clases del sistema alteren el estado interno de manera indebida.

### Justificación técnica del ejemplo (UML):

En el fragmento del diagrama UML se muestra que los atributos de la clase Proyecto se definen con visibilidad privada, mientras que los métodos públicos permiten consultar y modificar el estado del objeto de forma controlada.

Este enfoque garantiza que las reglas de negocio se apliquen correctamente, ya que el estado interno no puede ser accedido ni alterado directamente desde otras clases. En su lugar, cualquier interacción debe realizarse mediante los métodos definidos por la clase, preservando la consistencia y la integridad de los datos.
## Ejemplo de Código


```java
public class Proyecto {

    private String estado;
    private int duracionPlanificada;
    private int duracionReal;

    public Proyecto(int duracionPlanificada) {
        this.estado = "Iniciado";
        this.duracionPlanificada = duracionPlanificada;
        this.duracionReal = 0;
    }

    public String getEstado() {
        return estado;
    }

    public int getDuracionPlanificada() {
        return duracionPlanificada;
    }

    public int calcularDuracionReal() {
        return duracionReal;
    }

    public void actualizarEstado(String nuevoEstado) {
        this.estado = nuevoEstado;
    }
}

```


### Justificación técnica del código:

Desde el punto de vista técnico, el encapsulamiento se materializa en la clase Proyecto mediante la declaración de sus atributos con visibilidad privada, lo que impide su acceso directo desde el exterior y garantiza la protección del estado interno del objeto.

El acceso y la modificación de dichos atributos se realizan exclusivamente a través de métodos públicos, como getEstado() y actualizarEstado(), estableciendo un mecanismo de control sobre los datos y asegurando que cualquier interacción respete las reglas definidas por la clase.

Este enfoque reduce el acoplamiento, mejora la mantenibilidad del sistema y preserva la integridad del modelo, ya que la lógica interna puede evolucionar sin afectar a las clases consumidoras.