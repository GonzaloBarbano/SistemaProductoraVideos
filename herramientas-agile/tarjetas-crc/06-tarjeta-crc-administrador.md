| **Nombre de la clase:**                 | Administrador                  |                                                                          |               |
| --------------------------------------- | ------------------------------ | ------------------------------------------------------------------------ | ------------- |
| **Superclase:**                         | Usuario                        |                                                                          |               |
| **Subclase:**                           |                                |                                                                          |               |
| **Responsabilidades**                   | **Colaboradores**              | **Pensamiento del objeto**                                               | **Propiedad** |
|                                         |                                |                                                                          |               |
| Crear un nuevo proyecto                 | Proyecto, Auditoría            | Soy quien inicia el ciclo de vida del proyecto y debo dejar registro.    | permisos      |
| Designar diseñadores o responsables     | Usuario, Proyecto, Auditoría   | Asigno usuarios a proyectos o etapas según roles, registrando la acción. | nivelAcceso   |
| Revisar y archivar proyectos terminados | Proyecto, Cliente, Auditoría   | Garantizo el cierre formal del proyecto y registro el evento.            | registro      |
| Alertar posible retraso en etapas       | Etapa, Notificación, Auditoría | Supervisto el avance y notifico atrasos, dejando constancia.             | monitoreo     |
| Registrar evento de auditoría           | Auditoría                      | Toda acción administrativa debe quedar registrada.                       | trazabilidad  |
