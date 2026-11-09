# Catálogo de Assets y Archivos Base (`assets/`)

Este documento registra todos los motores de servidor, plugins premium desbloqueados y paquetes de **SamusDev** disponibles en `assets/`, sincronizados con el documento visual de Word/Google Drive **`assets/Catalogo_Assets_The_Last_Ascension.docx`**.

> **Regla de Mantenimiento (`AGENTS.md` Regla 5):**
> - **Deduplicación:** En `assets/` solo debe existir **una única copia** de cada asset (siempre la versión más reciente).
> - **Contraseña de Archivos:** Si un `.zip` o `.rar` descargado pide contraseña, es **`BLACKSPIGOT.COM`** (y debe re-empaquetarse/extraerse sin contraseña en `assets/`).
> - **Sincronización con Word/Drive:** Cada vez que se añada, actualice o elimine un asset en `assets/`, se debe regenerar/actualizar **`assets/Catalogo_Assets_The_Last_Ascension.docx`** (usando `scratch/build_openxml_docx.ps1`) con: Nombre, 1 foto representativa, mini-descripción en Español, link de descarga (BlackSpigot) y link oficial (`samusdev.com` / creador).

---

## 1. Motores del Servidor y Plugins Premium (`assets/`)

| Archivo en `assets/` | Versión | Link Oficial | Rol en *The Last Ascension* |
| :--- | :--- | :--- | :--- |
| `purpur-1.21.1-2329.jar` | Purpur `1.21.1` (Build 2329) | [purpurmc.org](https://purpurmc.org/) | Motor principal del servidor (Paper API + Pufferfish SIMD). |
| `UltimateModelEngine-R4.1.1-UME.2.zip` | `R4.1.1-UME.2` (Desbloqueado) | [MythicCraft](https://mythiccraft.io/index.php?resources/model-engine-ultimate-custom-entity-model-manager-1-19-4-1-21-4.1213/) | Sustituye a `ModelEngine-4.1.1.jar` (Free eliminado). Elimina el límite de 12 modelos simultáneos, cargando los **73+ `.bbmodel`** completos en `server/plugins/ModelEngine/blueprints/`. |
| `MythicMobs-5.13.1-community.1.zip` | `5.13.1-community.1` (Premium) | [MythicCraft](https://mythiccraft.io/index.php?resources/mythicmobs.1/) | Sustituye a `MythicMobs-5.14.0.jar` (Free eliminado). Activa `isVolatile() = true` (matemáticas, `<random.float>`, variables de caster y proyectiles complejos de SamusDev). |
| `ItemsAdder.jar` | `4.0.18-community.1` | [itemsadder.devs.beer](https://itemsadder.devs.beer/) | Gestor opcional de Resource Pack, HUDs, Font Images e Ítems Custom. |
| `Oraxen-1.219.0-community.1.zip` | `1.219.0-community.1` | [docs.oraxen.com](https://docs.oraxen.com/) | Gestor alternativo de Resource Pack, Glifos Unicode, Armaduras y Mobiliario 3D con código fuente incluido. |

---

## 2. Packs Esenciales y Sistemas Base de SamusDev (`assets/`)

| # | Nombre y Versión | Archivo en `assets/` | Link Descarga | Link Oficial (`samusdev.com`) |
| :-: | :--- | :--- | :--- | :--- |
| 1 | **RPG Essentials Core (v1.1)** | `samus2002_RPG_ESSENTIALS_CORE [v1.1].zip` | [NullForums](https://nullforums.net/resources/rpg-essentials-core.11077/) | [samusdev.com/product/rpg-essentials-core/](https://samusdev.com/product/rpg-essentials-core/) |
| 2 | **RPG Essentials Vol 1 (v1.1)** | `samus2002_RPG_ESSENTIALS_VOL1_v1.1.zip` | [NullForums](https://nullforums.net/resources/samusdev-rpg-essentials-vol-1-v1-1.5019/) | [samusdev.com/product/rpg-essentials-vol-1/](https://samusdev.com/product/rpg-essentials-vol-1/) |
| 3 | **RPG Essentials Vol 2 (v1.0)** | `samus2002_RPG_ESSENTIALS_VOL2.zip` | [BlackSpigot .21888](https://www.blackspigot.com/leaked-minecraft-plugins/rpg-essentials-vol-2.21888/) | [samusdev.com/product/rpg-essentials-vol-2/](https://samusdev.com/product/rpg-essentials-vol-2/) |
| 4 | **RPG Essentials Vol 3 (v1.0)** | `samus2002_RPG_ESSENTIALS_VOL3.zip` | [BlackSpigot .21970](https://www.blackspigot.com/leaked-minecraft-plugins/rpg-essentials-vol-3.21970/) | [samusdev.com/product/rpg-essentials-vol-3/](https://samusdev.com/product/rpg-essentials-vol-3/) |
| 5 | **RPG Class Essentials Vol 1 (v1.0)** | `samus2002_RPG_CLASS_ESSENTIALS_VOL1_PACK.zip` | [BlackSpigot .1823](https://www.blackspigot.com/leaked-minecraft-plugins/rpg-class-essentials-vol-1.1823/) | [samusdev.com/product/rpg-class-essentials-vol-1/](https://samusdev.com/product/rpg-class-essentials-vol-1/) |
| 6 | **Training Dummy Pack (v1.1)** | `samus2002_TRAINING_DUMMY_PACK_v1.1.zip` | [NullForums](https://nullforums.net/resources/training-dummy-v1-1.7797/) | [samusdev.com/product/training-dummy/](https://samusdev.com/product/training-dummy/) |

---

## 3. Paquetes de Clases RPG y Jefes de SamusDev (`assets/`)

| # | Nombre y Versión | Archivo en `assets/` | Link Descarga (BlackSpigot) | Link Oficial (`samusdev.com`) |
| :-: | :--- | :--- | :--- | :--- |
| 7 | **RPG Class Series \| Archer (v1.8)** *(Eliminado duplicado antiguo v1.0)* | `[Samus2002] RPG Class Series Archer.zip` | [BlackSpigot .1649](https://www.blackspigot.com/leaked-minecraft-plugins/rpg-class-series-archer-v1-8.1649/) | [samusdev.com/product/rpg-class-series-archer/](https://samusdev.com/product/rpg-class-series-archer/) |
| 8 | **RPG Class Series \| Archmage (v1.3)** | `[Samus2002] RPG Class Series Archmage.zip` | [BlackSpigot .1626](https://www.blackspigot.com/leaked-minecraft-plugins/rpg-class-series-archmage-v1-3.1626/) | [samusdev.com/product/rpg-class-series-archmage/](https://samusdev.com/product/rpg-class-series-archmage/) |
| 9 | **RPG Class Series \| Bard (v1.2)** | `samus2002_BARD_PACK_v1.2.rar` | [BlackSpigot .1212](https://www.blackspigot.com/leaked-minecraft-plugins/rpg-class-series-bard-v1-2.1212/) | [samusdev.com/product/rpg-class-series-bard/](https://samusdev.com/product/rpg-class-series-bard/) |
| 10 | **RPG Class Series \| Monk (v1.1)** | `samus2002_MONK_PACK_v1.1.zip` | [BlackSpigot .1724](https://www.blackspigot.com/leaked-minecraft-plugins/rpg-class-series-monk-v1-1.1724/) | [samusdev.com/product/rpg-class-series-monk/](https://samusdev.com/product/rpg-class-series-monk/) |
| 11 | **RPG Class Series \| Shaman (v1.0)** | `samus2002_SHAMAN_PACK.zip` | [BlackSpigot .1189](https://www.blackspigot.com/leaked-minecraft-plugins/rpg-class-series-shaman.1189/) | [samusdev.com/product/rpg-class-series-shaman/](https://samusdev.com/product/rpg-class-series-shaman/) |
| 12 | **RPG Class Awakened \| Archer (v1.0)** | `samus2002_AWAKENED_ARCHER.zip` | [BlackSpigot .2285](https://www.blackspigot.com/leaked-minecraft-plugins/rpg-class-awakened-archer.2285/) | [samusdev.com/product/rpg-class-awakened-archer/](https://samusdev.com/product/rpg-class-awakened-archer/) |
| 13 | **RPG Class Awakened \| Cleric (v1.0)** | `samus2002_AWAKENED_CLERIC.zip` | [BlackSpigot .22122](https://www.blackspigot.com/leaked-minecraft-plugins/rpg-class-awakened-cleric.22122/) | [samusdev.com/product/rpg-class-awakened-cleric/](https://samusdev.com/product/rpg-class-awakened-cleric/) |
| 14 | **RPG Class Awakened \| Dragon Warrior (v1.0)** | `samus2002_AWAKENED_DRAGON_WARRIOR.zip` | [BlackSpigot .217](https://www.blackspigot.com/leaked-minecraft-plugins/rpg-class-awakened-dragon-warrior.217/) | [samusdev.com/product/rpg-class-awakened-dragon-warrior/](https://samusdev.com/product/rpg-class-awakened-dragon-warrior/) |
| 15 | **RPG Class Awakened \| Mage (v1.0)** *(Extraído de `archive.zip`)* | `samus2002_AWAKENED_MAGE.zip` | [BlackSpigot .2324](https://www.blackspigot.com/leaked-minecraft-plugins/rpg-class-awakened-mage.2324/) | [samusdev.com/product/rpg-class-awakened-mage/](https://samusdev.com/product/rpg-class-awakened-mage/) |
| 16 | **RPG Class Awakened \| Shaman (v1.1)** | `samus2002_AWAKENED_SHAMANv_1.1.zip` | [BlackSpigot .304](https://www.blackspigot.com/leaked-minecraft-plugins/rpg-class-awakened-shaman.304/) | [samusdev.com/product/rpg-class-awakened-shaman/](https://samusdev.com/product/rpg-class-awakened-shaman/) |
| 17 | **RPG Class Awakened \| Spiritcaller (v1.0)** | `samus2002_AWAKENED_SPIRITCALLER.zip` | [BlackSpigot .22123](https://www.blackspigot.com/leaked-minecraft-plugins/rpg-class-awakened-spiritcaller.22123/) | [samusdev.com/product/rpg-class-awakened-spiritcaller/](https://samusdev.com/product/rpg-class-awakened-spiritcaller/) |
| 18 | **RPG Class Legends \| Death Knight (v1.1)** | `samus2002_DEATH_KNIGHT_PACK_v1.1.zip` | [BlackSpigot .2070](https://www.blackspigot.com/leaked-minecraft-plugins/rpg-class-legends-death-knight-v1-1.2070/) | [samusdev.com/product/rpg-class-legends-death-knight/](https://samusdev.com/product/rpg-class-legends-death-knight/) |
| 19 | **RPG Class Heroes \| Water Samurai (v1.0)** | `samus2002_HEROES_WATER_SAMURAI.zip` | [BlackSpigot .2282](https://www.blackspigot.com/leaked-minecraft-plugins/rpg-class-heroes-water-samurai.2282/) | [samusdev.com/product/rpg-class-heroes-water-samurai/](https://samusdev.com/product/rpg-class-heroes-water-samurai/) |
| 20 | **RPG Class Boss \| Archer (Boss Only) (v1.0)** | `samus2002_RPG_CLASS_BOSS_ARCHER_BOSS_ONLY.zip` | [BlackSpigot .2340](https://www.blackspigot.com/leaked-minecraft-plugins/rpg-class-boss-archer.2340/) | [samusdev.com/product/rpg-class-boss-archer/](https://samusdev.com/product/rpg-class-boss-archer/) |
| — | *[Pendiente de copiar `.zip` a `assets/`]* **RPG Class \| Arcane Swordweaver (COSMO)** | *(No presente aún en `assets/`)* | [BlackSpigot .688](https://www.blackspigot.com/leaked-minecraft-plugins/rpg-class-arcane-swordweaver.688/) | [MCModels](https://mcmodels.net/products/11919/cosmo-arcane-swordweaver-rpg-class) |

---

## 4. Duplicados Eliminados durante la Auditoría de `assets/`
1. **`samus2002_ARCHER_PACK.zip` (`v1.0`):** Eliminado en favor de `[Samus2002] RPG Class Series Archer.zip` (**`v1.8`**, más reciente con 312 archivos frente a 303).
2. **`samus2002_RPG_ESSENTIALS_CORE.zip.zip`:** Eliminado por ser un duplicado encriptado de `samus2002_RPG_ESSENTIALS_CORE [v1.1].zip`.
3. **Duplicado de `samus2002_RPG_ESSENTIALS_VOL2.zip`:** Se conservó la copia con `Important Stuff.txt` y fechas originales intactas y se eliminó el duplicado.
4. **`ModelEngine-4.1.1.jar` (Free Trial):** Eliminado en favor de `UltimateModelEngine-R4.1.1-UME.2.zip` (versión completa sin límite de 12 modelos).
5. **`MythicMobs-5.14.0.jar` (Free Trial):** Eliminado en favor de `MythicMobs-5.13.1-community.1.zip` (versión Premium desbloqueada con soporte completo de variables y matemáticas).
