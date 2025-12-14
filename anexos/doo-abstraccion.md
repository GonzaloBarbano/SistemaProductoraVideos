# Abstracción

Explicación del fundamento: 
La abstracción es el principio del diseño orientado a objetos que permite representar los conceptos esenciales del dominio del problema, ocultando los detalles de implementación que no son relevantes para el uso del sistema. Su objetivo es reducir la complejidad, facilitar la comprensión del modelo y permitir que las dependencias se establezcan sobre conceptos generales y no sobre detalles concretos.

Relación con SOLID y patrones de diseño:

.Se relaciona directamente con el principio de Inversión de Dependencias (DIP), ya que las clases de alto nivel dependen de abstracciones conceptuales y no de clases concretas.

.También se vincula con el principio Open/Closed (OCP), ya que el sistema puede extenderse sin modificar las clases existentes.

.Es un fundamento clave en patrones como Facade, Strategy y Repository, presentes en la arquitectura del proyecto.

## Ejemplo en el proyecto
En el Sistema de Gestión de Proyectos Audiovisuales, la clase Proyecto actúa como una abstracción del concepto central del dominio. Esta clase define las propiedades y comportamientos comunes que todo proyecto debe tener, sin entrar en detalles específicos de implementación interna.

A su vez, otras clases del sistema (como Cliente, ServicioProyecto o los distintos roles de Usuario) interactúan con Proyecto a través de sus métodos públicos, sin conocer ni depender de cómo se calculan internamente sus estados o duraciones.

![Abstracción](../../SistemaProductoraVideos/anexos/Ejemplo-de-abstracción(Santiago-Samitier).png)
- [Ejemplo de abstracción (Codigo del diagrama UML)](../../SistemaProductoraVideos/anexos/Ejemplo-de-abstracción(Santiago-Samitier).puml)

Relación con el diagrama de clases:

El fragmento del diagrama UML seleccionado muestra cómo Proyecto encapsula información relevante (estado, duración planificada y real) y expone únicamente operaciones de alto nivel como actualizarEstado() o calcularDuracionReal(). Esto refleja claramente la abstracción, ya que las clases consumidoras utilizan estas operaciones sin acceder a los detalles internos.

Justificación técnica del ejemplo (UML):

Desde el punto de vista técnico, la abstracción se aplica al definir a Proyecto como un modelo del dominio que concentra la lógica y los datos esenciales relacionados con la gestión de un proyecto audiovisual. Otras clases del sistema interactúan con esta abstracción a través de métodos bien definidos, sin depender de cálculos internos, estructuras de datos o reglas de negocio específicas. Esto permite modificar o extender la lógica interna del proyecto (por ejemplo, cambiar la forma de calcular la duración o el estado) sin impactar en las clases que lo utilizan, cumpliendo con los principios de bajo acoplamiento y alta cohesión.

## Ejemplo de Código
Codigo escrito en java:

public class Proyecto {
private String estado;
private int duracionPlanificada;
private int duracionReal;


public void actualizarEstado(String nuevoEstado) {
this.estado = nuevoEstado;
}


public int calcularDuracionReal() {
return duracionReal;
}
}

Justificación técnica del código:

Este fragmento de código representa la abstracción al definir una clase que modela el concepto de Proyecto mediante atributos y métodos significativos para el dominio. Las clases que utilizan Proyecto no necesitan conocer cómo se calcula la duración real ni cómo se gestiona internamente el estado, sino únicamente invocar los métodos expuestos.
Esto reduce el acoplamiento, mejora la mantenibilidad y permite modificar la lógica interna del proyecto sin afectar al resto del sistema.
