# Catálogo de Assets y Archivos Base (`archivos temp/`)

Este documento registra los binarios de servidor, plugins base y paquetes de **SamusDev** disponibles en el proyecto, así como su estado de integración y localización al Español.

---

## 1. Motor y Plugins Base (`archivos temp/`)

| Archivo | Versión | Rol en *The Last Ascension* |
| :--- | :--- | :--- |
| `purpur-1.21.1-2329.jar` | Purpur `1.21.1` (Build 2329) | Motor principal del servidor (Paper API). |
| `ModelEngine-4.1.1.jar` | `4.1.1` (Plan Gratuito inicial) | Renderizado y animación de modelos 3D (`.bbmodel`) de NPCs, nodos, trampas, monturas, pets y bosses. |
| `MythicMobs-5.14.0.jar` | `5.14.0` (Plan Gratuito inicial) | Gestión de entidades custom, IA base y ejecución de skills de SamusDev conectadas a `AscendantCore`. |

---

## 2. Paquetes de Assets de SamusDev (`samus2002_*`)

### A. `samus2002_RPG_ESSENTIALS_CORE [v1.1].zip`
- **NPCs 3D (`ModelEngine/blueprints/npc_*.bbmodel` + Avatares PNG):**
  - `npc_banker` (Banquero / Banco Personal y de Clan)
  - `npc_merchant_armor` y `npc_merchant_weapon` (Herreros sincronizados globalmente entre ciudades)
  - `npc_merchant_forbidden` (**Mercader del Mercado Negro** rotativo/móvil)
  - `npc_merchant_jewelry` (Mercader de Joyas / **Talismanes estilo Elden Ring**)
  - `npc_merchant_pet` (Mercader de **Mascotas / Pets**)
  - `npc_merchant_potion`, `npc_merchant_basic`, `npc_merchant_wandering`
  - `npc_quest_master` (Maestro de Misiones principales/secundarias/clase)
  - `npc_healing_fairy`, `npc_mayor`, `npc_guard`, `npc_villager_f/m` (y variantes sentadas)
- **Objetos Interactivos 3D (`obj_*.bbmodel`):**
  - `obj_portal_dungeon`, `obj_portal_basic`, `obj_portal_sanctuary`, `obj_portal_unstable` (Portales de acceso a Mazmorras y Pisos)
  - `obj_waypoint_gate` (Puerta de **Viaje Rápido** con cámara estilo *GTA V*)
  - `obj_storage_chest` (Cofre de almacenamiento/banco)
- **Economía Visual:** Modelos y texturas de monedas (`coin`, `coin_bundle`, `coin_stacked`).

### B. `samus2002_RPG_ESSENTIALS_VOL1_v1.1.zip`
- **Nodos de Minerales Renovables (Entidades 3D `ore_*.bbmodel` + Lingotes `bar_*`):**
  - Cobre (`copper`), Hierro (`iron`), Oro (`gold`), Esmeralda (`emerald`), Diamante (`diamond`), Rubí (`ruby`), Zafiro (`sapphire`), Topacio (`topaz`) y **Dragonita** (`dragonite`), además de `rock`, `boulder`, `pebbles_1/2`, `log` y `twig`.
- **Cofres y Llaves Temáticas/Elementales (`chest_*` + `key_*`):**
  - `wooden`, `golden`, `bone`, `aqua`, `fire/magma`, `ice`, `wind`, `forest`, `light`, `shadow`.
- **Runas y Piedras Rúnicas (Ideales para Mejora de Habilidades y Buffs):**
  - Runas (`rune_aqua`, `fire`, `ice`, `light`, `nature`, `shadow`, `undead`, `wind`).
  - Piedras rúnicas 3D (`runestone_heal`, `resistance`, `speed`, `strength`).
- **Objetos Rompibles / Interactivos de Mazmorra:**
  - `barrel_explosive`, `barrel_poison`, `vase_common`, `vase_small`, `vase_tall`.

### C. `samus2002_RPG_ESSENTIALS_VOL2.zip`
- **Flora y Recursos Alquímicos Renovables (Entidades 3D `.bbmodel` + Ítems):**
  - `deathbloom`, `magical_herb`, `mushroom_glowing`, `mushroom_red`, `four_leaf_clover`, `shamrock`, `wild_berry`, `cactus`.
- **Trampas 3D de Mazmorra (`ModelEngine/blueprints/*_trap*.bbmodel`):**
  - `flame_trap`, `sawblade_trap_long`, `sawblade_trap_short`, `spike_ball_trap`, `spike_trap_pop_up`, `spike_trap_still`.
- **Viaje y Consumibles:**
  - `waystone.bbmodel`, `portal.bbmodel`, `portal_round.bbmodel`.
  - Pociones (`potion_minor`, `small`, `large`, `superior`, `eternal`) y pergaminos (`scroll_return`, `scroll_teleport`).

### D. `samus2002_TRAINING_DUMMY_PACK_v1.1-dqx5zn.zip`
- **Muñeco de Entrenamiento (`dummy.bbmodel`):**
  - Entidad inmóvil con animación de impacto (`state{s=hit}`), ideal para testear el **Parry**, la **Barra de Stun**, los **Ataques Cargados** y las **Reacciones Elementales**.

---

## 3. Estado de Integración y Traducción al Español (Regla 3)

- **Integración Técnica (Completada en Punto 4):**
  - **ModelEngine (`server/plugins/ModelEngine/`):** Extraídos los **73 modelos `.bbmodel`** completos en `blueprints_library/` y activados los **12 modelos principales de showcase** en `blueprints/` (límite de la versión gratuita de `ModelEngine 4.1.1`: `dummy`, `npc_quest_master`, `npc_merchant_weapon`, `npc_merchant_armor`, `npc_merchant_potion`, `npc_banker`, `npc_healing_fairy`, `obj_portal_dungeon`, `obj_waypoint_gate`, `runestone_heal`, `ore_dragonite`, `chest_golden`).
  - **MythicMobs (`server/plugins/MythicMobs/packs/AscendentSamus/`):** Integrados los **16 archivos YAML** (`89` Mobs/NPCs/Nodos, `53` Ítems y `456` Skills), adaptados para funcionar sin errores de placeholders de pago en `MythicMobs Free 5.14.0`.
  - **Resource Pack Unificado (`resource packs/AscendentResourcePack` `v1.1.0`):** Fusionados los modelos/texturas de `RPG_ESSENTIALS_CORE`, `VOL1`, `VOL2` (`paper.json`, `feather.json` con 45 `custom_model_data` `2000..2044` y `atlases/blocks.json`) junto con el resource pack compilado de `ModelEngine`, y sincronizado automáticamente en el perfil de CurseForge (`The Last Ascension/resourcepacks/AscendentResourcePack`).
- **Estado de Idioma Actual:** **100% EN INGLÉS** en los 16 archivos YAML de `AscendentSamus` (`[Merchant]`, `[Banker]`, `Copper Bar`, `Dragonite Bar`, `Deathbloom`, `Magical Herb`, `Training Dummy`, menús y diálogos).
- **Acción Requerida (Regla 3):** Avisado al usuario tras completar el Punto 4 para confirmar si desea traducir ahora mismo todos los NPCs, ítems, menús y textos de SamusDev al **Español**.
