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

## 3. Estado de Traducción al Español (Regla 3)

- **Estado Actual:** **100% EN INGLÉS** en los 4 paquetes originales (`[Merchant]`, `Copper Bar`, `Dragonite Bar`, `Deathbloom`, `Magical Herb`, `Training Dummy`, menús y skills).
- **Acción Requerida:** Avisado al usuario para confirmar la traducción íntegra al Español (manteniendo soporte secundario en Inglés) al integrarlos en el servidor.
