# Entendimiento del Proceso — Sistema de Gestión MP 2026

**Documento vivo.** Aquí se acumula el entendimiento de **mi trabajo** (el del encargado de Equipamiento Clínico del HHHA), el **porqué** de cada cosa que pido y cómo la aplicación me apoya. Se actualiza con **cada ajuste**. Cuando ya no haya más ajustes, esto es lo que define la **aplicación oficial final** que se adapta a mi día a día. Está escrito en primera persona, tal como lo expliqué, para poder leerlo y confirmar que se entendió todo. Si algo no calza con la realidad, se corrige aquí primero.

*Última actualización: 2026-06-16 · App build 2026-06-16.37*

## 1. Quién soy y cuál es mi foco

Soy el encargado del **Equipamiento Clínico del HHHA** y gestiono el **Programa de Mantenciones Preventivas 2026 (MP 2026)** de ~966 equipos.

**Mi foco real no es llenar planillas: es saber en todo momento el estado de cada equipo y asegurar su operatividad.** El último estado de un equipo vale más que el detalle histórico. Todo lo que hago (preventivos, reprogramaciones, correctivos, pendientes) existe para que los equipos estén operativos y para dejar constancia oficial de lo que se hizo.

## 2. La idea central: dos mundos que se complementan

Trabajo con **dos soportes**, y entender la diferencia es la clave de todo:

| | **La carta (Excel)** | **La aplicación** |
| --- | --- | --- |
| Qué es | El **documento oficial** | El **detalle y el borrador** |
| Qué guarda | **Solo resultados** (códigos: Si, C1–C8, FS, No, NU, Baja, Si-RA) | **Todo el detalle** que la carta no guarda (ejecutor, fechas reales, observaciones, gestiones, documentos, firmas, expedientes…) |
| Estado | Lo que está en la carta es **oficial** | Lo que registro en la app es **borrador** hasta que lo oficializo |

**La carta solo registra resultados, no detalles.** Por eso la aplicación me ayuda: ahí pongo el detalle, hago seguimiento y veo qué falta.

**El puente entre los dos mundos** es la regla **Borrador → Oficial**: lo que registro en la app como *Borrador* pasa a *Oficial* cuando **recargo la carta** y esa mantención ya aparece con su resultado. Si no aparece, sigue como borrador.

*En una frase: **la app es donde trabajo y acumulo el detalle; la carta es donde queda lo oficial.***

## 3. El flujo de documentos (el corazón de mi día a día)

Este es el ciclo que repito todo el tiempo:

1. **Recibo un documento** (un informe, un reporte, una orden, un reporte de reprogramación…).
2. **Lo ingreso en la aplicación** con todo su detalle (la carta no guarda ese detalle).
3. **Hago seguimiento hasta tenerlo completo** ("hasta la fecha"): la app me ayuda a ver qué le falta a ese documento/gestión.
4. Cuando el documento **ya no le falta nada**:
   - lo **agrego a la carpeta física del equipo** (cada equipo tiene su **N° de Carpeta**),
   - lo **actualizo en la carta (Excel)** escribiendo el resultado,
   - y al **recargar la carta** en la app, **queda oficial**.

La aplicación, entonces, es mi **mesa de trabajo**: me ordena los documentos en curso, me dice qué falta para cerrar cada uno, y cuando lo oficializo en la carta, todo queda consistente.

## 4. Mantenimiento Preventivo (MP)

- Cada equipo tiene su **programación anual** por mes (X programada, R reprogramada, RA reprogramada de año anterior, PM puesta en marcha).
- Cuando ejecuto un preventivo registro el detalle en la app: fecha, ejecutor, resultado, observaciones, **estado del equipo** y el **tipo de mantenimiento: Interno o Externo**.
- Si queda una **gestión pendiente**, la app me crea un **pendiente** con su lista de trabajo:
  - **Interno** → protocolo de mantenimiento interno.
  - **Externo** → protocolo interno **y** externo.
  - Cada protocolo se marca **Sí / No / Imprimir / Gestión**, admite comentarios, y cuando lo dejo en **Gestión** puedo abrir **subtareas** para detallar qué hay que gestionar.

**Por qué:** el resultado va a la carta, pero el *cómo* y el *qué falta* viven en la app.

## 5. Reprogramaciones (cuando una preventiva no se puede hacer)

Cuando una MP no se puede ejecutar, se **reprograma** con una **causal C1–C8** (p. ej. *C6: no disponibilidad de horas del servicio técnico externo*). Esto **no es solo escribir un código**: detrás hay un **documento (reporte de reprogramación) que debo tramitar**.

**El ciclo del reporte de reprogramación (y el porqué de cada paso):**

1. **Generar el documento** — el reporte lo genero yo; lleva la **causal** (p. ej. C6) y la **fecha** de la mantención reprogramada (p. ej. 30-04-2026).
2. **Imprimirlo.**
3. **Firmas** — lleva **dos**: la del **supervisor del servicio clínico** y la del **jefe de equipos médicos**. *(Por eso me conviene agrupar las reprogramaciones por servicio: junto las de cada servicio para conseguir la firma de su supervisor de una sola vez.)*
4. **Oficializar** — recién cuando el documento está **firmado**, escribo el código (C6) en la **carta (Excel)**, en el Resultado del mes que corresponde, y lo recargo. Ahí pasa de borrador a **oficial**.
5. **Cerrar el pendiente.**

**Por qué este orden:** mientras no esté firmado, no es oficial. La app me sirve para tener el borrador, ver en qué etapa va cada reporte (por generar / por imprimir / por firmar / por oficializar / oficializado) y, cuando está firmado, me indica **exactamente qué código y en qué columna del Excel** escribir. Cuando recargo la carta con ese código, la app lo detecta y me recuerda **cerrar** el pendiente.

## 6. Mantenimiento Correctivo

Cuando un equipo falla, se abre **mantenimiento correctivo**:

- Una **Orden de Trabajo (OT)** con su **Folio SIGEM** agrupa todo el **expediente** (la OT, sus reportes de servicio y los envíos a servicio técnico).
- El expediente avanza por etapas: **Apertura → (cotización) → Informe técnico → Orden de Compra → Ejecución → Cierre**, con **Trato Directo** o **Compra Ágil**.
- Lo crítico es la **operatividad**: si el equipo queda **No Operativo** o **en Servicio Técnico**, cuento los **días detenido**; si siguió operativo, es el ciclo administrativo.
- Los **envíos a servicio técnico** tienen su **N° de envío** (y el retorno se conecta con su envío). Debo poder **buscar por ese número** ("¿tienes el envío 166?").

## 7. Pendientes y gestión

Los **pendientes** son las gestiones que quedan asociadas a un equipo (reprogramaciones, protocolos, monitoreos, documentos por imprimir, etc.). Para cada uno llevo: fecha de compromiso, responsables, tareas y una **bitácora de gestión**. La **fecha de compromiso de un pendiente que nace de un evento** (una mantención o una reprogramación) es **la fecha de ese evento**.

Necesito **encontrarlos rápido** y **trabajarlos por lote** (p. ej. "todos los reportes por firmar de tal servicio"), y poder **ver/exportar las columnas del equipo** que me sirvan en cada caso.

## 8. Operatividad (el tablero que responde "¿en qué está cada equipo?")

De todo lo anterior, la app deriva **una sola verdad por equipo**: su **estado** (Operativo / No Operativo / Servicio Técnico), su **criticidad** y la **siguiente acción** recomendada para asegurar la operatividad. Así, en una mirada, sé qué equipos necesitan atención y qué hacer con cada uno, sin tener que reconstruirlo a mano.

## 9. Principios que deben guiar la aplicación final

1. **La app no reemplaza a la carta; la complementa.** La carta manda en lo oficial (resultados); la app manda en el detalle y el seguimiento.
2. **Nada se da por oficial hasta que está en la carta.** Borrador hasta que se recarga con su resultado.
3. **El foco es la operatividad**, no el papeleo: todo debe ayudar a saber el estado y la siguiente acción.
4. **Cada documento tiene su ciclo** (recibir → detallar → completar → carpeta + carta → oficial), y la app debe acompañar ese ciclo, no entorpecerlo.
5. **Lo que hago a diario debe ser rápido**: buscar, filtrar por servicio/mes, trabajar por lote, ver/exportar solo lo que necesito.

## 10. Registro acumulativo de ajustes (qué pedí y por qué)

*Cada entrada deja constancia del **ajuste** y, sobre todo, del **porqué** (mi necesidad real).*

| **Fecha** | **Ajuste** | **Por qué lo necesito** |
| --- | --- | --- |
| 2026-06-15 | Columnas de equipo (ID, N° Carpeta, Unidad, Ubicación, Procedencia, Marca, Modelo, Serie…) y **Carta Gantt** filtrable tipo Excel en el Plan | Ver el plan como lo veo en la carta y ubicar equipos por sus datos reales |
| 2026-06-15 | Búsqueda de Pendientes por tarea, inventario, serie y cualquier campo | Encontrar un pendiente por cualquier dato, no solo por el equipo |
| 2026-06-16 | **Tipo de mantenimiento (Interno/Externo)** y **protocolo de tareas** (Sí/No/Imprimir/Gestión + comentarios) | El resultado va a la carta, pero el detalle del protocolo lo llevo en la app |
| 2026-06-16 | El **tipo de pendiente** arma su checklist; no perder texto sin agregar | Que al elegir "Protocolo…" aparezca la lista sola, también en pendientes existentes |
| 2026-06-16 | **Motor de estado integral**: estado + criticidad + **siguiente acción** por equipo, conectando todo | Saber de una el estado de cada equipo y qué hacer, sin rearmarlo a mano |
| 2026-06-16 | **Subtareas** cuando un protocolo queda en **Gestión** | Desglosar qué hay que gestionar (p. ej. generar documento, firmas) |
| 2026-06-16 | **Reprogramación con ciclo de reporte** (generar → imprimir → 2 firmas) + columna y chips por etapa | Tramito un documento con firmas, no solo escribo un código; necesito ver en qué etapa va cada uno |
| 2026-06-16 | El reporte conserva su **causal y su fecha** (la de la MP) | El documento lleva esa causal y esa fecha; debo verlas sin buscarlas |
| 2026-06-16 | **Envíos buscables** por N° (global y en Correctivos) + columna N° Envío | Me preguntan "¿tienes el envío 166?" y debo encontrarlo al instante |
| 2026-06-16 | **Selector de columnas en Pendientes** (todas las del equipo, ver y exportar) y **orden** ID→…→Clasificación | Armar y exportar la vista de pendientes con las columnas que me sirvan |
| 2026-06-16 | **Compromiso = fecha del evento** (mantención/reprogramación) | Que el pendiente refleje la fecha real del evento que lo originó |
| 2026-06-16 | **«← Volver»** regresa a la vista de origen | Si entré desde Pendientes, volver a Pendientes, no a Equipos |
| 2026-06-16 | **Oficializar y cerrar** la reprogramación: la app indica **qué código y en qué columna del Excel** y, al recargar la carta, sugiere cerrar | Cerrar el ciclo: firmado → escribo el código en la carta → recargo (oficial) → cierro |
| 2026-06-16 | El respaldo no guarda columnas derivadas (se recalculan) | Respaldos más livianos para traspasar/guardar |

## 11. Pendiente de aclarar / próximos pasos

*Espacio para dudas abiertas y lo que falta entender antes de la versión final.*

*(sin pendientes abiertos por ahora — agregar a medida que surjan)*

### Cómo se mantiene este documento

- Es la **fuente de la verdad del proceso**. Ante cada ajuste, primero se actualiza aquí (qué y por qué) y luego se construye en la app.
- Cuando confirmemos que **todo está entendido y no hay más ajustes**, esta es la base para **congelar la aplicación oficial final**.
