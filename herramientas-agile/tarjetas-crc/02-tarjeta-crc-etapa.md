| **Nombre de la clase:**                           | Etapa                    |                                                |                       |
| ------------------------------------------------- | ------------------------ | ---------------------------------------------- | --------------------- |
| **Superclase:**                                   |                          |                                                |                       |
| **Subclase:**                                     |                          |                                                |                       |
| **Responsabilidades**                             | **Colaboradores**        | **Pensamiento del objeto**                     | **Propiedad**         |
| Configurar pasos según el proyecto                | Proyecto                 | Soy la unidad secuencial del proyecto.         | pasos                 |
| Registrar estado (pendiente, en curso, terminado) | Responsable del Proyecto | Mi estado muestra el progreso actual.          | estado                |
| Registrar fechas estimadas de inicio y fin        | Notificacion             | Guardo planificación para detectar demoras.    | fechaInicio, fechaFin |
| Calcular tiempos reales de ejecución              | Proyecto                 | Comparo lo planificado con lo ejecutado.       | tiempoReal            |
| Eliminar etapa del proyecto                       | Proyecto / Administrador | Puedo ser removida si la planificación cambia. | eliminacion           |
