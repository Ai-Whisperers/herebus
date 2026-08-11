# Análisis: metadata de Cursor + Git — Saskia Weiss Vander

**Fecha:** 2026-08-11  
**Autor del análisis:** sesión Cursor (workspace `02-Work/saskia`)  
**Sujeto:** Saskia Weiss Vander / HEREBUS (negocio de comida / panadería-pastelería)  
**Propósito:** inventario verificable de lo que existe hoy (Cursor + GitHub) para preparar el producto a venderle y la sesión del viernes (repo + Excels + Hermes).

---

## 1. Resumen ejecutivo

| Hallazgo | Implicancia |
|---|---|
| El workspace local `02-Work/saskia` **no tiene clone git** de sus repos; solo metadata de Cursor/SpecStory | Hay que clonar `saskia-personal-context` antes de la sesión del viernes |
| El sistema operativo de HEREBUS (Excels de administración) vive en **`Ai-Whisperers/saskia-personal-context`** → `04_foodbiz-management-system/` | Ese es el “repositorio” que ella quiere entender |
| Hay **8 workbooks `.xlsx`** versionados (4 HEREBUS operativos + blueprint + plantilla + 2 originals) | El producto “fijar Excels vs Hermes” debe nombrar archivos concretos |
| Su GitHub personal (`SaskiaWeiss1234`) es **bootcamp web-dev**, activo hasta hoy (2026-08-11) | Ella ya hace commits/PRs; puede participar en la web, pero el negocio aún no tiene repo de página |
| Existe un Flask “Saskia Bakery” archivado (`IvanWeissVanDerPol/Saskia`, Jul 2025) | Prototipo viejo (San Lorenzo); no es el sistema Excel actual |
| `SaskiaPersonal` (ERP financiero citado en roadmap) **ya no resuelve (404)** | Posible merge/rename/delete; finanzas personales pueden estar solo en el context repo o perdidas |
| Hermes = agente AI de la org, **no** un repo de Saskia | El riesgo que ella nombra (“que Hermes no esté cambiando nomas”) es gobernanza de commits/agentes sobre el folder foodbiz |

---

## 2. Metadata de Cursor (local)

### 2.1 Workspace paths

| Path | Qué es |
|---|---|
| `c:\Users\kyrian\Documents\02-Work\saskia\` | Carpeta de trabajo abierta en Cursor |
| `c:\Users\kyrian\Documents\02-Work\saskia\.cursor\` | Única contenido real bajo saskia (no hay código de producto) |
| `C:\Users\kyrian\.cursor\projects\c-Users-kyrian-Documents-02-Work-saskia-cursor\` | Proyecto Cursor del IDE (transcripts, tools, MCP cache, canvases) |

**No hay** `.git` en `02-Work\saskia`. El workspace es un contenedor de sesión, no un repo.

### 2.2 SpecStory

| Archivo | Contenido relevante |
|---|---|
| `.cursor\.specstory\.project.json` | `workspace_id`: `4129-cff8-cd4d-a8da`; `workspace_id_at`: `2026-08-11T17:27:28Z`; `project_name`: `.cursor` |
| `.cursor\.specstory\statistics.json` | **1 sesión** (`ef64f5b8-…`): 1 user msg, 4 agent msgs; start `2026-08-11T14:26:23-03:00`; provider `cursoride`; markdown ~4801 bytes |
| `.cursor\.specstory\cli\config.toml` | Defaults SpecStory (local/cloud sync, redaction on); sin overrides activos |
| `.cursor\.specstory\history\2026-08-11_17-26-23Z-repository-review-and-planning.md` | Historial de esta misma conversación (WhatsApp paste + búsqueda de repos) |
| `.cursor\.cursorindexingignore` | Excluye `.specstory/**` del indexado |

**Interpretación:** este workspace de Cursor es **nuevo** (11 ago 2026). No hay historial largo de chats previos sobre Saskia en esta carpeta. El “contexto” real del negocio está en GitHub privado, no en SpecStory local.

### 2.3 Plan local (ruido / no relacionado)

| Archivo | Nota |
|---|---|
| `.cursor\plans\merge-repositories-into-global-courses-structure-c5985c78.plan.md` | Plan de merge de cursos QA / Courses-Content. **No es de HEREBUS ni de Saskia.** Parece residual de otro workspace/proyecto pegado aquí. |

### 2.4 Proyecto Cursor IDE (`…saskia-cursor`)

Contiene:

- `agent-transcripts/` — transcript de esta sesión
- `agent-tools/` — outputs temporales de tools (ej. listado Ai-Whisperers)
- `mcps/` — cache de MCP (`cursor-ide-browser`, `plugin-supabase-supabase` needs auth)
- `canvases/` — SDK de canvas + `node_modules` (infra Cursor, no producto Saskia)

**Sin** reglas custom, skills, hooks ni `.canvas.tsx` de análisis propios de Saskia todavía.

### 2.5 Contexto de negocio capturado en Cursor (WhatsApp 05/08/2026)

De la conversación pegada en esta sesión, Saskia pidió / ofreció:

1. Ver lo que hizo de **HEREBUS** (sesión presencial).
2. Entender **dónde están los Excels de administración** en el repo.
3. **Fijar** esos Excels para que Hermes no los cambie libremente, pero sí puedan actualizarse vía Hermes más adelante (producción/venta).
4. Armar **página web** + **WhatsApp Business**.
5. Plan escrito el viernes de mañana; pricing de productos al día siguiente de compras.
6. Cuestionario de K.W. para definir qué sí / qué no.

Eso define el brief comercial; el resto del análisis abajo es evidencia técnica.

---

## 3. Inventario Git / GitHub

### 3.1 Identidades

| Cuenta | Rol |
|---|---|
| [SaskiaWeiss1234](https://github.com/SaskiaWeiss1234) | GitHub personal de Saskia Weiß — 10 repos públicos; creada 2026-05-29 |
| [Ai-Whisperers](https://github.com/Ai-Whisperers) | Org — repo privado de contexto familiar/negocio |
| [IvanWeissVanDerPol](https://github.com/IvanWeissVanDerPol) | Histórico: `Saskia` archivado; roadmap citaba `SaskiaPersonal` (404) |
| Colaboradores en `saskia-personal-context` | `IvanWeissVanDerPol`, `kyrianWVDP`, `aiwhispererwvdp`, `JohnvanderPol2` |

### 3.2 Repo canónico del negocio: `Ai-Whisperers/saskia-personal-context`

| Campo | Valor |
|---|---|
| URL | https://github.com/Ai-Whisperers/saskia-personal-context |
| Visibilidad | **PRIVATE** |
| Creado | 2026-07-12 |
| Último push | 2026-08-10 |
| Default branch | `main` (+ rama `compliance/whatsapp-banlist-scrub`) |
| Lenguaje dominante | Python (~323 KB), JS/CSS/HTML (calendar planner) |
| Tamaño | ~1253 KB |
| Commits (páginas API) | ~42 páginas × 1 = **~42 commits** (orden de magnitud) |
| Issue abierta | #1 — `compliance: scrub WhatsApp trademark from 26 files` (2026-08-10) |
| Descripción | Context repo OPSEC (estilo pierce-charm / sarah-lubricants): banca, identidad, sesiones + foodbiz |

#### Estructura (120 blobs en `main`)

| Carpeta / archivo | Archivos | Rol |
|---|---:|---|
| `04_foodbiz-management-system/` | 55 | **Sistema HEREBUS** (Excels + Python + docs) |
| `02_sessions/` | 20 | Notas de sesión WhatsApp/WebUI |
| `01_banking-accounts/` | 15 | Extractos Familiar PY + ABN NL |
| `06_calendar-planner/` | 13 | MVP FastAPI + Google Calendar (HEREBUS) |
| `05_research/` | 7 | Roadmap, RQ, ecosystem design, best practices |
| `00_identity/` | 3 | Datos personales / household |
| `03_data-quality/` | 2 | Preguntas abiertas OCR/datos |
| Root (`README`, `AGENTS`, `INDEX`, `CHANGELOG`, `.gitignore`) | 5 | Contratos del repo |

#### Workbooks Excel (fuente de verdad operativa documentada)

| Path | Rol |
|---|---|
| `04_foodbiz-management-system/data/HEREBUS_FoodBiz.xlsx` | Libro principal (~89 KB): inventory ES, ~63 ingredientes, ~20 Recipe_* tabs, production/waste/dashboard |
| `…/HEREBUS_Suppliers.xlsx` | Proveedores + price history + shopping list |
| `…/HEREBUS_Analisis.xlsx` | KPI, pricing por producto, risk, wishlist, benchmarks |
| `…/HEREBUS_Comparacion_Proveedores.xlsx` | 63×4 slots comparación (2026-08-05) |
| `…/FoodBiz_Management.xlsx` | Blueprint genérico USD (referencia) |
| `…/RECETARIO_EN_BLANCO.xlsx` | Plantilla vacía para nuevas recetas |
| `…/originals/herbus_recipes_legacy_2026-07-19.xlsx` | Legacy 7 recetas |
| `…/originals/smallfoodbiz_template_empty.xlsx` | Template origen |

#### Gobernanza ya escrita (`04_foodbiz-management-system/AGENTS.md`)

Reglas relevantes para el producto “Hermes no cambia nomas”:

1. **Python es source of truth** — no editar xlsx a mano; regenerar con scripts.
2. Sheet protection en celdas calculadas.
3. Moneda Gs. enteros, sin decimales.
4. Repo PRIVATE; sin deploy público de datos.
5. Sin datos reales de clientes en el workbook (política).
6. **No bots WhatsApp/Telegram en este repo** (decisión 2026-07-24).
7. Precios/yields empiezan vacíos para que Saskia los llene al comprar/cocinar.

Commits recientes (autores): principalmente **Ivan Weiss Van Der Pol** — merges feat comparación proveedores, calendar planner MVP, sub-recipes/suppliers/análisis.

### 3.3 Histórico: `IvanWeissVanDerPol/Saskia` (archivado)

| Campo | Valor |
|---|---|
| URL | https://github.com/IvanWeissVanDerPol/Saskia |
| Estado | **public, archived** |
| Creado / push | 2025-07-04 |
| Stack | Flask (`app.py`, `models.py`, `routes.py`, templates), HTML |
| README | “Sistema de Gestión Saskia Bakery” — San Lorenzo, PY; inventario, recetas, pedidos, dashboard |

**Interpretación:** primer intento de app web de gestión. Superseded por el enfoque Excel+Python en el context repo. Roadmap de mejoras del README (facturación, WhatsApp, app móvil, delivery, RRSS) **sigue alineado** con lo que ella pide ahora — pero la implementación viva no es este repo.

### 3.4 Fantasma: `IvanWeissVanDerPol/SaskiaPersonal`

Citado en `05_research/HEREBUS-setup-roadmap.md` (2026-07-23) como ERP personal con `Finance.xlsx` (EUR+PYG). **API actual: 404.** Tratar como asset perdido o renombrado hasta confirmar con Ivan.

### 3.5 GitHub personal de Saskia (`SaskiaWeiss1234`) — bootcamp

| Repo | Lang | Notas | Actividad |
|---|---|---|---|
| `web-challenges` | JS | Bootcamp challenges; contribs también de coaches (`djfarly`, etc.) | Push **2026-08-11** (“completed the task”) |
| `color-code-app` | JS | Deploy Vercel; PRs mergeadas por ella | Jul 2026 |
| `Lord-of-the-Rings-App` | JS | Initial commit | Jul 2026 |
| `git-conflicts` | HTML | Ejercicios + merges confusos | Jul 2026 |
| `rick-and-morty` | — | **Repo vacío** | Jul 2026 |
| `quiz-app` | HTML | GitHub Pages live | Jun–Jul 2026 |
| `session-notebook` | — | Notas markdown + PRs | Jun 2026 |
| `html-and-the-web_personal-website-` | — | Personal website exercise | Jun 2026 |
| `my-first-repository` | — | Primer repo | Jun 2026 |
| `SaskiaWeiss1234` | — | Profile README | Jun 2026 |

**Señal de habilidad:** ya usa branches, PRs, Vercel, Pages. Útil para co-construir la página HEREBUS, no para admin Excel (eso es otro stack/repo).

### 3.6 Relacionados pero no “producto HEREBUS”

| Repo | Nota |
|---|---|
| `Ai-Whisperers/meal-prerp-website` | Site meal-prep TypeScript; no etiquetado como HEREBUS/Saskia |
| Hermes stack (`hermes-agent`, `ai-whisperers-hermes-agent`, org `infrastructure`) | Infra del agente que ella quiere acotar sobre los Excels |

---

## 4. Mapa “qué le mostramos el viernes”

Orden sugerido alineado a su mensaje:

1. Abrir **`saskia-personal-context`** (clone local o GitHub web).
2. Ir a **`04_foodbiz-management-system/README.md`** + `data/`.
3. Abrir en Excel/Sheets los 4 libros HEREBUS (FoodBiz, Suppliers, Analisis, Comparacion).
4. Mostrar **`AGENTS.md`** = las reglas anti-cambio libre (Python regenera; Hermes no hand-edit).
5. Mostrar **`05_research/herbus-ecosystem-design.md`** = Drive vs Sheets vs repo.
6. Separar conversación de **página web** (aún sin repo HEREBUS) para la semana siguiente.
7. Entregar el **cuestionario Word** (español) para que complete el plan del viernes.

---

## 5. Gaps vs producto a vender

| Pedido (WhatsApp) | Estado técnico hoy | Gap de producto |
|---|---|---|
| Ver Excels de administración | Existen en repo privado | Acceso + tour + ownership de edición |
| Fijar vs Hermes | AGENTS.md ya dice “no hand-edit xlsx” | Política operativa + permisos + posiblemente branch protection / CODEOWNERS / allowlist de paths para el agente |
| Actualizar vía Hermes en producción/venta | No hay pipeline documentado de “Hermes escribe JSON → rebuild xlsx” | Diseñar canal seguro de update (PR, review, dry-run) |
| Página web | Solo ejercicios bootcamp + Flask archivado | Scope, stack, dominio, contenido, hosting |
| WhatsApp Business | Explícitamente **fuera** del context repo | Producto separado: catálogo/pedidos/out-of-stock (hay diseños en `processes/` / sesiones Jul-24) |
| Pricing en uso | Inventory/recipe yields pensados para que ella llene | Onboarding de datos reales post-compras |
| Contador / régimen / compliance BPM | Preguntas Jul-23 aún en research | Bloquean tabs fiscales/legales |

---

## 6. Riesgos / OPSEC

- El context repo mezcla **identidad + banca + negocio**. Cualquier “página web” o bot **no debe** vivir en ese mismo repo (ya hay regla 6).
- Issue #1 de scrub de trademark WhatsApp: cuidado al documentar/comercializar integraciones.
- No clonar el repo privado a carpetas sync’d con Drive público / OneDrive compartido sin revisar.
- `SaskiaPersonal` 404: confirmar backup de `Finance.xlsx` antes de asumir que las finanzas personales están cubiertas.

---

## 7. Artefactos generados junto a este análisis

| Archivo | Uso |
|---|---|
| `docs/2026-08-11-saskia-cursor-git-analysis.md` | Este informe (interno) |
| `docs/Cuestionario-HEREBUS-Definicion-de-Producto.docx` | Cuestionario en español para Saskia |

---

## 8. Fuentes verificadas

- GitHub API / `gh` (2026-08-11): repos listados arriba  
- Contenidos remotos: `INDEX.md`, `AGENTS.md` foodbiz, `HEREBUS-questions-for-saskia.md`, `HEREBUS-setup-roadmap.md`, tree `main`  
- Local: SpecStory project/statistics/history, plan residual courses, Cursor project folder  
- WhatsApp transcript 05/08/2026 (pegado en sesión Cursor)

---

*Fin del análisis.*
