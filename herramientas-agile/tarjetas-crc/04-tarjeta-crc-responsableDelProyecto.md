| **Nombre de la clase:**                                 | Responsable del Proyecto |                                             |               |
| ------------------------------------------------------- | ------------------------ | ------------------------------------------- | ------------- |
| **Superclase:**                                         | Usuario                  |                                             |               |
| **Subclase:**                                           |                          |                                             |               |
| **Responsabilidades**                                   | **Colaboradores**        | **Pensamiento del objeto**                  | **Propiedad** |
| Cambiar estado de una etapa a “En Curso”                | Etapa                    | Soy quien autoriza y controla el inicio.    | autorizacion  |
| Cambiar estado de una etapa a “Terminado”               | Etapa                    | Confirmo que la etapa ha sido completada.   | validacion    |
| Revisar entregables del diseñador                       | Diseñador                | Verifico calidad y cumplimiento.            | observaciones |
| Validar reglas de negocio antes del cambio de estado    | Etapa                    | Aseguro que las políticas se respeten.      | validacionBN  |
| Validar si el usuario es responsable del proyecto       | Usuario                  | Confirmo que el solicitante tiene permisos. | controlAcceso |
| Validar usuario responsable (existencia y rol)          | Usuario                  | Verifico que el usuario seleccionado exista |
| y posea el rol adecuado para asumir la responsabilidad. | validacionUsuario        |
