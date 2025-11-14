# Matriz CLAE (CRUD) – [crear-editar-proyecto]

**Proyecto:** Sistema de Gestión de Proyectos Audiovisuales  
**Caso de Uso:** [CU1 - Crear/Editar Proyecto]

---

## 1 Tabla CLAE

> **Estructura:**
>
> - **Filas:** Actividades internas del caso de uso (acciones o pasos del flujo).
> - **Columnas:** Clases del sistema involucradas.
> - **Celdas:** Letras **C**, **L**, **A**, **E** según la operación que se realiza sobre la clase.
> - Si no aplica, dejar la celda vacía.

| Actividad / Clase                      | Administrador (Coord/Prod) | Cliente | Proyecto | Servicio de Notificaciones | Auditoría |
| -------------------------------------- | :------------------------: | :-----: | :------: | :------------------------: | :-------: |
| Abrir formulario Nuevo/Editar          |             L              |    L    |          |                            |           |
| Completar campos del proyecto          |             L              |    L    |          |                            |           |
| Validar campos (obligatorios / fechas) |             L              |         |    L     |                            |           |
| Verificar duplicado de nombre          |             L              |         |    L     |                            |           |
| Persistir proyecto                     |             L              |         |    C     |                            |     C     |
| Registrar auditoría (quién/quándo)     |             L              |         |          |                            |     C     |
| Generar evento de notificación         |             L              |         |          |             C              |           |
| Enviar notificación a interesados      |                            |         |          |             C              |     L     |
| Mostrar confirmación / errores         |             L              |    L    |          |                            |           |

> **Leyenda:**  
> **C**: Crear – **L**: Leer/Listar – **A**: Actualizar – **E**: Eliminar

---

## 2 Métodos identificados

> Los métodos se derivan directamente de las operaciones (C/L/A/E) marcadas en la tabla.  
> Cada método deberá existir en la clase correspondiente del **diagrama de clases**, y reflejarse en su **Tarjeta CRC** y en el **diagrama de secuencia** del caso de uso.

| Clase                   | Método                                                               | Tipo (C/L/A/E) | Parámetros (objetos, no IDs)                            | Retorno            | Actividad asociada                  |
| ----------------------- | -------------------------------------------------------------------- | -------------- | ------------------------------------------------------- | ------------------ | ----------------------------------- |
| Proyecto                | `crearProyecto(proyecto: Proyecto)`                                  | C              | `proyecto: Proyecto`                                    | `bool`             | Persistir proyecto                  |
| Proyecto                | `editarProyecto(proyecto: Proyecto)`                                 | A              | `proyecto: Proyecto`                                    | `bool`             | Persistir proyecto                  |
| Proyecto                | `validarProyecto(proyecto: Proyecto)`                                | L              | `proyecto: Proyecto`                                    | `ValidationResult` | Validar campos / duplicados         |
| Administrador           | `abrirFormularioProyecto(usuario: Usuario)`                          | L              | `usuario: Usuario`                                      | `Form`             | Abrir formulario                    |
| Administrador / Cliente | `completarFormulario(datos: Map<string,object>)`                     | L              | `datos: Map<string,object>`                             | `bool`             | Completar campos                    |
| ServicioNotificaciones  | `generarEventoNotificacion(proyecto: Proyecto, evento: string)`      | C              | `proyecto: Proyecto`, `evento: string`                  | `Evento`           | Generar evento                      |
| ServicioNotificaciones  | `enviarNotificacion(usuarios: List<Usuario>, mensaje: string)`       | C              | `usuarios: List<Usuario>`, `mensaje: string`            | `bool`             | Enviar notificación                 |
| Auditoría               | `registrarEvento(entidad: object, accion: string, usuario: Usuario)` | C              | `entidad: object`, `accion: string`, `usuario: Usuario` | `bool`             | Registrar auditoría                 |
| Proyecto                | `obtenerProyectoParaEdicion(proyecto: Proyecto)`                     | L              | `proyecto: Proyecto`                                    | `Proyecto`         | Mostrar confirmación / cargar datos |

---

## 3 Relación con otros artefactos del diseño

> Esta sección documenta la **trazabilidad** del caso de uso con los demás artefactos del modelo.  
> Cada fila establece una correspondencia entre los elementos de la matriz CLAE y los artefactos donde aparecen.

| Elemento                                    | Artefacto vinculado         | Archivo / Referencia URL                                                                                                                                                         | Descripción de la relación                              |
| ------------------------------------------- | --------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------- |
| `crearProyecto()`                           | Tarjeta CRC – Proyecto      | [`01-tarjeta-crc-proyecto.md.md`](../tarjetas-crc/01-tarjeta-crc-proyecto.md)                                                                                                    | Figura como responsabilidad “Registrar nuevo proyecto”. |
| `validarProyecto()`                         | Diagrama de Secuencia – CU1 | [`05-diagramas-secuencia/05-crear-editar-proyecto-crear-proyecto-exitoso-01.png`](../../diagramas/05-diagramas-secuencia/05-crear-editar-proyecto-crear-proyecto-exitoso-01.png) | Aparece como validación interna del sistema.            |
| `registrarEvento(entidad, accion, usuario)` | Diagrama de Actividad – CU1 | [`04-actividad-crear-editar-proyecto-01.png`](../../diagramas/04-diagramas-actividades/04-actividad-crear-editar-proyecto-01.png)                                                | Acción de auditoría que registra quién y cuándo.        |
| `enviarNotificacion()`                      | Servicio de Notificaciones  | [`diagrama de secuencia`](../../diagramas/05-diagramas-secuencia/05-crear-editar-proyecto-crear-proyecto-exitoso-01.png)                                                         | Acción final del flujo que informa a los interesados.   |

---

## 4 Issues e inconsistencias detectadas

> Registrar cualquier diferencia encontrada entre esta matriz y los artefactos relacionados.

| URL                                                                        | Descripción de la inconsistencia                                                   | Artefacto relacionado             | Acción correctiva                                                              |  Estado   |
| -------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | --------------------------------- | ------------------------------------------------------------------------------ | :-------: |
| [#72](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/72) | Uso de `proyectoId` en diagramas y secuencias — se debe usar el objeto `Proyecto`. | Diagrama de Secuencia / Actividad | Reemplazar parámetros por objetos `Proyecto` y crear issue para actualización. | Pendiente |
| [#73](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/73) | `registrarEvento()` aparece en actividad pero no en la CRC de Auditoría.           | Tarjeta CRC – Auditoría           | Agregar responsabilidad y método `registrarEvento()` en la CRC.                | Pendiente |
| [#74](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/74) | Falta operación `validarProyecto()` documentada en la CRC de Proyecto.             | Tarjeta CRC – Proyecto            | Añadir método de validación.                                                   | Pendiente |
