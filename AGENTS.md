# Reglas del Proyecto: The Last Ascension (Ascendant)

1. **Lectura Obligatoria de Contexto:**
   - Al iniciar cualquier tarea en este repositorio, lee siempre `.agents/skills/the-last-ascension/SKILL.md` (y sus archivos en `references/`) para conocer la arquitectura, el lore, las mecánicas de combate y las normas del servidor.

2. **Principios Inquebrantables del Servidor:**
   - **Privado para amigos / Cero Pay-to-Win:** Prohibido diseñar o incluir sistemas de pago con dinero real, tiendas VIP o mecánicas P2W.
   - **Sinergia Total:** Todos los plugins/mods, datapacks, resource packs, modelos y menús interactivos deben compartir el mismo sistema unificado de estadísticas (vida, defensa, daño mágico/elemental, resistencias elementales, barra de stun, talismanes, vivienda e inmobiliaria, y mecánica de Parry/Bloqueo estilo *Grounded 2*).

3. **Regla Estricta de Idioma (Español Obligatorio):**
   - **Texto:** Todo texto del servidor (interfaces, ítems, descripciones, misiones, mensajes) **debe estar siempre en Español** (con soporte secundario opcional en Inglés).
   - **Aviso Obligatorio del Agente:** Si al revisar o integrar cualquier plugin, mod, resource pack, datapack o asset (ej. SamusDev) detectas que algún texto NO está en español (y el usuario no te ha pedido ya expresamente traducirlo en ese mismo mensaje), **debes avisar al 100% al usuario** y preguntarle si quiere añadir/traducir todo al español. *(Nota: Los 4 packs iniciales de SamusDev están pendientes de traducir más adelante cuando el servidor esté montado; recuérdaselo al usuario llegado ese momento).*
   - **Voces:** Soporte para pistas de audio en **Español** y **Japonés**.

4. **Arquitectura de Carpetas, Prefijo `Ascendent`, Versionado (`X.Y.Z`) y Creación en IntelliJ IDEA:**
   - **Prefijo Oficial `Ascendent`:** Todos los plugins, mods, resource packs, datapacks y assets creados desde cero por nosotros deben empezar siempre por **`Ascendent`** seguido de su función (ej. `AscendentCore`, `AscendentCombat`, `AscendentClasses`, `AscendentHousing`, `AscendentClans`, `AscendentResourcePack`, `AscendentDatapack`, `AscendentClient`).
   - **Estructura de Carpetas:** `server/` (solo compilados listos + `start.bat`), `plugins/`, `mods/`, `resource packs/`, `datapacks/` y `assets/` (recursos crudos sin modificar).
   - **Consola Visible y Comprobación Previa de Servidor Encendido (`start.bat`):**
     - **Antes de iniciar el servidor (o desplegar cambios que requieran reinicio):** Comprueba **siempre** primero si el servidor ya está en ejecución (proceso `java` con `purpur-1.21.1` o puerto `25565`). Si ya está encendido, apágalo primero limpiamente y espera a que termine de cerrarse antes de volver a iniciarlo, para que nunca choque con una instancia ya abierta.
     - **Ventana Visible:** Siempre que inicies el servidor en local, ábrelo en una ventana visible de `cmd.exe` o `powershell` ejecutando `server\start.bat` (ej. `Start-Process cmd.exe -ArgumentList "/c start.bat" -WorkingDirectory "...\server"`) para que el usuario vea en directo la consola y el log del servidor en su pantalla, exactamente igual que si él hubiera ejecutado el `.bat`.
   - **Prohibido Crear Esqueletos de Plugins o Mods por Cuenta del Agente:** Cuando haga falta crear un plugin nuevo o un mod nuevo, **avisa primero al usuario**. El usuario lo creará con **IntelliJ IDEA (Minecraft Development)** y lo dejará en `plugins/` o `mods/`. Solo cuando el usuario avise que ya lo ha creado podrás implementar el código dentro.
   - **Versionado Semántico (`X.Y.Z`):** Todos los plugins, mods, datapacks y resource packs usan 3 números: `X` (cambios masivos/estructurales -> reinicia `Y` y `Z` a `0`, ej. `2.0.0`), `Y` (mejoras o nuevas funciones normales -> reinicia `Z` a `0`, ej. `1.3.0`), `Z` (fixes de bugs o micro-cambios, ej. `1.2.4`).

5. **Auto-Actualización Continua de `AscendentAdmin`, del Catálogo de Assets (`.docx`) y de la Skill (`.agents/skills/the-last-ascension/`):**
   - **Sincronización Obligatoria con `AscendentAdmin`:** Cada vez que en el futuro se implemente una nueva mecánica, plugin, ítem, entidad, sistema de vivienda, clanes, mascotas, monturas o mazmorras, **debes actualizar automáticamente también el plugin `AscendentAdmin`** (`/staff`, `/admin`, `/panel`) para que el Panel de Staff incluya siempre botones y herramientas para administrar, editar y probar esa nueva funcionalidad.
   - **Catálogo Visual de Assets (`assets/Catalogo_Assets_The_Last_Ascension.docx`) y Deduplicación:**
     - Siempre que se añada, actualice o elimine algún asset en `assets/`, revisa si hay duplicados o versiones repetidas y **quédate únicamente con una copia (siempre la versión más reciente/completa)**.
     - Si algún archivo comprimido (`.zip`/`.rar`) pide contraseña, usa **`BLACKSPIGOT.COM`** y déjalo desencriptado y limpio en `assets/`.
     - Actualiza automáticamente el archivo Word **`assets/Catalogo_Assets_The_Last_Ascension.docx`** (sincronizado con Google Drive) para que cada asset tenga: **Nombre y versión**, **1 única foto/captura visual representativa**, **mini-descripción en Español**, **link de descarga (BlackSpigot / fuente)** y **link oficial (`samusdev.com` / creador)**.
   - **Actualización Automática de la Skill:** Cada vez que en una conversación se planifique una mecánica, el usuario responda preguntas de diseño, se añada una mejora, se integre un asset, se modifique la arquitectura o se solucione un bug, **actualiza automáticamente** `.agents/skills/the-last-ascension/SKILL.md` y/o sus archivos en `.agents/skills/the-last-ascension/references/` sin esperar a que el usuario lo pida.
   - **Filtro de Ruido:** Si lo hablado ya está documentado o no aporta nada nuevo/relevante al proyecto, no modifiques la skill innecesariamente.
