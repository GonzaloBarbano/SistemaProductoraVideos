# Matriz CLAE (CRUD) – [cambiar-estado-etapa]

**Proyecto:** Sistema de Gestión de Proyectos Audiovisuales  
**Caso de Uso:** [CUx - cambiar-estado-etapa]  

---

## 1 Tabla CLAE

> **Estructura:**  
> - **Filas:** Actividades internas del caso de uso (acciones o pasos del flujo).  
> - **Columnas:** Clases del sistema involucradas.  
> - **Celdas:** Letras **C**, **L**, **A**, **E** según la operación que se realiza sobre la clase.  
> - Si no aplica, dejar la celda vacía.  

|Actividad / Clase                  | Responsable de Etapa | Coordinador / Productor | asistente de Producción | Servicio de Notificaciones  |
|-----------------------------------|:--------------------:|:-----------------------:|:-----------------------:|:---------------------------:|
| Validar Reglas de Negocio         |         L            |          L              |                         |                             |
| Alertar Posible Retraso           |         C            |                         |                         |              C              |
| Registrar Auditoría               |                      |          C              |                         |              L              |
| Registrar Comentarios             |                      |          L              |           C             |                             |
| Adjuntar Links a Material         |                      |          L              |           C             |                             |
| Enviar Notificaciones Automáticas |         L            |          L              |                         |              C              |
> **Leyenda:**  
> **C**: Crear – **L**: Leer/Listar – **A**: Actualizar – **E**: Eliminar  

---

## 2 Métodos identificados

> Los métodos se derivan directamente de las operaciones (C/L/A/E) marcadas en la tabla.  
> Cada método deberá existir en la clase correspondiente del **diagrama de clases**, y reflejarse en su **Tarjeta CRC** y en el **diagrama de secuencia** del caso de uso.

| Clase                      | Método                                                          | Tipo (C/L/A/E) | Parámetros (nombre: tipo)                       | Retorno | Actividad asociada                                |
| -------------------------- | --------------------------------------------------------------- | -------------- | ----------------------------------------------- | ------- | ------------------------------------------------- |
| Responsable de Etapa       | `validarReglasNegocio(etapaId: int, nuevoEstado: string)`       | L              | `etapaId: int`, `nuevoEstado: string`           | `bool`  | Validar reglas de negocio del cambio de estado    |
| Responsable de Etapa       | `actualizarEstadoEtapa(etapaId: int, nuevoEstado: string)`      | A              | `etapaId: int`, `nuevoEstado: string`           | `bool`  | Cambiar estado de la etapa                        |
| Coordinador / Productor    | `registrarAuditoria(usuarioId: int, etapaId: int, fecha: date)` | C              | `usuarioId: int`, `etapaId: int`, `fecha: date` | `bool`  | Registrar auditoría del cambio                    |
| Asistente de Producción    | `registrarComentario(etapaId: int, texto: string)`              | C              | `etapaId: int`, `texto: string`                 | `bool`  | Registrar observaciones o comentarios             |
| Asistente de Producción    | `adjuntarLink(etapaId: int, url: string)`                       | C              | `etapaId: int`, `url: string`                   | `bool`  | Adjuntar links a material                         |
| Asistente de Producción    | `gestionarDocumentacion(proyectoId: int)`                       | A              | `proyectoId: int`                               | `bool`  | Gestionar documentación del proyecto              |
| Servicio de Notificaciones | `enviarNotificacion(destinatarioId: int, mensaje: string)`      | C              | `destinatarioId: int`, `mensaje: string`        | `bool`  | Enviar notificaciones automáticas                 |
| Servicio de Notificaciones | `registrarEnvio(etapaId: int, fecha: date, estado: string)`     | C              | `etapaId: int`, `fecha: date`, `estado: string` | `bool`  | Registrar envío en historial de notificaciones    |
| Servicio de Notificaciones | `programarEnvio(fechaHora: datetime)`                           | L              | `fechaHora: datetime`                           | `bool`  | Programar fecha y hora de envío de notificaciones |
---

## 3 Relación con otros artefactos del diseño

> Esta sección documenta la **trazabilidad** del caso de uso con los demás artefactos del modelo.  
> Cada fila establece una correspondencia entre los elementos de la matriz CLAE y los artefactos donde aparecen.

| Elemento | Artefacto vinculado | Archivo / Referencia URL | Descripción de la relación |
|-----------|--------------------|-----------------------|-----------------------------|
| `validarReglasNegocio()` | Tarjeta CRC – responsableDelProyecto | [`04-tarjeta-crc-responsableDelProyecto.md`](../../herramientas-agile/tarjetas-crc/01-tarjeta-crc-proyecto.md) | Figura como responsabilidad: “Autoriza y controla el inicio de las etapas”. |
| `validarReglasNegocio()` | Diagrama de Secuencia – 4 | [`diagramas-secuencia-04.png`](../../diagramas/05-diagramas-secuencia/05-cambiar-estado-etapa-cambiar-estado-de-etapa-exitoso-04.png) | Representa la validación de reglas antes del cambio de estado. |
| `actualizarEstadoEtapa()` | Diagrama de Secuencia – 4 | [`diagramas-secuencia-04.png`](../../diagramas/05-diagramas-secuencia/05-cambiar-estado-etapa-cambiar-estado-de-etapa-exitoso-04.png) | Se ejecuta cuando el Responsable confirma el nuevo estado de la etapa. |
| `registrarAuditoria()` | Tarjeta CRC – Administrador | [`06-tarjeta-crc-administrador.md`](../../herramientas-agile/tarjetas-crc/06-tarjeta-crc-administrador.md) | Definido como responsabilidad de registrar eventos y auditorías. |
| `registrarComentario()` | Tarjeta CRC – Asistente | [`09-tarjeta-crc-asistente.md`](../../herramientas-agile/tarjetas-crc/09-tarjeta-crc-asistente.md) | Figura como responsabilidad de registrar observaciones. |
| `adjuntarLink()` | Tarjeta CRC – Asistente | [`09-tarjeta-crc-asistente.md`](../../herramientas-agile/tarjetas-crc/09-tarjeta-crc-asistente.md) | Se corresponde con la responsabilidad de adjuntar material de apoyo. |
| `enviarNotificacion()` | Diagrama de Secuencia – 4 | [`diagramas-secuencia-04.png`](../../diagramas/05-diagramas-secuencia/05-cambiar-estado-etapa-cambiar-estado-de-etapa-exitoso-04.png) | Refleja el envío automático de una notificación al Coordinador. |
| `registrarEnvio()` | Tarjeta CRC – notificacion | [`05-tarjeta-crc-notificacion.md`](../../herramientas-agile/tarjetas-crc/05-tarjeta-crc-notificacion.md) | Figura como responsabilidad: “Registrar el historial de envíos automáticos”. |
| `registrarEnvio()` | Diagrama de Actividad – 4 | [`diagramas-secuencia-04.png`](../../diagramas/05-diagramas-secuencia/05-cambiar-estado-etapa-cambiar-estado-de-etapa-exitoso-04.png) | Se visualiza como acción “Registrar envío en historial”. |

---

## 4 Issues e inconsistencias detectadas

> Registrar cualquier diferencia encontrada entre esta matriz y los artefactos relacionados.

| URL | Descripción de la inconsistencia | Artefacto relacionado | Acción correctiva | Estado |
|----|----------------------------------|------------------------|-------------------|:------:|
| [#55](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/55)| El método validarReglasNegocio() está en la CLAE pero no figura en la tarjeta CRC del Responsable de Etapa. | Tarjeta CRC – Responsable de Etapa | Agregar responsabilidad “Validar reglas de negocio antes del cambio de estado”. | Pendiente |    

| [#56](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/56)| El método alertarPosibleRetraso() aparece en la CLAE pero no está presente en la CRC del Coordinador/Productor. | Tarjeta CRC – Coordinador/Productor | Incluir esta operación como comportamiento adicional vinculado al monitoreo de etapas. | Pendiente |

| [#56](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/56)| En la CRC del Administrador se menciona la responsabilidad “Designar diseñadores o responsables”, pero ese método no se ve reflejado en la CLAE de UC4. | Tarjeta CRC – Coordinador/Productor | Confirmar si pertenece a otro caso de uso o incluir asignarResponsable() como referencia compartida. | Pendiente |

| [#57](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/57)| En el diagrama de secuencia no se representa la interacción para alertarPosibleRetraso(). | Diagrama de Secuencia – 4 | Añadir una condición alternativa (alt) que muestre el envío de alerta en caso de demora. | Pendiente |

| [#57](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/57)| La actividad “Registrar Auditoría” existe en la CLAE pero no está modelada en el diagrama de secuencia. | Diagrama de Secuencia – 4 | Insertar mensaje interno del sistema registrarAuditoria() después de actualizar estado. | Pendiente |

| [#57](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/57)| La acción “Registrar Auditoría” tampoco está presente en el diagrama de actividad. | Diagrama de Secuencia – 4 | Incorporar acción de registro de auditoría antes de notificar al usuario. | Pendiente |

| [#57](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/57)| El método adjuntarLinksMaterial() está indicado en la CLAE pero no se visualiza en el diagrama de secuencia. | Diagrama de Secuencia – 4 | Agregar mensaje desde el actor Asistente de Producción al sistema adjuntarLinksMaterial(). | Pendiente |

| [#57](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/57)| En el diagrama de secuencia se destruye ServicioNotificaciones al final del flujo, pero en el modelo de clases el objeto se considera persistente. | Diagrama de Secuencia – 4 | Eliminar el destroy o aclarar que se trata de una instancia temporal del servicio. | Pendiente |

| [#57](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/57)| En el diagrama de secuencia no se muestra la verificación de permisos del actor antes de cambiar el estado. |Diagrama de Actividad – 4 | Incluir llamada interna verificarPermisos(actor) en el sistema antes de validar reglas. | Pendiente |

| [#58](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/58)| El método registrarComentarios() aparece en la CLAE, pero en la CRC del Asistente de Producción no figura ninguna responsabilidad relacionada con comentarios. | Tarjeta CRC – Asistente  | Añadir responsabilidad “Registrar y mantener comentarios asociados a etapas”. | Pendiente |
 
| [#59](https://github.com/GonzaloBarbano/SistemaProductoraVideos/issues/59)| En la CRC del Notificación se usa el nombre “Notificacion” (singular), pero en los otros artefactos figura “Servicio de Notificaciones”. | CRC / Diagramas 4 | Unificar nomenclatura en todos los artefactos para mantener consistencia. | Pendiente |

**Estados posibles:** Abierto / Pendiente / Resuelto

---
