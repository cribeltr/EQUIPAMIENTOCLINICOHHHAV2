# Sistema de Gestión MP 2026 — Guía para Claude Code

## Qué es
App de una sola página (single-file HTML) para la gestión de **mantenciones
preventivas de equipamiento clínico** del Hospital HHHA. La usa Cristián
(administrador) junto a un equipo de ejecutores. Lleva: equipos, mantención
preventiva (MP), pendientes y mantenimiento correctivo (expedientes / OT).
Corre **100% en el navegador, sin conexión**.

## Fuente de verdad de las reglas
El documento de flujo (**Flujo_Sistema_Gestion_MP_2026**) define las 15 etapas y
TODAS las reglas de negocio. **Antes de tocar cualquier lógica, léelo.**
Invariantes que NUNCA deben romperse (son las que más fácil se rompen al editar):

- **Serie y N° Inventario son TEXTO**, conservando ceros a la izquierda
  ("00039" ≠ "39"), en carga, vista y toda exportación.
- **Ningún registro se filtra ni descarta**, ni siquiera con valor 0.
- **Borrador→Oficial**: al recargar la planilla, un registro Borrador que
  aparezca en ella pasa a Oficial; la planilla prevalece y no se duplica el
  conteo del mes.
- **Reprogramación C1–C8**: C2/C3/C4 no fijan fecha nueva (se registran al
  reintegrarse el equipo); C1/C5/C6/C7/C8 se reprograman dentro de 30 días, el
  mes origen conserva X + la causal en Resultado, el mes destino lleva R.
- **El último estado de cada equipo manda** (motor de estado integral, Paso 12).
- La key única del equipo es la **Serie o el N° Inventario**, no el orden de fila.

## Navegación y UX (principios)
- **La navegación conserva el origen.** Cualquier vista de detalle (p. ej. la ficha
  de un equipo) alcanzable desde más de una vista debe volver a la vista desde la
  que se entró, no a una vista fija. «← Volver» = vista de origen.
- Al agregar una acción o vista nueva, revisa **desde cuántos lugares se llega** y
  que se comporte consistente en todos.

## Documento vivo del proceso: ENTENDIMIENTO.md
Junto a las reglas formales existe **`ENTENDIMIENTO.md`**: el registro **en primera
persona** de QUÉ pido, POR QUÉ (mi necesidad real) y cómo la app me apoya, más el
**registro acumulativo de ajustes** y las **dudas abiertas**. Léelo también al
inicio: te da el *porqué* y la historia que las reglas formales no cuentan.

**Cómo se reparten los dos documentos (para que no haya ambigüedad):**
- Sobre **cómo funciona una regla** (etapas, causales, oficialización, invariantes)
  manda **Flujo_Sistema_Gestion_MP_2026** + las invariantes de arriba.
- Sobre **qué quiero, por qué, y qué se ha ido cambiando** manda **ENTENDIMIENTO.md**.
- Si encuentras una contradicción entre ambos, **no la resuelvas en silencio**:
  avísame.

**Mantén ENTENDIMIENTO.md vivo — en CADA ajuste que haga, después de aplicarlo:**
1. Agrega una fila a la tabla de la **sección 10** (Registro de ajustes):
   *Fecha · Ajuste · Por qué lo necesito*.
2. Actualiza las **secciones del proceso** (1–9) que el cambio afecte.
3. Si el ajuste resolvió o abrió una duda, refléjalo en la **sección 11**.
4. Actualiza el encabezado del documento (**"Última actualización"** y **build**)
   para que coincida con el nuevo build de la app.

## Arquitectura (cómo está hecho)
- **Vanilla JS, sin framework. Un solo archivo HTML.**
- **Las líneas ~1–29 son la librería SheetJS minificada (vendida/vendored) para
  importar y exportar Excel. NO las leas ni las edites. El código de la app
  empieza alrededor de la línea 300.**
- **Estado global**: `let state = {…}` (~línea 1119):
  `equipos`, `registros` (planilla), `manuales` (MP creadas en la app),
  `pendientes`, `correctivos`, `empresas`, `meta`.
  Más `prefs` (memoria de uso) y objetos de filtro por vista
  (`filtros`, `filtrosPlan`, `filtrosGantt`, `filtrosPend`, `filtrosCorr`).
- **Persistencia**: `localStorage`, 3 claves —
  `gmp2026.datos` (equipos/registros/meta),
  `gmp2026.usuario` (manuales/pendientes/correctivos/empresas),
  `gmp2026.pref`.
- **Render-on-demand con cachés**: `cacheFiltradas`, `cachePlanBase`, `cacheGantt`…
  se invalidan a mano con `invalidar()`, `invalidarPlan()`, etc.
  → **Toda mutación de `state` debe `guardar()` E invalidar las cachés afectadas.**
  (Olvidar la invalidación = vista desactualizada: es la fuente de bug más típica.)
- **Motor de estado (Paso 12)**: `calcularDerivadosEquipos()`,
  `decidirSiguienteAccion()`, `estadoActualEquipo()`, `tableroOperatividad()`,
  `siguientePasoDe()`. De aquí se alimentan Equipos, la ficha y Operatividad:
  manténlos consistentes entre sí.
- **Vistas**: Equipos (`renderTabla`), Operatividad (`renderOperatividad`),
  Plan (`renderPlan`), Pendientes, Correctivo. Todas con filtros estilo Excel.

## Convenciones
- Español en UI, mensajes y nombres de función.
- Fechas internas en ISO (`hoyISO`/`sumarDias`/`fmtFecha`); se muestran dd-mm-aaaa.
- **Versionado**: el build tiene formato `AAAA-MM-DD.NN` (hoy `2026-06-16.37`).
  **Súbelo en cada cambio.**
- Cambios pequeños y revisables; nada de reescrituras masivas del archivo.

## Cómo quiero que trabajes (importante)
No quiero un ejecutor de instrucciones. Quiero que actúes como un ingeniero que
ya conoce este sistema:

- **Plan antes de código** (en cambios no triviales): dime en 2–3 líneas qué
  entendiste y cómo lo vas a hacer, y espera mi OK antes de escribir.
- **Avísame si rompo una regla**: si lo que pido contradice una invariante de
  arriba, dímelo ANTES de hacerlo.
- **Tienes luz verde para mejorar, no solo proponer**: si ves algo que claramente
  me sirve en el día a día (riesgo de datos, bug latente, simplificación, UX),
  hazlo. Pero: **no elimines ni rompas algo que ya funciona sin avisarme**,
  **explícame siempre qué cambiaste y por qué me sirve**, y si **dudas** de que me
  sirva, **pregúntame antes** en vez de asumir.
- **Documenta el cambio**: después de cada ajuste, actualiza `ENTENDIMIENTO.md`
  como se indica más arriba.
- **Piensa en los casos límite**: equipo sin programación, reprogramación a fin
  de año, recarga de planilla con borradores abiertos, `localStorage` lleno,
  expediente con avances fuera de orden cronológico.

**Antes de dar por terminado un cambio** (recorre el flujo, no solo la función nueva):
- ¿Cómo llegó el usuario hasta aquí y a dónde vuelve? ¿El «volver» lo deja donde estaba?
- ¿Esta vista/acción es alcanzable desde más de un lugar? Si sí, ¿se comporta igual en todos?
- ¿Qué otra parte usa los mismos datos/estado y debe quedar en sincronía?
- ¿Rompí o dejé inconsistente algo que ya funcionaba?
