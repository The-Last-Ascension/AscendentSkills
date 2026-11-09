# Arquitectura del Repositorio, Prefijo `Ascendent`, Versionado y Flujo de Trabajo

---

## 1. Convención de Nombres Oficial: Prefijo `Ascendent`

Todo lo que se cree desde cero en este proyecto (plugins, mods, resource packs, datapacks, assets propios y repositorios) llevará obligatoriamente el prefijo **`Ascendent`** seguido de la mecánica o sistema:
- **Plugin Central:** `AscendentCore`
- **Plugins Modulares (Ejemplos):** `AscendentCombat`, `AscendentClasses`, `AscendentHousing`, `AscendentClans`, `AscendentMenus`, `AscendentCompanions` (Pets/Monturas), `AscendentDungeons`
- **Mod Cliente Fabric:** `AscendentClient`
- **Resource Pack y Datapack:** `AscendentResourcePack`, `AscendentDatapack`

---

## 2. Estructura de Carpetas Raíz (`The Last Ascension/`)

La raíz del proyecto está estructurada estrictamente así:

```text
The Last Ascension/
├── .agents/skills/the-last-ascension/  # Documentación viva y reglas del proyecto
├── server/                             # Servidor Purpur 1.21.1 ejecutable (con start.bat)
│                                       # SOLO contiene .jars compilados y packs listos (NO código fuente)
├── plugins/                            # Proyectos de código fuente de cada plugin (1 subcarpeta por plugin)
├── mods/                               # Proyectos de código fuente de cada mod (ej. cliente Fabric; 1 subcarpeta por mod)
├── resource packs/                     # Proyectos de desarrollo de resource packs
├── datapacks/                          # Proyectos de desarrollo de datapacks
└── assets/                             # Recursos crudos sin modificar (.zip, .jar originales, packs de SamusDev)
```

- **Entorno Local -> Linux:** El servidor dentro de `server/` se ejecutará inicialmente en local en Windows mediante un archivo `start.bat` para pruebas rápidas, y más adelante se migrará a un servidor Linux en producción.
- **Regla de Comprobación Previa + Ejecución en Ventana de Consola Visible (`start.bat`):**
  1. **Comprobar que NO esté ya encendido:** Antes de iniciar el servidor, verifica siempre si ya hay un proceso de Purpur (`purpur-1.21.1-2329.jar` / puerto `25565`) corriendo. Si ya está en ejecución y necesitas reiniciarlo, **detén primero el servidor existente y espera a que libere el puerto** antes de lanzar el nuevo.
  2. **Ventana Visible:** Cada vez que el agente inicie el servidor en local, **debe abrir una ventana real y visible de `cmd.exe` / `powershell` ejecutando `server\start.bat`** (`Start-Process cmd.exe -ArgumentList "/c start.bat" -WorkingDirectory "c:\Users\Sebilebi\source\repos\The Last Ascension\server"`) para que el usuario tenga la consola del servidor en pantalla y pueda ver los logs o escribir comandos directamente como si hubiera abierto `start.bat` él mismo.
- **Organización de GitHub (`https://github.com/The-Last-Ascension`):**
  - Conectada y verificada en local con la cuenta administradora **`Sebilebi`** (vía *Git Credential Manager* + GitHub REST API, con permisos `repo` y `admin` sobre la organización `ID: 354255522`).
  - **Qué SÍ se sube a GitHub (1 repositorio independiente por cada uno):**
    - Todos los plugins creados por nosotros (`AscendentCore`, `AscendentCombat`, etc.).
    - Todos los mods creados por nosotros (`AscendentClient`, etc.).
    - Todos los resource packs creados por nosotros (`AscendentResourcePack`).
    - Todos los datapacks creados por nosotros (`AscendentDatapack`).
    - La documentación viva / skills del proyecto (`AscendentSkills`).
  - **Qué NUNCA se sube a GitHub:**
    - Prohibido subir la carpeta `server/` ni la carpeta `assets/` (recursos descargados pesados de varios GB).

---

## 2. Arquitectura Modular de Plugins (Core + Módulos por Sistema)

- **Diseño 100% Modular:** Cada plugin (o menú) se encarga de **una única mecánica o sistema concreto** (ej. un plugin para Combate/Parry, otro para Clases, otro para Clanes, otro para Vivienda/Inmobiliaria, otro para Pets/Monturas, etc.).
- **El Plugin `AscendentCore` (Centro Neurálgico y Base de Datos):**
  - Contiene todo el código genérico, repetible y transversal que necesitan todos los demás plugins.
  - Incluye utilidades compartidas como el **sistema de traducción/localización** (Español obligatorio + Inglés opcional), registro de jugadores, atributos base y comunicación con `AscendentClient`.
  - **Base de Datos de Alto Rendimiento (Portable Windows -> Linux):** Utiliza **SQLite en modo WAL (`Write-Ahead Logging`) con HikariCP asíncrono + Caché en RAM** por defecto (cero latencia en el hilo principal y 100% autocontenido en archivo para moverlo de Windows a Linux sin instalar nada externo), con soporte configurable para **MariaDB/MySQL** si en el futuro se escalan múltiples instancias.
  - Todos los demás plugins modulares (`Ascendent*`) se conectan a `AscendentCore`.

---

## 3. Regla Estricta de Creación de Plugins y Mods (IntelliJ IDEA)

- **PROHIBIDO crear esqueletos de plugins o mods desde cero por cuenta del agente.**
- **Procedimiento Obligatorio:**
  1. Cuando se necesite un nuevo plugin o un nuevo mod, **el agente debe avisar primero al usuario** especificando todos los campos de la ventana *New Project -> Minecraft* de IntelliJ IDEA.
  2. **El usuario lo creará personalmente desde IntelliJ IDEA** usando la extensión *Minecraft Development* y dejará el proyecto base limpio dentro de `plugins/<Nombre>` o `mods/<Nombre>`.
  3. Cuando el usuario confirme (*"ya he creado este plugin/mod"*), el agente procederá a programar e implementar todo el código dentro de ese proyecto base y a vincularlo con su repositorio en `https://github.com/The-Last-Ascension`.
- **Valores Estándar para todos nuestros Plugins en IntelliJ IDEA:**
  - **Location:** `C:\Users\Sebilebi\source\repos\The Last Ascension\plugins`
  - **Groups / Templates:** `Plugin` -> `Paper`
  - **Build System:** `Gradle`
    - **Use Gradle version catalog:** Desmarcado (`[ ]`)
    - **Gradle Plugins:**
      - `Use run-paper Gradle plugin`: Desmarcado (`[ ]`, ya usamos nuestro `server/` propio con Purpur)
      - `Use shadow Gradle plugin`: **Marcado (`[x]`)** en `AscendentCore` (para empaquetar HikariCP/SQLite en el `.jar`) y desmarcado en módulos ligeros que solo dependan de `AscendentCore`.
      - Resto (`paperweight-userdev`, `resource-factory`, `gremlin`): Desmarcados (`[ ]`).
  - **Language:** `Java`
  - **Minecraft Version:** `1.21.1`
  - **Group ID:** `com.thelastascension`
  - **Version:** `1.0.0`
  - **JDK:** `21 Oracle OpenJDK 21.0.12`

---

## 4. Estándar de Versionado Semántico (`X.Y.Z`)

Todos los plugins, mods, resource packs y datapacks del proyecto deben seguir rigurosamente el esquema de 3 números `Mayor.Menor.Parche` (ej. `1.2.3`):

1. **Primer Número (`X` — Mayor):** Cambios muy grandes, rediseños profundos o cambios de sistema en ese componente.
   - Al incrementar `X`, los dos números de la derecha se reinician a `0` (ej. `1.3.4` $\rightarrow$ `2.0.0`).
2. **Segundo Número (`Y` — Menor):** Mejoras nuevas o implementaciones de funcionalidades normales.
   - Al incrementar `Y`, el número de la derecha (`Z`) se reinicia a `0` (ej. `1.2.4` $\rightarrow$ `1.3.0`).
3. **Tercer Número (`Z` — Parche):** Corrección de bugs (`fixes`) o micro-implementaciones muy pequeñas.
   - Solo incrementa el último dígito (ej. `1.2.3` $\rightarrow$ `1.2.4`).
