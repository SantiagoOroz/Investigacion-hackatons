# Verificación en vivo del flujo de inscripción

**Fecha de la comprobación:** 12 de septiembre de 2026
**Método:** navegación real a cada página y clic en el botón de inscripción, **sin cargar datos ni crear cuentas**. Se documenta hasta dónde llega el flujo y qué pide exactamente.

**Pregunta que responde:** ¿cuáles están *hoy* en ventana de construcción y permiten inscribirse **en este momento y en solitario**?

---

## Respuesta corta

**Cuatro, todas en Devpost, todas con inscripción instantánea y participación individual permitida:**

| Evento | Estado hoy | Días restantes | Deadline (confirmado por la propia web en GMT-3) | Cash | Participantes | ¿Solista? |
|---|---|---|---|---|---|---|
| **LexHack 2026** | 🟢 En construcción | 16 | 27 sept 2026 @ 18:00 | USD 49.560 | **208** | ✅ Sí, 1–4 |
| **Amazon — Build, Ship, Shape** | 🟢 En construcción | 42 | 23 oct 2026 @ 16:00 | USD 138.000 | 4.406 | ✅ Sí, confirmado en bases |
| **OpenCV AI Competition 2026** | 🟢 En construcción | 45 | 27 oct 2026 @ 03:45 | USD 20.250 | 1.494 | ✅ Sí |
| **Nebius x NVIDIA Global AI** | 🟢 En construcción | 48 | 30 oct 2026 @ 14:00 | USD 50.000 | 3.669 | ✅ Sí |

---

## Hallazgo transversal: Devpost muestra las fechas en GMT−3

Las cuatro páginas renderizaron el deadline directamente en **GMT−3**, es decir, la hora de Río Grande. No hay que convertir nada: **lo que muestra la web ya es hora local**.

Esto además **valida de forma independiente todas las conversiones de `05-CALENDARIO.md`**, que se habían calculado a mano desde PT/EDT:

| Evento | Conversión calculada | Lo que muestra Devpost | ¿Coincide? |
|---|---|---|---|
| LexHack 2026 | 27/09 18:00 ART | `27 sept 2026 @ 6:00pm GMT-3` | ✅ |
| Amazon | 23/10 16:00 ART | `23 oct 2026 @ 4:00pm GMT-3` | ✅ |
| OpenCV | 27/10 03:45 ART | `27 oct 2026 @ 3:45am GMT-3` | ✅ |
| Nebius x NVIDIA | 30/10 14:00 ART | `30 oct 2026 @ 2:00pm GMT-3` | ✅ |

> ⚠️ Devpost usa la zona horaria del navegador. Si se abre desde una VPN o un equipo mal configurado, **las horas mostradas cambian**. Hay un ícono de lápiz junto a `GMT-3` que permite fijar la zona manualmente.

---

## Flujo de inscripción en Devpost — qué pasa al apretar el botón

Probado en **Nebius** y en **OpenCV**; el comportamiento es idéntico en las cuatro.

1. En la página del evento, el botón azul **`Join hackathon`** está activo (arriba a la izquierda, debajo del título).
2. Al hacer clic redirige a `secure.devpost.com` con la barra verde: **"Please sign up or log in to continue."**
3. Aparece la pantalla **"Join Devpost to register for \<nombre del evento\>"**, con estas opciones:
   - Sign up with **GitHub** ← la más conveniente, ya que el proyecto se entrega con repositorio
   - Sign up with **Facebook**
   - Sign up with **Google**
   - Sign up with **LinkedIn**
   - *or sign up with email*
4. Debajo hay un **checkbox premarcado**: *"Subscribe me to Devpost's weekly newsletter"*. Si no lo querés, hay que destildarlo — viene activado por defecto.
5. Y el aviso: *"By creating an account, you agree to our Terms of Service and Privacy Policy"*.

**El proceso se detuvo en este punto a propósito: no se creó ninguna cuenta ni se cargó ningún dato.**

### Qué significa esto en la práctica
- **El único requisito para inscribirse ahora mismo es tener cuenta de Devpost.** Una sola cuenta sirve para las cuatro.
- **La inscripción es instantánea**, sin aprobación previa ni lista de espera.
- **No pide comprobante de nada al registrarse.** Los eventos *students only* (LexHack) verifican la condición de estudiante recién en la instancia de juzgamiento o de entrega del premio → conviene tener lista la constancia de alumno regular de la UTN igual.
- **No pide equipo.** Se entra como persona y, si más adelante querés, se arma o se suma equipo desde la misma plataforma.

---

## Contraste: lablab.ai **no** es inscripción instantánea

Se probó el flujo del **Lablab x AMD AI Academy Challenge**, que es el único evento de toda la investigación con la etiqueta explícita **"INDIVIDUAL PARTICIPATION ONLY"** y por lo tanto el candidato natural para una inscripción en solitario.

**Estado verificado:** 🟢 `Live`, con badge de "Submission deadline Dec 1, 4:00 PM AST", período 1 sept – 1 dic 2026, prize pool USD 5.000, 2.531 participantes.

**Pero el flujo tiene dos fricciones que Devpost no tiene:**

1. La propia página avisa: **"Sign up and wait until your enrollment is approved."** → la inscripción **no es inmediata**, queda sujeta a aprobación.
2. El botón `Sign up with AMD` dispara *"Redirecting to SSO login…"* y termina en **`login.amd.com`**: hace falta una cuenta del **AMD AI Developer Program**, no alcanza con una cuenta de lablab.

**Conclusión:** sirve, pero no cumple el "en este instante". Si te interesa, conviene crear la cuenta de AMD ya para que la aprobación no te agarre encima de la fecha.

*(Nota al pasar: la página abre un popup del AMD Developer Hackathon: ACT III con un botón "REGISTER NOW" — el evento del 12–18 de octubre que figura como secundaria en `02-SECUNDARIAS.md`. Sigue abierto.)*

---

## Corrección a la documentación previa

En `01-RECOMENDADAS.md` el formato de equipo del hackatón de Amazon figuraba como **"Ambiguo"**. Leyendo la sección 3 de las bases quedó **confirmado**:

> *"The Hackathon IS open to: Individuals who are at least the age of majority where they reside as of the time of entry ('Eligible Individuals'); Teams of Eligible Individuals ('Teams'); and Organizations…"*
>
> *"An Eligible Individual may join more than one Team or Organization and an Eligible Individual who is part of a Team or Organization may also enter the Hackathon on an individual basis."*

Es decir: **la participación individual está explícitamente contemplada**, y además una misma persona puede entrar por su cuenta *y* sumarse a un equipo en la misma edición. La ficha ya fue corregida.

También quedó confirmada la lista de exclusión: *Brasil, Quebec, Rusia, Crimea, Cuba, Irán y Corea del Norte*, más los países sancionados integralmente por la OFAC. **Argentina no figura.**

---

## Dato competitivo: cuánta gente hay anotada

Es el número más útil que devolvió esta verificación y no estaba en la investigación original:

| Evento | Participantes | Cash | Lectura |
|---|---|---|---|
| **LexHack 2026** | **208** | USD 49.560 | 🟢 **El campo más chico por lejos.** USD 1.720 al primer puesto contra ~200 personas es la mejor probabilidad por peso de la lista. |
| OpenCV AI Competition | 1.494 | USD 20.250 | 🟡 Moderado, y con barrera técnica alta (OpenCV 5 + AWS) que filtra aún más. |
| Nebius x NVIDIA | 3.669 | USD 50.000 | 🟡 Alto, pero los **20 city awards de USD 500** reparten premio fuera del podio. |
| Amazon Build, Ship, Shape | 4.406 | USD 138.000 | 🔴 El más competitivo — aunque se reparte entre **4 tracks + 2 mini challenges**, así que el pozo real por track enfrenta a ~1.100. |

---

## Recomendación operativa

**Hoy, en un solo movimiento:**

1. Crear la cuenta de **Devpost con GitHub** (una vez, sirve para todas).
2. Apretar `Join hackathon` en **LexHack 2026** — cierra en 16 días, hay 208 inscriptos y admite solista. Es la de mejor relación probabilidad/premio.
3. Apretar `Join hackathon` en **Nebius x NVIDIA** — 48 días, sin apuro, y es la de mayor retorno esperado del trimestre.

Inscribirse no obliga a entregar. En Devpost registrarse solo habilita el acceso a recursos, Discord y el formulario de entrega; **si después no presentás nada, no pasa absolutamente nada**. Así que no hay costo en anotarse en las cuatro.
