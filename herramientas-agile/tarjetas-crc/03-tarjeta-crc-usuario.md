|                                      |                                                               |                                                                |                    |
| ------------------------------------ | ------------------------------------------------------------- | -------------------------------------------------------------- | ------------------ |
| **Nombre de la Clase:**              | Usuario                                                       |                                                                |                    |
| **Superclase:**                      |                                                               |                                                                |                    |
| **Subclase:**                        | Administrador, Diseñador, Responsable del Proyecto, Asistente |                                                                |                    |
| **Responsabilidades**                | **Colaboradores**                                             | **Pensamiento del objeto**                                     | **Propiedad**      |
| Registrar datos básicos de identidad | -                                                             | Soy la base de cualquier persona que interactúa en el sistema. | nombre, apellido   |
| Asignar rol en el sistema            | -                                                             | Mi rol define mis permisos y funciones.                        | rol                |
| Permitir autenticación para ingresar | SistemaAutenticacion                                          | Necesito correo y contraseña para validar acceso.              | correo, contraseña |
| Participar en proyectos              | Proyecto                                                      | Mi participación se asocia a tareas o etapas.                  | proyectosAsignados |
