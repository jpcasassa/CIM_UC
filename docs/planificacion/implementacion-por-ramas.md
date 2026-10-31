# Plan de Implementación por Ramas · CIM UC

> Complemento de `plan-implementacion.md`: ordena el trabajo en ramas Git, todas desde `main`,
> cada una con merge a `main` al estar lista. Los pasos internos siguen el orden de dependencia
> técnica, no el número de issue. Cobertura: 24 issues abiertos ↔ módulos N (4.1), F (4.2),
> V (4.3), A (4.4), P (4.5) y R (4.6) del plan.

## Grafo de merges

```text
main ──┬── feat/datos-room ────────────┐
       ├── feat/navegacion-interface ──┤
       │                               ▼
       ├── feat/validacion-mvvm        (merge en cualquier orden)
       │           ▲                     
       └── feat/formulario-contacto ───┤
                                       ▼
                          feat/animaciones
                          feat/recursos-nativos
```

Orden lógico de ejecución y merge:

1. `chore/decisions-previas` (1 commit a main)
2. `feat/datos-room` y `feat/navegacion-interface` (paralelas)
3. `feat/validacion-mvvm`
4. `feat/formulario-contacto`
5. `feat/animaciones` y `feat/recursos-nativos` (paralelas al final)

---

## Rama 0 · `chore/decisions-previas` — 1 commit a main ✅

Un único commit que deja los acuerdos previos registrados:

1. **Decisión de paquete:** mantener `cl.duoc.jpcu.cimuc` (código actual) y corregir la
   referencia a `cl.duoc.jpcu.cimuc` dentro de `docs/planificacion/plan-implementacion.md`.
2. **Decisión de precarga (tomada, alineada al ramo):** catálogo ficticio por **objetos Kotlin**
   (`CimSeedData`) insertados la primera vez vía `RoomDatabase.Callback` (`onCreate`) en
   `Dispatchers.IO`, con `@Insert(onConflict = IGNORE)` en los DAOs para precarga idempotente.
   Descartado JSON en `assets/`: el material del ramo nunca usa assets y JSON **agrega**
   ~100–150 líneas netas (parseo + manejo de error) sin cubrir ningún requisito.
   Coherente con #21, RNF-07 y la verificación en Database Inspector.
3. Incluir este documento (`implementacion-por-ramas.md`) en el mismo commit.

> Todo se cierra en **un solo commit a main**, sin ramas intermedias.

---

## Rama 1 · `feat/datos-room` (P1–P6 · #18–#23) — sin dependencias ✅

| # | Paso | Detalle |
| :-- | :--- | :--- |
| 1 | **#18 Entidades Room** | `ProyectoEntity`, `AreaTematicaEntity`, `IntegranteEntity`, `OrganizacionEntity`, `CapacidadEntity`, `PublicacionEntity`, `ActividadEntity`, `SolicitudContactoEntity` + tablas intermedias, según `docs/05-modelo-datos.md`; PK/FK + `ForeignKey(onDelete = CASCADE)` + índices. |
| 2 | **#19 DAOs** | Consultas `Flow<List<T>>`; búsqueda con `LIKE` sin distinción de mayúsculas/tildes; filtros combinables por tipo/área/año; relaciones con `@Relation`/JOIN (ProyectoDao, IntegranteDao, ActividadDao, SolicitudContactoDao y restantes). |
| 3 | **#20 AppDatabase + Repository** | `@Database` singleton + `CimRepository` y `ContactoRepository` que abstraen los DAOs hacia los ViewModels. |
| 4 | **#21 Precarga** | Catálogo ficticio como objetos Kotlin (`CimSeedData`) insertados vía `RoomDatabase.Callback` (`onCreate`, `Dispatchers.IO`, decisión de rama 0). Cotas mínimas: ≥10 proyectos, ≥10 integrantes, ≥6 capacidades, ≥8 publicaciones, ≥6 actividades. `@Insert(onConflict = IGNORE)` en los DAOs para idempotencia. |
| 5 | **#22 Persistir SolicitudContacto** | Insert al enviar + recuperar resumen por ID para P-07. |
| 6 | **#23 Búsqueda y filtros** | `ExplorarViewModel` con búsqueda insensible, filtros combinables, contador de coincidencias y `EmptyState`. |

Cierre: verificar con Database Inspector, commits atómicos por issue, PR → main.

---

## Rama 2 · `feat/navegacion-interface` (N1–N5 · #1–#5) — sin dependencias, paralela a rama 1 ✅

| # | Paso | Detalle |
| :-- | :--- | :--- |
| 1 | **#1 Rutas y NavHost** | `Screen` sealed class + `NavHost` conectando P-01 a P-07 en `AppNavigation.kt`. |
| 2 | **#2 NavigationBar inferior** | Visible solo en P-01, P-02 y P-05 vía `currentBackStackEntryAsState()`. |
| 3 | **#3 TopAppBar con retroceso** | `TopAppBarCommon` con `popBackStack()` en P-03, P-04 y P-06; preservar búsqueda/filtros de P-02 (el ViewModel sobrevive al back stack). |
| 4 | **#4 Las 7 pantallas** | Composables P-01..P-07 según `docs/06-mockups.md`: `Scaffold`, `LazyColumn`, `Card`. |
| 5 | **#5 Tema Material 3** | Paleta institucional en `Color.kt`/`Theme.kt`/`Type.kt`; espaciados 8dp, targets ≥48dp, texto ≥14sp. |

Cierre: RNF-02 (contraste/accesibilidad), RNF-03 (`contentDescription`), RNF-08 (consistencia visual), commits, PR → main.

---

## Rama 3 · `feat/validacion-mvvm` (V1–V4 · #12–#14) — conveniente tras mergear rama 2 ✅

| # | Paso | Detalle |
| :-- | :--- | :--- |
| 1 | **#12 ContactoValidator** | Funciones puras que retornan `ValidationResult`; unit tests en `app/src/test` sin dependencias de UI Android. |
| 2 | **#13 ContactoViewModel** | `StateFlow<ContactoUiState>` con estados `Formulario`, `Enviando`, `Error`, `Exito`, consumido vía `collectAsState()`. |
| 3 | **#14 Desacoplar UI** | `ContactoScreen` solo observa UiState y delega eventos por lambdas (`onNombreChange`, `onEnviarClick`…); cero lógica en Composables. |

Cierre: checklist "Lógica y Validación" del plan, commits, PR → main.

---

## Rama 4 · `feat/formulario-contacto` (F1–F5 · #6–#10) — requiere ramas 1 y 3 mergeadas

| # | Paso | Detalle |
| :-- | :--- | :--- |
| 1 | **#6 Layout P-06** | `OutlinedTextField` para nombre/correo/organización/motivo/mensaje + campo "Contenido referido" (`readOnly = true`) + botón de envío, fiel al mockup. |
| 2 | **#7 Validación visual** | `isError` + `supportingText` + íconos por campo. |
| 3 | **#8 Validación de correo** | Regla de formato (`@` y dominio) en `ContactoValidator` + test. |
| 4 | **#9 Retención de datos** | Estado controlado en `StateFlow`; los campos no se limpian al fallar. |
| 5 | **#10 Navegar a P-07** | Solo con validación OK: insert vía `ContactoRepository` + paso de ID/resumen a `ConfirmacionScreen`. |

Cierre: RNF-01 (recorrido ≤5 toques), RNF-04 (respuestas <1s), commits, PR → main.
Nota: al terminar F4 el validador ya trae la validación de correo (rama 3) — integrar y no duplicar.

---

## Rama 5 · `feat/animaciones` (A1–A3 · #15–#17) — requiere ramas 2, 3 y 4 mergeadas

| # | Paso | Detalle |
| :-- | :--- | :--- |
| 1 | **#15 Transiciones NavHost** | `slideInHorizontally`+`fadeIn` y sus inversos con `popEnterTransition`/`popExitTransition`. |
| 2 | **#16 AnimatedVisibility en P-06** | Aparición de errores y feedback de procesamiento al enviar, usando el UiState de la rama 3. |
| 3 | **#17 Animación en LazyColumn** | Items y cambios de filtro en ExplorarScreen, sobre los filtros reactivos de la rama 1. |

Cierre: RNF-05 (20 recorridos completos + rotaciones sin crash), commits, PR → main.

---

## Rama 6 · `feat/recursos-nativos` (R1–R2 · #24–#25) — última, sobre main

| # | Paso | Detalle |
| :-- | :--- | :--- |
| 1 | **#24 Compartir proyecto** | Botón en P-03: `Intent.ACTION_SEND` con título, área y descripción formateados. |
| 2 | **#25 Contacto por correo** | `Intent.ACTION_SENDTO` con `mailto:`, prellenado de asunto/mensaje en P-03/P-06/P-07. |

Cierre: auditoría de `AndroidManifest` (sin permisos peligrosos), commits, PR → main.

---

## Cierre global (tras el último merge)

- [ ] Checklist técnico completo del plan (sección 6): flujo navegable completo, barras, estado, Room en Database Inspector, capacidades nativas.
- [ ] RNF-06: verificar en emulador API 26+, 360×640 y 412×915dp, portrait.
- [ ] Recorrido final de usabilidad cronometrado (RNF-01) y TalkBack (RNF-03).

## Dependencias entre ramas

| Rama | Depende de |
| :--- | :--- |
| 1. datos-room | — (paralela a 2) |
| 2. navegacion-interface | — (paralela a 1) |
| 3. validacion-mvvm | 2 (recomendado) |
| 4. formulario-contacto | 1 y 3 |
| 5. animaciones | 2, 3 y 4 |
| 6. recursos-nativos | 2 y 4 |
