# Sistema de Gestión MP 2026 — Equipamiento Clínico HHHA

Aplicación de **una sola página** (single-file HTML) para la gestión de las
**mantenciones preventivas (MP) del equipamiento clínico** del Hospital Hernán
Henríquez Aravena. Lleva equipos, mantención preventiva, reprogramaciones,
pendientes y mantenimiento correctivo (expedientes / OT). Corre **100% en el
navegador, sin conexión**.

## Cómo usar

Abre **`index.html`** en un navegador (doble clic). No requiere servidor ni
internet. La primera vez, importa tu **carta (Excel `.xlsm`)** o un **respaldo
(`.json`)** desde la vista de carga; los datos quedan en `localStorage`.

- **Importar / cargar:** planilla `ProgramaciónMP_2026.xlsm` (hojas `PMP_2026` y
  `Registro_MP-2026`) o un respaldo JSON.
- **Persistencia:** `localStorage` (claves `gmp2026.datos`, `gmp2026.usuario`,
  `gmp2026.pref`). Todo es local a ese computador.
- **Respaldo / exportación:** la app exporta a Excel y genera respaldos JSON.

## Vistas

- **Equipos** — inventario con filtros estilo Excel.
- **Operatividad** — una sola verdad por equipo: estado, criticidad y siguiente acción.
- **Plan** — programación anual y **Carta Gantt** filtrable.
- **Pendientes** — gestiones por equipo (reprogramaciones, protocolos, documentos…).
- **Correctivo** — expedientes/OT con su Folio SIGEM y envíos a servicio técnico.

## Documentación del proyecto

- **`CLAUDE.md`** — guía técnica y reglas/invariantes para trabajar el código.
- **`ENTENDIMIENTO.md`** — documento vivo del proceso: qué se pide, por qué, y el
  registro acumulativo de ajustes.
- **`revision-mp-2026.html`** — tablero de revisión (informe de solo lectura) de
  un respaldo, con verificaciones de integridad y listas accionables.

## Arquitectura (resumen)

- **Vanilla JS, sin framework, un solo archivo HTML.** Las primeras líneas son la
  librería SheetJS (vendida) para importar/exportar Excel; el código de la app
  empieza más abajo.
- **Estado global** `state` (`equipos`, `registros`, `manuales`, `pendientes`,
  `correctivos`, `empresas`, `meta`) + `prefs` y objetos de filtro por vista.
- **Render con cachés** que se invalidan a mano; toda mutación de `state` debe
  `guardar()` e invalidar las cachés afectadas.
- **Motor de estado** (`calcularDerivadosEquipos`, `decidirSiguienteAccion`,
  `estadoActualEquipo`, `tableroOperatividad`, `siguientePasoDe`) que alimenta
  Equipos, la ficha y Operatividad. Se recalcula en `renderTodo()` al cargar.

> Build actual: **2026-06-16.37**. El versionado sube en cada cambio (`AAAA-MM-DD.NN`).
