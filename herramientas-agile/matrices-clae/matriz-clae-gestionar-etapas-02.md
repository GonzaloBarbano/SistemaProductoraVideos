# Matriz CLAE (CRUD) – [gestionar-etapas-de-proyecto]

**Proyecto:** Sistema de Gestión de Proyectos Audiovisuales  
**Caso de Uso:** [CU2 - Gestionar Etapas de un Proyecto]

---

## 1 Tabla CLAE

> **Estructura:**
>
> - **Filas:** Actividades internas del caso de uso (acciones o pasos del flujo).
> - **Columnas:** Clases del sistema involucradas.
> - **Celdas:** Letras **C**, **L**, **A**, **E** según la operación que se realiza sobre la clase.
> - Si no aplica, dejar la celda vacía.

| Actividad / Clase                         | Administrador (Coord/Prod) | Responsable del Proyecto | Asistente | Proyecto | Servicio de Notificaciones |
| ----------------------------------------- | :------------------------: | :----------------------: | :-------: | :------: | :------------------------: |
| Abrir lista de etapas                     |             L              |            L             |     L     |          |                            |
| Agregar etapa                             |             L              |                          |           |    C     |                            |
| Editar etapa                              |             L              |            L             |           |    A     |                            |
| Eliminar etapa                            |             L              |                          |           |    E     |                            |
| Validar responsable / fechas              |                            |            L             |     L     |    L     |                            |
| Guardar cambios y registrar evento        |             L              |            L             |     L     |    A     |             C              |
| Notificar responsable (alta/edición/baja) |                            |            L             |           |          |             C              |
| Actualizar vista / tablero                |             L              |            L             |     L     |          |                            |

> **Leyenda:**  
> **C**: Crear – **L**: Leer/Listar – **A**: Actualizar – **E**: Eliminar

---

## 2 Métodos identificados

> Los métodos se derivan directamente de las operaciones (C/L/A/E) marcadas en la tabla.  
> Cada método deberá existir en la clase correspondiente del **diagrama de clases**, y reflejarse en su **Tarjeta CRC** y en el **diagrama de secuencia** del caso de uso.

| Clase                    | Método                                                                      | Tipo (C/L/A/E) | Parámetros (objetos)                                    | Retorno            | Actividad asociada                 |
| ------------------------ | --------------------------------------------------------------------------- | -------------- | ------------------------------------------------------- | ------------------ | ---------------------------------- |
| Proyecto                 | `agregarEtapa(proyecto: Proyecto, etapa: Etapa)`                            | C              | `proyecto: Proyecto`, `etapa: Etapa`                    | `bool`             | Agregar etapa                      |
| Proyecto                 | `editarEtapa(proyecto: Proyecto, etapa: Etapa)`                             | A              | `proyecto: Proyecto`, `etapa: Etapa`                    | `bool`             | Editar etapa                       |
| Proyecto                 | `eliminarEtapa(proyecto: Proyecto, etapa: Etapa)`                           | E              | `proyecto: Proyecto`, `etapa: Etapa`                    | `bool`             | Eliminar etapa                     |
| Responsable del Proyecto | `validarEtapa(etapa: Etapa)`                                                | L              | `etapa: Etapa`                                          | `ValidationResult` | Validar responsable/fechas         |
| Asistente                | `adjuntarMaterial(etapa: Etapa, adjunto: Adjunto)`                          | C              | `etapa: Etapa`, `adjunto: Adjunto`                      | `bool`             | Adjuntar material                  |
| Proyecto / Auditoría     | `registrarEventoEntidad(entidad: object, accion: string, usuario: Usuario)` | C              | `entidad: object`, `accion: string`, `usuario: Usuario` | `bool`             | Guardar cambios y registrar evento |
| ServicioNotificaciones   | `enviarNotificacion(usuario: Usuario, mensaje: string)`                     | C              | `usuario: Usuario`, `mensaje: string`                   | `bool`             | Notificar responsable              |
| Administrador            | `abrirGestionEtapas(proyecto: Proyecto)`                                    | L              | `proyecto: Proyecto`                                    | `List<Etapa>`      | Abrir lista de etapas              |

---

## 3 Relación con otros artefactos del diseño

> Esta sección documenta la **trazabilidad** del caso de uso con los demás artefactos del modelo.  
> Cada fila establece una correspondencia entre los elementos de la matriz CLAE y los artefactos donde aparecen.

| Elemento                   | Artefacto vinculado         | Archivo / Referencia URL                                                                                                                                                          | Descripción de la relación                                |
| -------------------------- | --------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------- |
| `agregarEtapa()`           | Tarjeta CRC – Etapa         | [`02-tarjeta-crc-etapa.md`](../tarjetas-crc/02-tarjeta-crc-etapa.md)                                                                                                              | Aparece como responsabilidad en la CRC de Etapa/Proyecto. |
| `validarEtapa()`           | Diagrama de Actividad – CU2 | [`04-actividad-gestionar-etapas-02.png`](../../diagramas/04-diagramas-actividades/04-actividad-gestionar-etapas-02.png)                                                           | Representa la validación de responsables y fechas.        |
| `registrarEventoEntidad()` | Diagrama de Secuencia – CU2 | [`05-gestionar-etapas-gestionar-etapas-de-un-proyecto-exitoso-02.png`](../../diagramas/05-diagramas-secuencia/05-gestionar-etapas-gestionar-etapas-de-un-proyecto-exitoso-02.png) | Guarda la operación en el historial.                      |
| `enviarNotificacion()`     | Servicio de Notificaciones  | [`diagrama de secuencia`](../../diagramas/05-diagramas-secuencia/05-gestionar-etapas-gestionar-etapas-de-un-proyecto-exitoso-02.png)                                              | Envía aviso al responsable afectado por la modificación.  |

---

## 4 Issues e inconsistencias detectadas

> Registrar cualquier diferencia encontrada entre esta matriz y los artefactos relacionados.

| URL                                                                        | Descripción de la inconsistencia                               | Artefacto relacionado       | Acción correctiva                                     |  Estado   |
| -------------------------------------------------------------------------- | -------------------------------------------------------------- | --------------------------- | ----------------------------------------------------- | :-------: |
| [#75](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/75) | `eliminarEtapa()` no figura explícitamente en la CRC de Etapa. | Tarjeta CRC – Etapa         | Añadir responsabilidad de eliminación de etapa.       | Pendiente |
| [#76](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/76) | `adjuntarMaterial()` aparece en CLAE pero no en secuencia.     | Diagrama de Secuencia – CU2 | Agregar mensaje `adjuntarMaterial()` desde Asistente. | Pendiente |
| [#77](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/77) | Uso de `etapaId` en secuencia/actividad                        | Diagrama / Secuencia        | Reemplazar por `Etapa` como objeto en parámetros.     | Pendiente |
| [#78](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/78) | Notificación de cambios no detallada en secuencia              | Diagrama de Secuencia – CU2 | Añadir interacción a ServicioNotificaciones.          | Pendiente |
