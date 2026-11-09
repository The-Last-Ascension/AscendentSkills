---
name: the-last-ascension
description: >-
  Documentación viva, arquitectura técnica, lore, mecánicas de combate (Parry estilo Grounded 2,
  Sinergias Elementales y Definitivas Conjuntas), progresión de clases (estilo Trove + Pokémon),
  integración de assets (SamusDev, modelos, voces ES/JP, UI con tabs) y registro evolutivo para
  el servidor RPG de Minecraft "The Last Ascension" (Ascendant). Úsala y actualízala automáticamente
  en cualquier tarea o conversación de este proyecto.
---

# The Last Ascension (Ascendant) — Guía Central y Documentación Viva

Esta skill es el cerebro persistente del proyecto **The Last Ascension** (nombre corto / ciudad principal: **Ascendant**). Permite que cualquier sesión o agente comprenda de inmediato el estado del servidor, sus normas inquebrantables, su arquitectura técnica y las decisiones tomadas hasta la fecha.

---

## 1. Identidad y Normas Inquebrantables del Proyecto

- **Nombre del Proyecto:** `The Last Ascension` (Abreviatura / Ciudad Central: `Ascendant`).
- **Propósito:** Servidor RPG de Minecraft con historia lineal, clases, voces, menús interactivos complejos y combate técnico cooperativo, diseñado **exclusivamente para jugar entre amigos** (privado).
- **Regla Estricta Anti-RMT:** Está **terminantemente prohibido** cualquier sistema de micropagos o compras con dinero real. Toda la economía, equipamiento, monturas y mascotas se obtienen 100% jugando.
- **Regla Estricta de Idioma (Español Obligatorio):**
  - **Texto:** Todo texto del juego **debe estar en Español** (con soporte secundario opcional en Inglés). Si algún asset, plugin, mod o resource pack no tiene su texto en español (y el usuario no ha ordenado ya traducirlo en ese mismo mensaje), **es obligatorio avisar al 100% al usuario** y preguntarle si quiere añadir la traducción completa al español.
  - **Voces (Audio):** Soporte dual para voces en **Español** y en **Japonés**.
- **Filosofía de Desarrollo ("Sintonía Total"):** Prácticamente todos los plugins/sistemas nucleares (combate, clases, clanes, economía, menús, atributos, talismanes, pets, monturas, nodos de recursos) se desarrollan a medida para que todo funcione en perfecta sinergia junto a los assets de **SamusDev** (*MythicMobs* + *ModelEngine 4*).

---

## 2. Ambientación, Lore e Inspiraciones

- **Estructura Narrativa:** Historia lineal principal acompañada de misiones secundarias y misiones de clase.
- **Inspiraciones Principales:**
  1. **Sword Art Online (SAO):** Mazmorras por pisos (bloques de 5 salas y un Boss cada 5 pisos), gremios, sensación de progresión y habilidades de arma.
  2. **DanMachi:** Ciudades conectadas a sus propias mazmorras que los jugadores deben conquistar piso a piso, herrerías y progreso de aventureros.
  3. **Grounded / Grounded 2:** Sistema de combate con **Parry en clic derecho**, bloqueo con mitigación gradual que sube el propio Stun del jugador, ataques cargados/rápidos y animaciones claras de **Stun**.
  4. **Genshin Impact / Wuthering Waves:** **Elementos propios con nombres e identidades inventadas**, estados alterados únicos, **Reacciones Elementales** entre compañeros y **Definitivas Conjuntas** con animación y efectos nuevos.
  5. **Trove & Pokémon:** Elección de clase inicial tipo *Starters*, cambio libre y gratuito de clase conservando estadísticas globales de jugador (*Trove*), y sistema de Clanes con niveles, pasivas y bonus de XP por jugar juntos.
  6. **Elden Ring:** Sistema de **Talismanes** equipables que otorgan pasivas y atributos especiales.
  7. **Solo Leveling & Mushoku Tensei:** Estética de habilidades, invocaciones/sombras, rangos mágicos y construcción de mundo.

---

## 3. Documentación Modular de Sistemas (`./references/`)

Para mantener el contexto limpio y detallado, consulta y actualiza estos documentos según el sistema en el que trabajes:

1. **[Combate, Parry, Stun y Sinergias Elementales](./references/combat_and_elements.md)**
   - Parry con clic derecho (`can_parry` / `can_block` en armas, ataques `parryable` vs solo bloqueables con subida de stun propio estilo *Grounded*).
   - Animaciones de Stun (*Grounded 2*), ataques rápidos/cargados/especiales/definitivas, mejora evolutiva de habilidades (tamaño, daño, efectos y animaciones).
   - Elementos inventados, reacciones elementales y **Definitivas Conjuntas cooperativas**.
2. **[Clases, Equipamiento, Talismanes, Pets y Monturas](./references/classes_and_gear.md)**
   - Elección inicial estilo Pokémon, separación entre **Puntos de Estadística Globales** (persisten al cambiar de clase) y **Puntos de Habilidad de Clase** (independientes por clase, estilo *Trove*), reseteo con moneda/ítem de dungeon.
   - Armaduras universales en stats base pero con pasivas/sets exclusivos por clase, **Talismanes estilo Elden Ring**, **1 Pet activa** (pasiva/combate/híbrida) y **Monturas** (Terrestres, Voladoras, Acuáticas con permisos por zona y habilidades).
3. **[Mundo, Mazmorras, Vivienda, Recursos Renovables, Clanes e Idioma](./references/world_and_systems.md)**
   - Ciudades con su propia mazmorra (boss cada 5 pisos), **sincronización global de herreros/tiendas** al desbloquear sets en cualquier ciudad, **Mercado Negro** rotativo/móvil y **Viaje Rápido con cámara estilo GTA V**.
   - **Sistema de Vivienda e Inmobiliaria:** Compra/alquiler de casas en ciudades, gastos compartidos, guardado en la nube de bloques y cofres si expira el alquiler, y reconstrucción automática.
   - Materiales inventados en **nodos-entidad renovables**, sistema de Amigos, Party y **Clanes estilo Trove** (banco, permisos, estandarte, mejoras y XP grupal).
4. **[Arquitectura de Carpetas, Versionado (`X.Y.Z`) y Regla de IntelliJ IDEA](./references/architecture_and_workflow.md)**
   - Estructura raíz (`server/`, `plugins/`, `mods/`, `resource packs/`, `datapacks/`, `assets/`), versionado de 3 cifras (`X.Y.Z`) y **regla obligatoria de que el usuario crea primero los proyectos base de plugins/mods en IntelliJ IDEA**.
5. **[Catálogo de Assets Base y Estado de Traducción](./references/assets_inventory.md)**
   - Inventario detallado de `archivos temp/` (`Purpur 1.21.1`, `MythicMobs 5.14.0`, `ModelEngine 4.1.1` y los 4 packs de **SamusDev**: *RPG Essentials Core, Vol 1, Vol 2* y *Training Dummy*) + recordatorio de traducción pendiente al Español.
6. **[Infografía Visual de 8 Elementos y Doble Sistema de Reacciones](./resources/tabla_elemental_ascendant.png)**
   - Esquema visual con iconos 100% originales pintados por nosotros para los **8 elementos** (*Ígneo, Crio, Fulmen, Céfiro, Terra, Sylva, Umbra, Astral*), eficacias, **Reacciones de Impregnación** (1J/Coop) y **Sinergias de Ataques entre Amigos** (Coop).
7. **[Registro Evolutivo, Hitos y Bugs](./references/changelog_and_lessons.md)**
   - Historial cronológico de decisiones y soluciones técnicas.

---

## 4. Arquitectura Técnica Confirmada

- **Servidor Base (Confirmado):** **Purpur 1.21.1** (`purpur-1.21.1-2329.jar`) junto a **MythicMobs `5.14.0`** (Free) y **ModelEngine `4.1.1`** (Free) y nuestro plugin central propio **`AscendantCore`**.
- **Cliente (Confirmado):** **Fabric 1.21.1** con nuestro **Mod Cliente Superligero (`AscendantClient`)** comunicado por paquetes con Purpur + **Resource Pack del Servidor**.

---

## 5. Protocolo de Auto-Mejora Continua (Obligatorio)

Esta skill está diseñada para **mejorarse y actualizarse automáticamente** a medida que avanza el proyecto, sin necesidad de que el usuario lo pida explícitamente en cada mensaje.

### Cuándo Actualizar Automáticamente Esta Skill:
1. **Planificación y Decisiones de Diseño:** Cada vez que el usuario responda preguntas, defina elementos, clases, assets de SamusDev, menús o mecánicas.
2. **Nuevas Implementaciones:** Cuando se cree o modifique cualquier plugin, mod, datapack, resource pack, modelo 3D o sistema.
3. **Bugs y Lecciones Técnicas:** Regístralos en [references/changelog_and_lessons.md](./references/changelog_and_lessons.md) con *Problema -> Causa -> Solución*.
4. **Petición Directa:** Siempre que el usuario pida guardar o recordar algo en la skill.

### Cuándo NO Actualizar:
- Si el comentario o cambio ya está documentado o no aporta información nueva ni relevante para futuras sesiones.
