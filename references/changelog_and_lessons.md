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

---

## Lecciones Técnicas y Resolución de Bugs

*(Se irá completando automáticamente conforme se desarrollen plugins, modelos, menús y sistemas)*
