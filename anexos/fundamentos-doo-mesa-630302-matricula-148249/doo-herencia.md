# Herencia
### Explicación del concepto

La herencia es un mecanismo de la Programación Orientada a Objetos que permite definir nuevas clases a partir de clases existentes. La clase derivada hereda
atributos y comportamientos de la clase base, promoviendo reutilización de código y jerarquías lógicas. 

### Relación con los principios SOLID

Principio Abierto/Cerrado (OCP): La herencia permite extender el comportamiento del sistema mediante nuevas clases derivadas sin modificar la clase base.

Principio de Responsabilidad Única (SRP): la clase padre concentra la lógica común, mientras que las clases hijas se enfocan en responsabilidades específicas. Esto permite que cada clase tenga una única responsabilidad bien definida dentro del sistema.  

### Relación con patrones de diseño

La herencia constituye un mecanismo estructural ampliamente utilizado en diversos
patrones de diseño, ya que permite definir jerarquías de clases que comparten una
estructura común y comportamientos reutilizables.

- **Factory Method:**  
  Este patrón utiliza herencia al definir una clase base (o interfaz) que declara un método de creación, sin especificar la clase concreta que será instanciada. Las subclases derivadas implementan dicho método, determinando qué objeto específico se crea.

## Ejemplo en el proyecto

En el Sistema de Gestión de Proyectos Audiovisuales, la herencia se aplica en la jerarquía de usuarios del sistema.
La clase Usuario representa el concepto general de un usuario, definiendo atributos y comportamientos comunes, mientras que las clases Administrador, Diseñador, ResponsableDelProyecto y Asistente heredan dichas características y agregan responsabilidades específicas de acuerdo con su rol dentro del sistema.

![Herencia](../../diagramas/01-diagrama-clases/Ejemplo-de-Herencia(Santiago-Samitier).png)
- [Ejemplo de Herencia (Codigo del diagrama UML)](../../diagramas/01-diagrama-clases/Ejemplo-de-Herencia(Santiago-Samitier).puml)

### Relación con diagrama de clase:
El fragmento del diagrama UML seleccionado muestra una jerarquía de herencia en la que la clase Usuario actúa como superclase, concentrando atributos y comportamientos comunes a todos los tipos de usuarios del sistema, como la información personal y el mecanismo de autenticación.

Las clases Administrador, Diseñador, ResponsableDelProyecto y Asistente heredan dichas características y extienden la funcionalidad base mediante la incorporación de atributos y operaciones específicas asociadas a cada rol. Esta relación permite reutilizar la lógica común, evitar la duplicación de código y representar de manera clara las variaciones de comportamiento dentro del dominio del sistema.

### Justificación técnica del ejemplo (UML):

Desde el punto de vista técnico, la herencia se materializa al definir una clase base (Usuario) que centraliza los atributos y comportamientos comunes a todos los tipos de usuarios del sistema. Las clases derivadas reutilizan esta funcionalidad compartida y la especializan de acuerdo con sus responsabilidades específicas, evitando la duplicación de datos y operaciones.

Este enfoque mejora la mantenibilidad del modelo, ya que cualquier modificación en la lógica común se realiza en la superclase y se propaga automáticamente a las subclases. Asimismo, favorece la extensibilidad del sistema, permitiendo incorporar nuevos tipos de usuarios mediante la creación de nuevas clases derivadas sin necesidad de alterar la estructura existente.


## Ejemplo de Código


```java
public abstract class Usuario {

    protected String nombre;
    protected String apellido;
    protected String rol;
    protected String correo;
    protected String contraseña;

    public Usuario(String nombre, String apellido, String rol, String correo, String contraseña) {
        this.nombre = nombre;
        this.apellido = apellido;
        this.rol = rol;
        this.correo = correo;
        this.contraseña = contraseña;
    }

    public boolean autenticar(String credencial) {
        return credencial != null && credencial.equals(this.contraseña);
    }
}

class Administrador extends Usuario {

    private String permisos;
    private String nivelAcceso;

    public Administrador(String nombre, String apellido, String correo, String contraseña,
                         String permisos, String nivelAcceso) {
        super(nombre, apellido, "Administrador", correo, contraseña);
        this.permisos = permisos;
        this.nivelAcceso = nivelAcceso;
    }

    public void crearProyecto() {
        System.out.println("El administrador crea un proyecto.");
    }

    public void archivarProyecto() {
        System.out.println("El administrador archiva un proyecto.");
    }
}

class Diseñador extends Usuario {

    private String especialidad;

    public Diseñador(String nombre, String apellido, String correo, String contraseña,
                     String especialidad) {
        super(nombre, apellido, "Diseñador", correo, contraseña);
        this.especialidad = especialidad;
    }

    public void subirEntregable() {
        System.out.println("El diseñador sube un entregable.");
    }
}

class ResponsableDelProyecto extends Usuario {

    private String autorizacion;

    public ResponsableDelProyecto(String nombre, String apellido, String correo, String contraseña,
                                  String autorizacion) {
        super(nombre, apellido, "ResponsableDelProyecto", correo, contraseña);
        this.autorizacion = autorizacion;
    }

    public void cambiarEstado() {
        System.out.println("El responsable cambia el estado del proyecto.");
    }
}

class Asistente extends Usuario {

    private String agenda;

    public Asistente(String nombre, String apellido, String correo, String contraseña,
                     String agenda) {
        super(nombre, apellido, "Asistente", correo, contraseña);
        this.agenda = agenda;
    }

    public void coordinarAgenda() {
        System.out.println("El asistente coordina la agenda.");
    }
}


```


### Justificación técnica del código:

El fragmento de código presentado ejemplifica el uso del mecanismo de herencia mediante la definición de una clase base abstracta (Usuario) que concentra los atributos y comportamientos comunes a todos los usuarios del sistema. Esta superclase encapsula la información general de identidad y provee una operación compartida de autenticación, estableciendo una estructura reutilizable para las clases derivadas.

Las clases Administrador, Diseñador, ResponsableDelProyecto y Asistente extienden la clase Usuario, heredando sus atributos y métodos sin necesidad de replicar su implementación. Cada subclase especializa el comportamiento mediante la incorporación de operaciones propias que representan responsabilidades específicas dentro del dominio del sistema, lo que permite modelar variaciones funcionales manteniendo una base conceptual común.

Desde el punto de vista del diseño, este enfoque reduce la duplicación de código, favorece la reutilización de la lógica compartida y mejora la mantenibilidad del sistema, ya que cualquier modificación en la estructura o comportamiento común se realiza en la clase base y se propaga automáticamente a las subclases. Asimismo, la jerarquía facilita la extensibilidad del modelo, permitiendo agregar nuevos tipos de usuarios mediante la creación de nuevas clases derivadas sin alterar las existentes.

