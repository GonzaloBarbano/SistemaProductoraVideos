# Matriz CLAE (CRUD) – [asignar-responsable-a-etapa]

**Proyecto:** Sistema de Gestión de Proyectos Audiovisuales  
**Caso de Uso:** [CU3 - Asignar Responsable a Etapa]

---

## 1 Tabla CLAE

> **Estructura:**
>
> - **Filas:** Actividades internas del caso de uso (acciones o pasos del flujo).
> - **Columnas:** Clases del sistema involucradas.
> - **Celdas:** Letras **C**, **L**, **A**, **E** según la operación que se realiza sobre la clase.
> - Si no aplica, dejar la celda vacía.

| Actividad / Clase                    | Administrador (Coord/Prod) | Responsable del Proyecto | Asistente | Servicio de Notificaciones |
| ------------------------------------ | :------------------------: | :----------------------: | :-------: | :------------------------: |
| Abrir detalle de proyecto y etapa    |             L              |            L             |     L     |                            |
| Seleccionar "Asignar/Cambiar"        |             L              |                          |           |                            |
| Mostrar selector de usuarios         |             L              |                          |           |                            |
| Validar existencia del usuario       |                            |            L             |           |                            |
| Validar rol permitido para la etapa  |                            |            L             |           |                            |
| Asignar responsable a la etapa       |             L              |            A             |           |                            |
| Registrar historial de asignación    |             L              |                          |           |             C              |
| Notificar nuevo responsable          |                            |                          |           |             C              |
| Confirmar visualmente al coordinador |             L              |                          |           |                            |

> **Leyenda:**  
> **C**: Crear – **L**: Leer/Listar – **A**: Actualizar – **E**: Eliminar

---

## 2 Métodos identificados

> Los métodos se derivan directamente de las operaciones (C/L/A/E) marcadas en la tabla.  
> Cada método deberá existir en la clase correspondiente del **diagrama de clases**, y reflejarse en su **Tarjeta CRC** y en el **diagrama de secuencia** del caso de uso.

| Clase                    | Método                                                                         | Tipo (C/L/A/E) | Parámetros (objetos)                                 | Retorno         | Actividad asociada          |
| ------------------------ | ------------------------------------------------------------------------------ | -------------- | ---------------------------------------------------- | --------------- | --------------------------- |
| Administrador            | `abrirDetalleEtapa(proyecto: Proyecto, etapa: Etapa)`                          | L              | `proyecto: Proyecto`, `etapa: Etapa`                 | `Etapa`         | Abrir detalle               |
| Administrador            | `mostrarSelectorUsuarios()`                                                    | L              | (sin parámetros)                                     | `List<Usuario>` | Mostrar selector            |
| Responsable del Proyecto | `validarUsuarioResponsable(usuario: Usuario, etapa: Etapa)`                    | L              | `usuario: Usuario`, `etapa: Etapa`                   | `bool`          | Validar existencia/rol      |
| Responsable del Proyecto | `asignarResponsableAEtapa(etapa: Etapa, usuario: Usuario)`                     | A              | `etapa: Etapa`, `usuario: Usuario`                   | `bool`          | Asignar responsable         |
| Administrador            | `registrarHistorialAsignacion(etapa: Etapa, usuario: Usuario, actor: Usuario)` | C              | `etapa: Etapa`, `usuario: Usuario`, `actor: Usuario` | `bool`          | Registrar historial         |
| ServicioNotificaciones   | `enviarNotificacionAsignacion(usuario: Usuario, mensaje: string)`              | C              | `usuario: Usuario`, `mensaje: string`                | `bool`          | Notificar nuevo responsable |
| Administrador            | `confirmacionVisualAsignacion(actor: Usuario, etapa: Etapa)`                   | L              | `actor: Usuario`, `etapa: Etapa`                     | `bool`          | Confirmar visualmente       |

---

## 3 Relación con otros artefactos del diseño

> Esta sección documenta la **trazabilidad** del caso de uso con los demás artefactos del modelo.  
> Cada fila establece una correspondencia entre los elementos de la matriz CLAE y los artefactos donde aparecen.

| Elemento                         | Artefacto vinculado         | Archivo / Referencia URL                                                                                                                                                                    | Descripción de la relación                         |
| -------------------------------- | --------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------- |
| `asignarResponsableAEtapa()`     | Tarjeta CRC – Etapa         | [`02-tarjeta-crc-etapa.md`](../tarjetas-crc/02-tarjeta-crc-etapa.md)                                                                                                                        | Operación principal para cambiar el responsable.   |
| `validarUsuarioResponsable()`    | Diagrama de Actividad – CU3 | [`04-actividad-asignar-responsable-etapa-03.png`](../../diagramas/04-diagramas-actividades/04-actividad-asignar-responsable-etapa-03.png)                                                   | Acción que comprueba existencia y rol del usuario. |
| `enviarNotificacionAsignacion()` | Diagrama de Secuencia – CU3 | [`05-asignar-responsable-etapa-asignar-responsable-a-etapa-exitoso-03.png`](../../diagramas/05-diagramas-secuencia/05-asignar-responsable-etapa-asignar-responsable-a-etapa-exitoso-03.png) | Interacción final que notifica al usuario.         |

---

## 4 Issues e inconsistencias detectadas

> Registrar cualquier diferencia encontrada entre esta matriz y los artefactos relacionados.

| URL                                                                        | Descripción de la inconsistencia                                                                                  | Artefacto relacionado                  | Acción correctiva                                                                                      |  Estado   |
| -------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- | -------------------------------------- | ------------------------------------------------------------------------------------------------------ | :-------: |
| [#79](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/79) | `validarUsuarioResponsable()` aparece en la CLAE pero no figura en la CRC del Responsable del Proyecto.           | Tarjeta CRC – Responsable del Proyecto | Agregar responsabilidad “Validar usuario responsable (existencia y rol)”.                              | Pendiente |
| [#80](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/80) | En algunos diagramas todavía se usan parámetros tipo `etapaId` o `usuarioId`.                                     | Diagramas de Secuencia / Actividades   | Reemplazar parámetros por objetos (`Etapa`, `Usuario`) y crear issues de corrección.                   | Pendiente |
| [#81](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/81) | ServicioNotificaciones referenciado como `Notificacion` en CRCs y como `Servicio de Notificaciones` en diagramas. | CRC / Diagramas                        | Unificar nomenclatura en todos los artefactos.                                                         | Pendiente |
| [#82](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/82) | Falta confirmar si la validación de existencia de usuario es local (Responsable) o central (Sistema).             | Diseño / Arquitectura                  | Definir en diseño: si existe un directorio central, mover validación a `Usuario`/`Sistema de Gestión`. |  Abierto  |
