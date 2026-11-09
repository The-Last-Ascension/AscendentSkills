# Sistema de Combate, Parry, Stun y Elementos

## 1. Mecánica de Parry y Bloqueo (Estilo *Grounded / Grounded 2*)

### A. Controles y Propiedades de Armas
- **Botón de Acción:** **Clic Derecho** es el input universal para Bloquear / hacer Parry.
- **Flags por Arma (Configurables por ítem):**
  - `can_block` (`boolean`): Define si el arma puede mantener guardia para mitigar daño.
  - `can_parry` (`boolean`): Define si el arma puede ejecutar un bloqueo perfecto (Parry). Habrá armas que no puedan ni bloquear ni hacer parry, armas que solo bloqueen, y armas con parry completo.

### B. Interacción con Ataques Enemigos (`parryable`)
Cada ataque enemigo tiene un flag `parryable` (`boolean`) y feedback visual claro:
1. **Ataque Parreable + Ventana de Parry Exacta:**
   - El jugador recibe **0 daño**.
   - El jugador no acumula Stun propio.
   - El enemigo sufre **Parry**, recibiendo un incremento fuerte en su barra de **Stun**.
2. **Ataque NO Parreable (Intentando hacer Parry) o Bloqueo Mantenido:**
   - Si el enemigo lanza un ataque **no parreable**, aunque el jugador clave el timing del clic derecho, **no se produce parry**, sino que pasa automáticamente a ser un **Bloqueo normal** (con feedback visual/sonoro claro de que ese ataque no admitía parry).
   - **Efecto del Bloqueo (Estilo *Grounded*):**
     - El jugador **sí recibe daño**, pero reducido por un porcentaje de mitigación gradual.
     - La **barra de protección del jugador disminuye** y **le sube su propia barra de Stun**. Si el jugador abusa de mantener el bloqueo, su barra se llena y queda aturdido (guard break).

### C. Estado de Stun (*Grounded 2*)
- Tanto enemigos como jugadores tienen barra de Stun/Postura.
- Cuando la barra de un enemigo llega al 100%, entra en **Estado Stunned**:
  - Reproduce una **animación dedicada de Stun** (totalmente reconocible).
  - No puede moverse ni atacar durante `X` segundos, quedando expuesto a combos o ataques cargados.

---

## 2. Repertorio de Ataques y Mejora de Habilidades

- **Tipos de Ataque del Jugador:**
  1. **Ataques Rápidos:** Golpes ligeros encadenables.
  2. **Ataques Cargados:** Mantener ataque para liberar un golpe pesado/rompepostura.
  3. **Ataques Especiales (Skills):** Habilidades activas de clase.
  4. **Definitivas (Ultimates):** Habilidad máxima de clase (individual o combinada).
- **Mejora Evolutiva de Habilidades:**
  - Las habilidades se pueden **mejorar por niveles/tiers** usando materiales renovables de mazmorra.
  - Cada mejora puede desbloquear: **mayor daño**, **mayor tamaño/rango (AoE)**, **nuevos efectos secundarios** e incluso **nuevas animaciones visuales**.
- **Sistema de Abatido y Revivir entre Jugadores (Downed & Revive):**
  - Al llegar a 0 de vida, antes de morir definitivamente, el jugador puede quedar abatido o ser **revivido por otro jugador** compañero en combate/mazmorra.

---

## 3. Elementos Personalizados y Doble Sistema de Reacciones *(Borrador Provisional — No Definitivo)*

> [!NOTE]
> La lista de los 8 elementos y los ejemplos concretos de reacciones (tanto de Impregnación como de Sinergia entre Amigos) son **orientativos / provisionales** y se irán ajustando a medida que se diseñen las clases y habilidades en el servidor.

### A. Identidad Elemental Propia e Iconos 100% Originales
- **Iconos Propios:** Prohibido reutilizar iconos de *Genshin Impact*. Todos los emblemas elementales del servidor están diseñados y pintados desde cero por nosotros para el Resource Pack de *The Last Ascension*.
- **Propuesta de 8 Elementos (Hexágono Elemental + Dualidad Cósmica):**
  1. **Ígneo (Pyros):** Fuego volcánico / Brasas — Impregnación: *Quemado (Brasa)*.
  2. **Crio (Glacis):** Hielo cristalino / Cero absoluto — Impregnación: *Escarchado*.
  3. **Fulmen (Volt):** Relámpago / Plasma — Impregnación: *Electrificado*.
  4. **Céfiro (Aether):** Viento cortante / Corrientes — Impregnación: *Vendaval*.
  5. **Terra (Geos):** Roca pesada / Cristal sísmico — Impregnación: *Cristalizado / Pesadez*.
  6. **Sylva (Vitae):** Flora abisal / Esporas / Veneno — Impregnación: *Esporas / Enraizado*.
  7. **Umbra (Nether):** Almas / Corrupción / Sangre abisal — Impregnación: *Maldición de Alma*.
  8. **Astral (Lumen):** Luz estelar / Gravedad cósmica — Impregnación: *Marca Estelar*.

### B. Diferenciación de los 2 Tipos de Reacciones Elementales

#### Tipo 1: Reacciones de Impregnación sobre el Enemigo (1 Jugador o Cooperativo)
- **Regla clave de Impregnación:** Un enemigo **NO viene impregnado de serie** aunque sea de una temática elemental (ej. un monstruo de fuego no empieza "impregnado en fuego" hasta que alguien le aplica el estado).
- **Cómo funciona:**
  1. **Paso 1 (Impregnar):** Golpeas al enemigo con ataques de un elemento (ej. *Ígneo*) hasta aplicarle su estado alterado activo (*Quemado/Impregnado en Ígneo*).
  2. **Paso 2 (Detonar):** Mientras el enemigo está impregnado con ese primer elemento, **cualquier jugador (tú mismo en solitario o un compañero)** le aplica un segundo elemento (ej. *Céfiro*, *Sylva*, *Fulmen*).
  3. **Resultado:** Ambos estados reaccionan sobre el cuerpo del enemigo generando un **Efecto Especial de Reacción** (explosión elemental, propagación en área, reducción de defensas, rotura de postura, etc.).

#### Tipo 2: Sinergias de Ataques y Definitivas Conjuntas entre Amigos (Exclusivo Cooperativo)
- **Cómo funciona:** Ocurre cuando **dos jugadores distintos** combinan directamente sus **Habilidades Activas o Definitivas en sincronía** (cruzando ataques o activando la ventana de sinergia grupal).
- **Resultado:** No es simplemente detonar un debuff del enemigo ni sumar un +5% de daño; las dos habilidades o definitivas se fusionan en un **Nuevo Movimiento / Definitiva Conjunta** con **animación propia, daño diferente y efecto secundario/elemental único**.
