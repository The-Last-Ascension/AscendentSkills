# Registro Evolutivo: Decisiones, Cambios y Lecciones Aprendidas

Este archivo registra cronológicamente las decisiones de arquitectura, sistemas implementados y soluciones a bugs de **The Last Ascension (Ascendant)**.

---

## Historial de Hitos y Decisiones

### [2026-11-08] — Inicialización del Proyecto y Visión Base
- **Visión:** Creación de un servidor RPG privado para amigos llamado **The Last Ascension** (ciudad/nombre corto: **Ascendant**), con cero compras con dinero real (prohibido RMT).
- **Inspiración:** *Sword Art Online* (principal), *Solo Leveling*, *DanMachi*, *Mushoku Tensei*, *Grounded 2*, *Genshin Impact / Wuthering Waves*, *Trove*, *Elden Ring*.

### [2026-11-08] — Definición Profunda de Sistemas Nucleares (Fase 0)
- **Plugins Base de Assets:** Se empezará trabajando con las versiones gratuitas de **MythicMobs** y **ModelEngine 4** para integrar y probar los primeros assets de **SamusDev**, mientras que todos los sistemas RPG nucleares los programaremos nosotros a medida.
- **Combate, Parry y Bloqueo (*Grounded / Grounded 2*):**
  - El Parry se ejecuta con **Clic Derecho**. Las armas tienen flags (`can_block`, `can_parry`) para decidir cuáles pueden bloquear/hacer parry.
  - Los ataques enemigos pueden ser **parreables** o **no parreables**. Si un jugador intenta hacer parry a un ataque no parreable (o mantiene guardia), no hace parry pero **bloquea** el golpe: mitiga parte del daño, reduce su barra de protección y **aumenta su propio Stun** (si abusa del bloqueo, queda stuneado).
  - Cuando un enemigo llena su barra de Stun, entra en **animación de Stun** y no puede atacar durante un tiempo.
  - El combate incluye ataques rápidos, cargados, especiales y definitivas, además de **mejora de habilidades** con materiales (mejorando daño, tamaño/AoE, efectos y animaciones).
- **Elementos Propios y Sinergias (*Genshin Impact / Wuthering Waves*):**
  - Elementos personalizados con nombres e identidades inventadas (evitando nombres genéricos como "Oscuridad" simple), resistencias y estados alterados propios.
  - **Reacciones Elementales** entre ataques de distintos jugadores y **Definitivas Conjuntas cooperativas** que generan una definitiva nueva con animación, daño y efectos propios.
- **Clases y Estadísticas (*Pokémon Starters* + *Trove*):**
  - Elección inicial entre clases base viendo todas sus evoluciones y árboles de habilidades.
  - Separación entre **Puntos de Estadística Globales** (daño, vel. ataque, vida, defensa — persisten al cambiar de clase) y **Puntos de Habilidad de Clase** (independientes para cada clase). Ambos reseteables con moneda/ítem de dungeon.
  - Cambio de clase **gratuito** desbloqueable temprano en la historia (1er/2º Boss) hablando con un NPC específico, guardando el progreso de cada clase por separado estilo *Trove*.
- **Equipamiento, Talismanes (*Elden Ring*), Pets y Monturas:**
  - Todas las clases pueden vestir cualquier armadura y reciben sus stats base (defensa/protección/daño base), pero las **pasivas, stats de clase y bonus de set completo** solo se activan si llevas la clase requerida.
  - Añadido sistema de **Talismanes** estilo *Elden Ring*.
  - **1 Pet activa** por jugador (pasiva, de combate o híbrida).
  - **Monturas** divididas en Terrestres, Voladoras y Acuáticas (con subgrupos), restricciones por zona/mazmorra y posibilidad de tener ataques/defensa/pasivas propias.
- **Mundo, Mazmorras, Recursos Renovables y Clanes:**
  - Ciudades con su propia mazmorra estilo *DanMachi/SAO* (5 salas y un Boss cada 5 pisos), más poblados, ciudades demonio y estructuras de exploración.
  - **Sincronización global de herreros/tiendas:** Desbloquear sets de armadura en una ciudad los desbloquea en los herreros de todas las ciudades (excepto el **Mercado Negro**, que rota y se mueve).
  - **Viaje Rápido (TP)** con animación de cámara aérea estilo *GTA V*.
  - **Recursos renovables inventados** (entidades recolectables en cuevas/pisos de mazmorra, no bloques vanilla).
  - Sistema de **Amigos** (con toggle de daño amigo), **Party temporal** y **Clanes estilo Trove** (banco, permisos, icono/estandarte, mejoras, pasivas y bonus de XP por jugar juntos).
- **Idioma y Voces:**
  - **Texto en Español 100% obligatorio** (con aviso obligatorio del agente si algún recurso no está en español) + Inglés secundario opcional.
  - **Audio de voces** en Español y Japonés.

### [2026-11-09] — Confirmación de Stack 1.21.1, Tabla Elemental Visual y Auditoría de `archivos temp/`
- **Stack Cerrado:** Servidor **Purpur `1.21.1` (build 2329)** + **MythicMobs `5.14.0`** + **ModelEngine `4.1.1`** + Cliente **Fabric `1.21.1`** con mod propio superligero (`AscendantClient`) y Resource Pack.
- **Progresión de Talismanes y Habilidades:**
  - El jugador empieza con **1 ranura de Talismán** y desbloquea más completando misiones principales/bosses.
  - El jugador empieza con **1 ranura equipada de cada tipo de habilidad** (rápida, cargada, movimiento, especial, definitiva) y desbloquea ranuras adicionales con el progreso (pudiendo llegar a tener 2 definitivas, etc.).
- **Tabla Elemental Visual:** Generada y guardada en `.agents/skills/the-last-ascension/resources/tabla_elemental_ascendant.png`.
- **Auditoría de `archivos temp/` (Regla 3 de Idioma):**
  - Revisados los 4 paquetes de SamusDev (`RPG_ESSENTIALS_CORE v1.1`, `VOL1 v1.1`, `VOL2`, `TRAINING_DUMMY_PACK v1.1`).
  - **Aviso de Idioma:** Se ha detectado que **todos los textos, nombres de ítems, etiquetas de NPCs y menús dentro de los 4 paquetes vienen en Inglés**. Se notifica al usuario para proceder a su traducción completa al Español.

### [2026-11-09] — Vivienda/Inmobiliaria, 8 Elementos con Doble Reacción, Arquitectura de Carpetas y Flujo con IntelliJ
- **Sistema de Vivienda e Inmobiliaria:**
  - En las ciudades habrá casas preconstruidas para **alquilar o comprar** (sin construcción libre fuera).
  - Permite invitar amigos, compartir el pago del alquiler y decorar/modificar el interior.
  - Si se acaba el alquiler, **todos los bloques colocados/reemplazados y el contenido de los cofres se guardan en la nube (Inmobiliaria)** para recogerlos sin perder nada, y si vuelve a pagar permite **reconstruir la casa automáticamente** como estaba aportando los materiales.
- **Ampliación a 8 Elementos con Iconos Propios y 2 Tipos de Reacciones:**
  - Prohibido usar iconos de *Genshin Impact*; todos los iconos se pintan desde cero para el servidor.
  - Se amplía a **8 Elementos** (*Ígneo, Crio, Fulmen, Céfiro, Terra, Sylva, Umbra, Astral*) para maximizar sinergias.
  - **Diferenciación de Reacciones:**
    1. **Reacciones de Impregnación (Estado en el enemigo — 1J o Coop):** El enemigo no viene impregnado de serie; primero se le aplica un estado alterado (ej. *Quemado*) y luego se le golpea con otro elemento (ej. *Céfiro*) para detonar una reacción sobre él.
    2. **Sinergias / Ataques Combinados entre Amigos (Coop):** Dos jugadores cruzan habilidades o definitivas compatibles generando un ataque conjunto nuevo.
- **Arquitectura de Carpetas, Versionado Semántico (`X.Y.Z`) y Flujo de Creación:**
  - Estructura definida: `server/` (solo compilados + `start.bat`), `plugins/`, `mods/`, `resource packs/`, `datapacks/`, `assets/`. *(En espera de que el usuario diga "ya puedes empezar con el servidor").*
  - Versionado `X.Y.Z` obligatorio en todos los módulos (al subir `X` se reinician `Y` y `Z` a `0`; al subir `Y` se reinicia `Z` a `0`).
  - **Regla de IntelliJ IDEA:** El usuario siempre creará primero el esqueleto limpio de cualquier plugin o mod con IntelliJ y el plugin *Minecraft Development* tras nuestro aviso, y luego nosotros implementaremos todo el código dentro.
  - **Traducción pospuesta:** Recordar al usuario traducir los packs de SamusDev más adelante cuando el servidor ya esté operativo.

### [2026-11-09] — Confirmación de Arquitectura Modular (Core + Módulos) y Conexión con GitHub (`The-Last-Ascension`)
- **Plugins Modulares + Core:**
  - Se confirma que los plugins serán **100% modulares**: cada plugin (o menú) gestiona un sistema o mecánica específica.
  - Existirá un plugin **`Core`** central que agrupa la lógica transversal y muy repetible (como el motor de traducciones, helpers genéricos, base de datos y API común) para que todos los módulos lo consuman sin duplicar código.
- **Verificación de GitHub (`https://github.com/The-Last-Ascension`):**
  - Comprobado con éxito el acceso local mediante *Git Credential Manager* con la cuenta **`Sebilebi`** (`role: admin` activo en la organización `The-Last-Ascension`, `ID: 354255522`).
  - Confirmados permisos OAuth (`repo`, `read:org`, `workflow`) para listar, **crear repositorios públicos/privados** dentro de la organización y realizar commits/pushes sin haber creado ningún repositorio todavía.

### [2026-11-09] — Inicio Oficial del Servidor, Prefijo `Ascendent`, DB SQLite WAL y Mecánica de Revivir
- **Prefijo Oficial `Ascendent`:** Todo plugin, mod, resource pack, datapack o asset creado por nosotros empieza por `Ascendent` (`AscendentCore`, `AscendentCombat`, `AscendentClient`, `AscendentResourcePack`, `AscendentDatapack`, etc.).
- **Base de Datos:** Se adopta **SQLite en modo WAL con HikariCP asíncrono + Caché en RAM** dentro de `AscendentCore` (con soporte opcional para MariaDB/MySQL) para máxima velocidad en 1.21.1 y migración directa de Windows a Linux sin dependencias externas.
- **Mecánica de Revivir:** Al morir/caer en combate, un jugador puede **revivir a otro jugador**.
- **Inicialización de Carpetas y `server/`:** El usuario autoriza empezar con el servidor (*"ya puedes empezar con el servidor"*). Se crean las carpetas oficiales (`server/`, `plugins/`, `mods/`, `resource packs/`, `datapacks/`, `assets/`), se trasladan los recursos crudos a `assets/` y se deja listo `server/` con Purpur `1.21.1`, `MythicMobs`, `ModelEngine` y `start.bat`.

### [2026-11-09] — Implementación de `AscendentCore v1.0.0` y Repositorios Oficiales en GitHub
- **Repositorios Creados y Publicados en `https://github.com/The-Last-Ascension`:**
  - `AscendentSkills` (`v1.0.0`)
  - `AscendentResourcePack` (`v1.0.0`)
  - `AscendentDatapack` (`v1.0.0`)
  - `AscendentCore` (`v1.0.0`)
- **Arquitectura de `AscendentCore v1.0.0` (`com.thelastascension.ascendentCore`):**
  - `LangManager`: Motor transversal de idiomas (`es_es.yml` obligatorio/primario y `en_us.yml` secundario) con auditoría automática de claves que falten en español y registro abierto para todos los plugins modulares.
  - `DatabaseManager`: Pool `HikariCP` con **SQLite en modo WAL** (`data/ascendent.db`) por defecto y soporte para **MariaDB/MySQL**, con hilos virtuales (`VirtualThreads` de Java 21) y `executeSchema()` para tablas de plugins hijos.
  - `ProfileManager` + `PlayerProfile`: Caché en RAM de perfiles de jugadores (Nivel Global, XP, Puntos de Estadística Globales estilo *Trove*, Monedas, Huecos de Talismán estilo *Elden Ring*, Clase Activa, Idioma, Barra de Stun estilo *Grounded 2* y estado Abatido/Revivir).
  - `ElementType` & `StatType`: Los 8 elementos y las 10 estadísticas base unificadas.
  - `ModuleRegistry` & `AscendentModule`: API de registro para plugins modulares hijos (`AscendentCombat`, `AscendentClasses`, `AscendentHousing`, `AscendentClans`, etc.).
  - `ClientBridge`: Canal de paquetes `ascendent:main` listo para comunicarse con `AscendentClient` (Fabric `1.21.1`).
  - `AscendentCommand`: Comando `/ascendent` (`/asc`) con subcomandos `info`, `stats`, `modulos`, `idioma` y `reload`.
  - Tarea Gradle `deployToServer`: Cada `./gradlew build` copia automáticamente `AscendentCore-1.0.0.jar` a `server/plugins/`.

### [2026-11-09] — Implementación de `AscendentCombat v1.0.0`, Repositorio en GitHub y Perfil Cliente en CurseForge
- **Perfil Cliente en CurseForge (`The Last Ascension`):**
  - Versión de Minecraft: **`1.21.1`**
  - Cargador de mods: **`Fabric`** (`fabric-0.20.1`) + **Fabric API** recomendada.
- **Implementación de `AscendentCombat v1.0.0` (`com.thelastascension.ascendentCombat`):**
  - Registrado automáticamente como módulo hijo en `AscendentCore` (`ModuleRegistry`) y en `LangManager` (`es_es.yml` primario + `en_us.yml` secundario).
  - **`WeaponCombatTags`:** Propiedades configurables por arma mediante `PersistentDataContainer` (`can_block`, `can_parry`, `element`, `block_mitigation`) y flag `unparryable_attack` en entidades enemigas.
  - **`ParryAndStunManager` (Estilo *Grounded 2*):**
    - Clic derecho abre ventana de Parry perfecto (`260ms`) y guardia activa (`1100ms`).
    - Si el ataque enemigo es **parreable** y entra en ventana de Parry: `0` daño recibido, sonido y chispas de parry, empuje y subida fuerte de **Stun al enemigo**.
    - Si el ataque enemigo **NO es parreable** (o es bloqueo normal): aviso de *Ataque Imparable*, mitigación parcial de daño y subida del **Stun propio del jugador** (si llega al máximo, rompe guardia y aturde al jugador).
    - Cuando la barra de Stun de un enemigo llega al 100%, entra en estado **Aturdido** (*Stunned*: halo de partículas sobre la cabeza, IA pausada y sin poder atacar durante `4s`).
  - **`ElementalReactionManager` (8 Elementos + Doble Reacción):**
    - **Tipo 1 (Impregnación en enemigo, 1J/Coop):** Los enemigos empiezan sin elemento impregnado; el primer elemento aplica su estado alterado (`8s`) y un segundo elemento distinto detona la Reacción de Impregnación (*Tormenta Ígnea*, *Combustión Abisal*, *Superconductividad*, *Eclipse Cósmico*, etc.) con daño y Stun extra.
    - **Tipo 2 (Definitiva Conjunta entre Amigos, Coop):** Abre una ventana de sinergia elemental (`4s`, `12` bloques) para que un segundo compañero combine otro elemento y desate una **Definitiva Conjunta** en área.
  - **`DownedReviveManager` (Abatido y Revivir):**
    - Al recibir daño letal, el jugador cae **Abatido** (`30s` de cuenta atrás en postura arrastrándose) en vez de morir al instante.
    - Un aliado cercano (`<= 3.5` bloques) manteniendo `Shift` canaliza el revivir durante `3.0s` con barra de progreso en tiempo real, levantándolo con el `40%` de su vida máxima.
  - **`CombatCommand` (`/combat` / `/asccombat`):** Subcomandos `info`, `weapon`, `dummy [parryable|unparryable]`, `coop <elemento> [solo]`, `downed` y `revive`.
  - Publicado en `https://github.com/The-Last-Ascension/AscendentCombat` (`v1.0.0`).

### [2026-11-09] — Implementación de `AscendentClasses v1.0.0` (Clases, Habilidades Evolutivas, Armaduras y Talismanes)
- **Implementación de `AscendentClasses v1.0.0` (`com.thelastascension.ascendentClasses`):**
  - Registrado en `AscendentCore` (`ModuleRegistry` y `LangManager` con `es_es.yml` primario + `en_us.yml` secundario).
  - **Catálogo de 12 Clases (`ClassAndTalismanRegistry`):**
    - **4 Clases Iniciales (*Pokémon Starters*):** `vanguardia` (*Vanguardia*), `filo_sombra` (*Filo de Sombra*), `arcanista` (*Arcanista Elemental*) y `custodio_sylva` (*Custodio Sylva*).
    - **8 Ascensiones/Evoluciones (Nivel 10 de clase base):** `paladin_astral`, `coloso_igneo`, `monarca_umbra`, `tempestad_cefiro`, `sabio_abismo`, `soberano_fulmen`, `druida_primordial` y `oraculo_estelar`.
  - **Separación de Puntos y Tablas SQL (`ascendent_class_progress` y `ascendent_player_gear`):**
    - Cambiar de clase es gratuito estilo *Trove*: guarda el nivel, puntos de habilidad y mejoras de cada clase por separado, mientras que los **Puntos de Estadística Globales** persisten siempre en el jugador.
    - Incluye **Respec** (reseteo de estadísticas globales o habilidades de clase con monedas).
  - **Habilidades Evolutivas por Categoría (`RAPIDA`, `CARGADA`, `MOVIMIENTO`, `ESPECIAL`, `DEFINITIVA`):**
    - Mejorables del Nivel 1 al 5 (+25% daño, +20% Stun y +0.6 bloques de tamaño AoE por nivel).
    - Las Definitivas se integran automáticamente con `AscendentCombat` abriendo/detonando ventanas de **Definitiva Conjunta Cooperativa (Tipo 2)**.
  - **Armaduras Inteligentes y Talismanes estilo *Elden Ring*:**
    - Armaduras con **Estadísticas Base Universales** (activas en cualquier clase) y **Pasivas/Bonos Exclusivos** que solo se activan si llevas la clase requerida o su evolución.
    - 6 Talismanes equipables respetando las ranuras desbloqueadas (`unlocked_talisman_slots`, empezando con 1).
  - **Menú GUI con 4 Pestañas (`ClassMenuGui` — `/clase`):** Pestañas interactivas para Clases/Ascensiones, Estadísticas Globales, Habilidades de Clase y Bolsa de Talismanes.
  - Publicado en `https://github.com/The-Last-Ascension/AscendentClasses` (`v1.0.0`).

---

## Lecciones Técnicas y Resolución de Bugs

- **Lección 1 (Gradle 9.9+ Configuration Cache en `deployToServer`):** En `build.gradle.kts` con `org.gradle.configuration-cache=true`, nunca referenciar `project.version` dentro del bloque `rename { ... }` de una tarea `Copy` en tiempo de ejecución. Capturar siempre `val pluginVersion = project.version.toString()` fuera del bloque de la tarea.
- **Lección 2 (Comillas obligatorias en `description` dentro de `plugin.yml`):** La plantilla por defecto de IntelliJ escribe `description: $description` sin comillas. Si la descripción en `gradle.properties` contiene dos puntos (`:`), SnakeYAML falla al arrancar Purpur con `ScannerException: mapping values are not allowed here`. Siempre envolver entre comillas dobles `description: "${description}"` en `plugin.yml` (aplicado en `AscendentCore v1.0.1`).
- **Lección 3 (Iniciar siempre el servidor en ventana visible con `start.bat`):** Al iniciar el servidor en local desde el agente, nunca dejarlo oculto solo en un proceso interno invisible; lanzarlo siempre abriendo una ventana de consola visible (`Start-Process cmd.exe -ArgumentList "/c start.bat" -WorkingDirectory "...\server"`) para que el usuario vea el log en tiempo real e interactúe con la consola directamente.
- **Lección 4 (`ConcurrentHashMap.entrySet().removeIf` no admite `entry.setValue` en Java 21):** En Java 21, `ConcurrentHashMap.removeEntryIf` evalúa el predicado pasando un `AbstractMap.SimpleImmutableEntry`, por lo que llamar a `entry.setValue(...)` dentro de `removeIf` lanza `UnsupportedOperationException`. Para actualizar o eliminar entradas atómicamente en un `ConcurrentHashMap`, usar siempre `map.computeIfPresent(key, (k, v) -> nuevoValor <= 0 ? null : nuevoValor)` (corregido en `AscendentCombat v1.0.1`).
- **Lección 5 (Verificar y detener instancia previa antes de iniciar el servidor):** Antes de lanzar `start.bat`, comprobar siempre si ya existe un proceso Java ejecutando `purpur-1.21.1-2329.jar` (o escuchando en `:25565`). Si está encendido, detenerlo limpiamente y esperar a que se cierre antes de volver a ejecutarlo para evitar errores de `Failed to bind to port`.
- **Lección 6 (Declarar `inputs.properties(props)` en `processResources` de Gradle):** En `build.gradle.kts`, si no se añade `inputs.properties(props)` dentro de `processResources`, Gradle marca `:processResources` como `UP-TO-DATE` al cambiar `version` en `gradle.properties` y deja la versión antigua dentro de `plugin.yml`. Añadido `inputs.properties(props)` en todos los plugins.
