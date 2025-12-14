# Herencia
 Explicación del concepto

La herencia es un fundamento de la Programación Orientada a Objetos que permite crear nuevas clases a partir de una clase existente.  
La clase base o padre define atributos y métodos comunes, mientras que las clases derivadas o hijas heredan dichas características, pudiendo ampliarlas o especializarlas.

Este mecanismo facilita la reutilización de código, evita la duplicación de lógica común y permite representar jerarquías naturales del dominio del problema dentro del sistema.

Relación con los principios SOLID

Principio Abierto/Cerrado (OCP): la herencia permite extender el comportamiento del sistema mediante nuevas clases hijas sin modificar la clase base.
Principio de Responsabilidad Única (SRP): la clase padre concentra la lógica común, mientras que las clases hijas se enfocan en responsabilidades específicas.

Relación con patrones de diseño

La herencia es un recurso estructural utilizado en distintos patrones de diseño, como:
Factory Method, donde las clases concretas heredan de una clase base o interfaz.

Template Method, donde una clase padre define la estructura general del algoritmo y las clases hijas implementan pasos específicos.

## Ejemplo en el proyecto

En el Sistema de Gestión de Proyectos Audiovisuales, la herencia se aplica en la jerarquía de usuarios del sistema.  
La clase Usuario representa el concepto general de un usuario, definiendo atributos y comportamientos comunes, mientras que las clases Productor y ResponsableEtapa heredan dichas características y agregan responsabilidades específicas según su rol.

![Herencia](../../SistemaProductoraVideos/diagramas/01-diagrama-clases/Ejemplo-de-Herencia(Santiago-Samitier).png)
- [Ejemplo de Herencia (Codigo del diagrama UML)](../../SistemaProductoraVideos/diagramas/01-diagrama-clases/Ejemplo-de-Herencia(Santiago-Samitier).puml)

Relación con diagrama de clase:
El fragmento del diagrama UML seleccionado muestra una jerarquía de herencia en la que la clase Usuario actúa como superclase, concentrando atributos y comportamientos comunes a todos los usuarios del sistema, como la identificación y la autenticación.

Las clases Productor y ResponsableEtapa heredan dichas características y extienden la funcionalidad base incorporando responsabilidades específicas asociadas a cada rol. Esta relación permite reutilizar código común y representar de forma clara las jerarquías naturales del dominio del sistema.

Justificación técnica del ejemplo (UML):

Desde el punto de vista técnico, la herencia se aplica al definir una clase base (Usuario) que centraliza la lógica y los datos compartidos por todos los tipos de usuarios del sistema. Las clases derivadas reutilizan esta funcionalidad heredada y la especializan según su responsabilidad particular, evitando la duplicación de atributos y métodos comunes.

Este diseño facilita la mantenibilidad y extensibilidad del sistema, ya que permite incorporar nuevos tipos de usuarios mediante la creación de nuevas clases hijas sin modificar la clase base ni afectar el comportamiento existente, cumpliendo con los principios de bajo acoplamiento, alta cohesión y con el principio Abierto/Cerrado (OCP) de SOLID.

## Ejemplo de Código
Codigo escrito en java:

public abstract class Usuario {
    protected String nombre;
    protected String email;

    public boolean autenticar() {
        return true;}
}
public class Productor extends Usuario {

    public void crearProyecto() {}
}
public class ResponsableEtapa extends Usuario {

    public void gestionarEtapa() {}
}

Justificación técnica del código:

En este fragmento de código, la clase Usuario actúa como clase base y define atributos y comportamientos comunes a todos los tipos de usuarios del sistema, como la identidad y el proceso de autenticación. Las clases Productor y ResponsableEtapa heredan estos atributos y métodos, reutilizando la lógica común sin necesidad de duplicarla.

Las clases derivadas extienden la funcionalidad heredada incorporando comportamientos específicos asociados a su rol dentro del sistema, lo que permite especializar responsabilidades manteniendo una estructura común. Este uso de la herencia mejora la mantenibilidad del código, ya que cualquier cambio en la lógica compartida puede realizarse en la clase base y propagarse automáticamente a las clases hijas.

Desde el punto de vista del diseño, esta jerarquía favorece la extensibilidad del sistema, permitiendo agregar nuevos tipos de usuarios mediante la creación de nuevas subclases sin modificar la clase Usuario, cumpliendo con el principio Abierto/Cerrado (OCP) de SOLID y promoviendo un diseño con bajo acoplamiento y alta cohesión.