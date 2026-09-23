# Investigación: Hackatones remotas a futuro

**Fecha de la investigación:** 11 de septiembre de 2026
**Perfil analizado:** 20 años, argentino, residente en Río Grande (Tierra del Fuego, UTC−3), estudiante de Tecnicatura Universitaria en Programación (UTN), español e inglés.

---

## Índice de documentos

| Archivo | Contenido |
|---|---|
| [01-RECOMENDADAS.md](01-RECOMENDADAS.md) | Fichas completas de las 9 hackatones que cumplen **los 4 requisitos obligatorios** y tienen mejor relación esfuerzo/retorno. |
| [02-SECUNDARIAS.md](02-SECUNDARIAS.md) | Opciones válidas pero con reservas (premio mayormente en especie, ventana muy corta, nicho exigente o hardware requerido). |
| [03-SIN-FECHA-DEFINIDA.md](03-SIN-FECHA-DEFINIDA.md) | Eventos recurrentes y confirmados **sin fecha publicada todavía**. Apartado separado, como se pidió. |
| [04-DESCARTADAS.md](04-DESCARTADAS.md) | Qué se descartó y por qué (aplicación de la Regla de Oro). |
| [05-CALENDARIO.md](05-CALENDARIO.md) | Línea de tiempo cronológica con todos los deadlines convertidos a **hora argentina (ART)**. |
| [06-FUENTES-Y-MONITOREO.md](06-FUENTES-Y-MONITOREO.md) | Plataformas, consultas y automatizaciones para seguir encontrando eventos nuevos. |
| [07-VERIFICACION-EN-VIVO.md](07-VERIFICACION-EN-VIVO.md) | **Comprobación real del flujo de inscripción (12/09/2026):** cuáles están abiertas *ahora*, cuántos inscriptos tiene cada una y qué pide exactamente el botón de registro. |

---

## Resumen ejecutivo

Se revisaron **~90 eventos** en 11 plataformas (Devpost, lablab.ai, Kaggle/ARC Prize, ETHGlobal, MLH, HackerEarth, DoraHacks, Zindi, NASA Space Apps, Luma y sitios propios de sponsors). Tras aplicar los filtros quedaron:

- **9 recomendadas** (cumplen todo: remoto + fecha definida + premio real + IA permitida + Argentina elegible).
- **15 secundarias** (cumplen pero con una advertencia relevante documentada).
- **8 sin fecha definida** (recurrentes, hay que vigilarlas).
- **Más de 40 descartadas** de forma explícita: 7 por la Regla de Oro (restricción geográfica o de matrícula), 8 por ser 100 % presenciales, 2 por exigir nivel secundario, 12 por haber cerrado, 6 por ventana insuficiente, 1 retirada de la plataforma, y el resto por premio nulo o simbólico.

### Las 3 que conviene atacar sí o sí

| # | Evento | Deadline (ART) | Premio real | Por qué |
|---|---|---|---|---|
| 1 | **Nebius x NVIDIA Global AI Hackathon** | 30/10/2026 14:00 | USD 20.000 / 10.000 / 6.000 + hardware NVIDIA Jetson + **20 premios de ciudad de USD 500** | Ventana de 7 semanas, no exige ser estudiante, admite solista, elegibilidad global explícita con Argentina incluida, y la categoría *city awards* premia diversidad geográfica: Río Grande juega a favor, no en contra. |
| 2 | **Build, Ship, Shape: Amazon Developer Hackathon** | 23/10/2026 16:00 | Hasta USD 25.000 cash por track + créditos AWS (USD 138.000 en total) | Premio en efectivo más alto por track accesible en remoto. Los tracks **Alexa+** y **Fire TV** no requieren hardware físico (MCP servers self-hosted / emulador). |
| 3 | **TLN Hackathon 2026** | 19–20/09/2026 | Grand Prize USD 8.752 + **"Best Beginner Project" USD 4.060** + USD 500 en créditos para los 192 participantes | Única con una categoría de principiante de casi USD 4.000, y **todos** los participantes se llevan créditos. Riesgo bajísimo, ventana de 8 días. |

---

## Criterios de filtrado aplicados

### Requisitos obligatorios (si falla uno, el evento no entra en `01-RECOMENDADAS`)

1. **Modalidad 100 % remota.** Se aceptan híbridos **solo** si la fase de construcción y la entrega se pueden hacer íntegramente online y la presencialidad es opcional y no condiciona el premio principal. Se documenta explícitamente en cada ficha.
2. **Fecha futura y definida.** Posterior al 11/09/2026, con inscripción abierta o con fecha de apertura confirmada. Sin fecha → va a `03-SIN-FECHA-DEFINIDA.md`.
3. **Incentivo real.** Dinero, hardware, créditos cloud, licencias o aceleración. Se distingue **cash real vs. valor declarado**: muchos eventos anuncian pools de seis cifras que en realidad son 95 % créditos de sponsors.
4. **IA permitida.** Sin prohibición estricta de asistentes de código ni de modelos generativos.

### Regla de Oro (exclusión automática)

Se descartó todo evento que exigiera:
- Matrícula en universidades específicas de otros países.
- Residencia en una región no aplicable (EMEA, India, África subsahariana, EE. UU., etc.).
- Que excluyera a Argentina de forma explícita o implícita.
- Idiomas distintos del español o el inglés.

**Hallazgo clave del análisis geográfico:** Argentina **no aparece en ninguna lista de exclusión estándar** de las plataformas revisadas. Las listas típicas son *Brasil, Quebec, Italia, Rusia, Crimea, Cuba, Irán, Siria, Sudán, Bielorrusia, Corea del Norte* + países sancionados por la OFAC. Argentina queda siempre del lado elegible. Es una ventaja competitiva concreta frente a, por ejemplo, un participante brasileño, que queda fuera de Nebius, Amazon y RevenueCat de un plumazo.

---

## Cuatro ventajas del perfil que conviene explotar

1. **Mayoría de edad cumplida (20 años).** La barrera más frecuente en Devpost es *"above legal age of majority in country of residence"*. En Argentina son 18 años → siempre se cumple. Elimina el consentimiento parental y habilita el cobro directo de premios.
2. **Estudiante universitario activo.** Cerca de la mitad de las hackatones de Devpost con premios grandes son **"students only"**. Ser estudiante de la UTN es un requisito habilitante, no un obstáculo — pero hay que poder acreditarlo (constancia de alumno regular en PDF, idealmente traducida al inglés).
3. **Inglés.** Todos los eventos de alto valor listados operan en inglés. No hay ninguno que requiera un tercer idioma.
4. **Huso horario UTC−3.** Río Grande está 1 hora *adelante* de la costa este de EE. UU. (EDT) y 4 horas adelante de la costa oeste (PDT). Un deadline "11:45 PM EDT" cae a las **00:45 ART del día siguiente**, y uno de "5:00 PM PT" a las **21:00 ART** — siempre se gana tiempo respecto de un participante estadounidense.

> ⚠️ **Ojo con esto:** Argentina y Tierra del Fuego usan UTC−3 todo el año, sin horario de verano. EE. UU. **sí** cambia el 1 de noviembre de 2026: a partir de esa fecha la diferencia sube a +2 h (EST) y +5 h (PST). Todos los deadlines de noviembre en adelante de este informe ya están convertidos con la diferencia correcta.

---

## Advertencia sobre los "premios inflados"

Es el hallazgo más importante de esta investigación y aplica a casi todo Devpost:

| Evento | Pool anunciado | Cash real estimado | Lectura |
|---|---|---|---|
| GatewayHacks 2026 | USD 1.007.085 | ~USD 13.000 | 98,7 % son créditos y dominios |
| Global Innovation Build Challenge V2 | USD 156.525 | ~USD 2.075 | 98,7 % son créditos |
| ForgeHacks Online 2026 | USD 126.361 | USD 175 (ciento setenta y cinco) | 99,9 % son créditos |
| TLN Hackathon 2026 | USD 126.929 | ~USD 29.400 | 77 % créditos, pero el cash es alto y bien repartido |
| Galuxium Nexus V2 | USD 14.944 | **USD 0** | Las bases dicen textualmente que *no se entrega dinero físico* |
| Nebius x NVIDIA | USD 50.000 | ~USD 46.000 | Casi todo cash + hardware |
| Amazon Developer Hackathon | USD 138.000 | ~USD 118.000 | Casi todo cash + créditos AWS |

**Conclusión:** ordenar por `prize_amount` en Devpost es engañoso. Las fichas de este informe separan siempre *cash* de *especie*.

---

## Metodología

- Consultas directas a la API pública de Devpost (`devpost.com/api/hackathons`) filtrando por `challenge_type=online` y `status=open|upcoming`, ordenando tanto por `deadline` como por `prize-amount`, y paginando hasta agotar resultados. La consulta se repitió **sin** el filtro de modalidad para no perder eventos híbridos con fase online.
- Lectura directa de las páginas `/rules` de cada candidato serio, no solo de la descripción de portada: las listas de países excluidos y las fechas reales viven ahí.
- Verificación cruzada contra las webs de los organizadores cuando la ficha de Devpost contradecía a las bases (ver el caso de *Global Innovation Build Challenge V2* en `02-SECUNDARIAS.md`).
- Barrido de plataformas no-Devpost: lablab.ai, ETHGlobal, MLH/Global Hack Week, Kaggle + ARC Prize, HackerEarth, DoraHacks, Zindi, NASA Space Apps, Luma, HackerNoon y hack0.dev (directorio LatAm).

### Límites conocidos de esta investigación

- Las páginas de lablab.ai no publican bases legales completas: **no se pudo confirmar la lista de países excluidos** de IBM Bob 2.0, AMD ACT III, Vultr Agent Rush ni AssemblyAI. Están marcadas como "elegibilidad probable, a confirmar".
- Varios montos figuran como "TBA" y se publican recién en el kickoff (TechEx Amsterdam, Vultr, AI GENESIS).
- Devpost no lista públicamente algunos eventos patrocinados grandes, así que conviene complementar con las newsletters de los sponsors (ver `06-FUENTES-Y-MONITOREO.md`).
- Toda la información fue capturada el 11/09/2026. Las bases pueden cambiar: **verificar fechas y reglas en el sitio oficial antes de inscribirse.**
