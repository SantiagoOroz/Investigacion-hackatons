# Fuentes y monitoreo continuo

Cómo se hizo esta investigación y cómo repetirla sin ayuda dentro de un mes.

---

## 1. La consulta que hace el 80 % del trabajo: la API de Devpost

Devpost tiene una **API pública sin autenticación** que devuelve mucho más y mejor que la web. La página `devpost.com/hackathons` carga por JavaScript y es difícil de leer automáticamente; la API no.

```
https://devpost.com/api/hackathons?challenge_type[]=online&status[]=open&status[]=upcoming&order_by=deadline&page=1
```

### Parámetros útiles

| Parámetro | Valores | Para qué |
|---|---|---|
| `challenge_type[]` | `online`, `in-person` | Filtra modalidad. **Ojo:** los eventos híbridos suelen etiquetarse como `in-person` aunque tengan fase online → conviene correr la consulta también **sin** este filtro. |
| `status[]` | `open`, `upcoming`, `ended` | Se pueden combinar repitiendo el parámetro. |
| `order_by` | `deadline`, `prize-amount`, `recently-added` | `prize-amount` para encontrar los grandes; `deadline` para no perder los que cierran pronto. |
| `page` | 1, 2, 3… | Devuelve 9 resultados por página. Paginar hasta que la respuesta venga vacía. |

### Campos que devuelve cada evento
`title`, `url`, `prize_amount`, `submission_period_dates`, `open_state`, `organization_name`, `themes`, `registrations_count`, `time_left_to_submission`.

### ⚠️ Tres trampas de esta API
1. **`prize_amount` es el número que declara el organizador, no el efectivo.** Ver la tabla de premios inflados en el `README.md`: ForgeHacks anuncia USD 126.361 y reparte USD 175 en cash. **Siempre abrir la página `/rules` del evento.**
2. **Las fechas de `submission_period_dates` a veces contradicen a las bases.** Caso comprobado: *Global Innovation Build Challenge V2* figura con cierre el 1/10 en la API y el 21/09 en sus propias bases.
3. **No lista todo.** Varios eventos corporativos grandes (algunos de Google Cloud) no aparecen en el listado público. Hay que complementar con las newsletters de los sponsors.

### Consultas recomendadas para revisar una vez por semana
```
# Lo que más paga, abierto ahora
https://devpost.com/api/hackathons?challenge_type[]=online&status[]=open&order_by=prize-amount&page=1

# Lo que viene, por orden de cierre
https://devpost.com/api/hackathons?challenge_type[]=online&status[]=upcoming&order_by=deadline&page=1

# Sin filtro de modalidad, para cazar híbridos con fase online
https://devpost.com/api/hackathons?status[]=open&status[]=upcoming&order_by=prize-amount&page=1
```

---

## 2. Plataformas, ordenadas por utilidad para este perfil

| # | Plataforma | Qué aporta | Frecuencia de revisión |
|---|---|---|---|
| 1 | **Devpost** — https://devpost.com/hackathons | El grueso del circuito remoto. Bases legales completas en `/rules`, con lista de países excluidos. | Semanal |
| 2 | **lablab.ai** — https://lablab.ai/ai-hackathons | Hackatones de IA patrocinadas por AMD, IBM, Vultr, AssemblyAI, NVIDIA. Globales y online. **Contra:** no publica bases legales completas. | Semanal |
| 3 | **Luma** — https://luma.com | Donde viven los eventos que no usan Devpost (Hack-Nation, comunidades de IA). Buscar por tema y filtrar por "online". | Quincenal |
| 4 | **Kaggle** — https://www.kaggle.com/competitions | Competencias de ML con premios grandes y 100 % remotas. Distinto formato: semanas o meses, no fines de semana. | Mensual |
| 5 | **ETHGlobal** — https://ethglobal.com/events | Solo si interesa Web3. Sus eventos online (`ETHOnline`, `HackMoney`) pagan bien; el resto del calendario es presencial. | Mensual |
| 6 | **MLH / Global Hack Week** — https://ghw.mlh.com/events | Gratis, mensual, global, sin filtros. Sirve para práctica y para armar equipo, no para premios. | Mensual |
| 7 | **NASA Space Apps** — https://www.spaceappschallenge.org | Una vez al año (octubre/noviembre). Máximo prestigio, sin dinero. | Anual |
| 8 | **HackerEarth** — https://www.hackerearth.com/challenges/hackathon/ | Mucho contenido, pero **fuertemente orientado a India**. Aplicar la Regla de Oro con rigor. | Mensual |
| 9 | **HackerNoon** — https://hackernoon.com | Corre hackatones propias por rondas (Decentralize AI). Entrega vía artículo publicado. | Trimestral |
| 10 | **hack0.dev** — https://hack0.dev | Directorio de eventos tech en Latinoamérica. Casi todo presencial, pero es la mejor fuente regional. | Mensual |
| 11 | **DoraHacks** — https://dorahacks.io/hackathon | Web3 y IA, global. **Nota técnica:** su web bloquea la lectura automatizada; hay que abrirla en el navegador. | Mensual |
| 12 | **Zindi** — https://zindi.world/competitions | Competencias de ML. Migró de `zindi.africa` a `zindi.world`. **Verificar si cada desafío está restringido a residentes de África.** | Mensual |

---

## 3. Canales directos de sponsors (donde aparecen los premios grandes primero)

Los eventos de más dotación suelen anunciarse en el blog del sponsor **antes** de aparecer en Devpost:

- **Google Cloud** — https://cloud.google.com/blog/topics/developers-practitioners y https://developers.google.com/events
  *(Pools de USD 50.000 a USD 180.000. Argentina elegible confirmada en All Things Agentic.)*
- **AWS / Amazon Developer** — el hackatón *Build, Ship, Shape* se anunció por los canales de Amazon Developer.
- **NVIDIA Developer Program** y **Nebius**.
- **AMD AI Developer Program (ADP)** — registro obligatorio para sus hackatones.
- **IBM TechXchange** — https://www.ibm.com/community/techxchange-hackathons/
- **DevNetwork** — https://www.developerweek.com/hackathon/ · https://apiworld.co/hackathon/ · https://aidevsummit.co/hackathon/
- **ARC Prize Foundation** — https://arcprize.org/competitions

---

## 4. Checklist de verificación antes de invertir tiempo

Aplicar esto a **cada** evento antes de escribir una línea de código. Está ordenado de más a menos descartante: si falla el paso 1, no hace falta seguir.

1. **¿Argentina está excluida?** Abrir `/rules` y buscar la sección *Eligibility*. Listas típicas: Brasil, Quebec, Italia, Rusia, Crimea, Cuba, Irán, Siria, Sudán, Bielorrusia, Corea del Norte + OFAC.
   → Argentina **nunca apareció** en ninguna lista revisada. Si aparece, se descarta sin más.
2. **¿Exige matrícula en una universidad específica o residencia en una región?**
   → Es la Regla de Oro. Atención con eventos organizados por universidades de EE. UU.: la mayoría **no** restringe a sus propios alumnos (lo hace HackTitan/IWU y Rice), pero hay que confirmarlo caso por caso.
3. **¿Qué parte del premio es dinero de verdad?** Buscar frases como *"non-cash benefits"*, *"cannot be exchanged or redeemed for cash"*, *"estimated fair-market equivalent"*.
   → Si el desglose no está publicado, asumir que es mayoritariamente en créditos.
4. **¿Exige ser estudiante?** *"Students only"* aparece en cerca de la mitad de los eventos grandes de Devpost. Ser estudiante de la UTN **habilita**, pero puede pedirse comprobante.
5. **¿Exige hardware físico?** Tracks como *Physical AI* (Nebius), *Bee* o *Ring* (Amazon) requieren dispositivos. Desde Tierra del Fuego, importarlos no es viable en plazo ni en costo.
6. **¿Qué dice sobre IA?** Buscar *"AI tools"*. Tres variantes encontradas: fomentada (UnivaBio, LexHack), permitida con declaración obligatoria (TLN, OpenCV) o restringida en la evaluación (ARC Prize).
7. **¿Cuánto tiempo queda realmente?** Convertir el deadline a ART. Los de EE. UU. **regalan** entre 1 y 5 horas según la zona y la época del año.
8. **¿Cómo se cobra el premio?** Verificar si hay transferencia internacional, PayPal o gift cards. Es el punto menos documentado de todo el circuito y conviene preguntarlo por Discord **antes** de competir.

---

## 5. Documentación a tener lista de antemano

Preparar esto una sola vez ahorra días de fricción cuando aparece una oportunidad con deadline corto:

- [ ] **Constancia de alumno regular de la UTN** en PDF, con traducción al inglés. La piden las hackatones *students only* (TLN, LexHack, UnivaBio, HackTitan, ForgeHacks, GatewayHacks).
- [ ] **Perfil de Devpost** completo, con foto, biografía y proyectos anteriores cargados.
- [ ] **GitHub** ordenado: los jurados lo miran. README claro en cada repo.
- [ ] **Plantilla de video de demo de 3 minutos** — casi todas piden lo mismo: problema, demo funcionando, arquitectura, stack.
- [ ] **Cuentas creadas por adelantado** en los proveedores que exigen los eventos: Nebius AI Cloud, AWS (capa gratuita + créditos de estudiante), Google Cloud, AMD ADP.
- [ ] **Datos de cobro internacional** resueltos (cuenta en dólares, PayPal o equivalente).
- [ ] **Discord** instalado: es el canal real de soporte de casi todos los eventos, y donde se contestan las dudas de elegibilidad.

---

## 6. Rutina de monitoreo sugerida

**Cada lunes (15 minutos):**
1. Correr las tres consultas a la API de Devpost de la sección 1.
2. Abrir https://lablab.ai/ai-hackathons y mirar la sección *Upcoming*.
3. Anotar cualquier evento con pool superior a USD 10.000 y cierre a más de 3 semanas.

**Cada primer lunes de mes (45 minutos):**
4. Revisar el blog de desarrolladores de Google Cloud y los canales de sponsors de la sección 3.
5. Revisar el estado de los eventos de `03-SIN-FECHA-DEFINIDA.md`, en particular **The Rise of AI Agents** (USD 60.000+) y las hackatones de **Google Cloud**.
6. Actualizar `05-CALENDARIO.md` con lo nuevo.

---

## 7. Fuentes consultadas en esta investigación

### Páginas de eventos verificadas de forma directa
- https://nebiusglobalaihackathon.devpost.com/rules
- https://amazonappdev2026.devpost.com/ y `/rules`
- https://opencv26.devpost.com/rules
- https://lexhack-2026.devpost.com/
- https://univabio.devpost.com/
- https://tln-cybersecurity-challenge.devpost.com/
- https://gatewayhacks-2026.devpost.com/
- https://gibc-v2.devpost.com/
- https://forgehacks-2026.devpost.com/
- https://launchhacks-v.devpost.com/
- https://galuxium-nexus-v2-29411.devpost.com/
- https://hacktitan.devpost.com/
- https://neighborhood-hacks-2026.devpost.com/
- https://revenuecat-shipaton-2026.devpost.com/rules
- https://allthingsagentichackathon.devpost.com/rules
- https://xprize.devpost.com/
- https://run.devpost.com/
- https://developerweek-2027-hackathon.devpost.com/
- https://api-cloud-ai-hackathon-2026.devpost.com/
- https://eazo-ai-hackathon.devpost.com/ → **HTTP 410 Gone**

### Otras plataformas
- https://lablab.ai/ai-hackathons (+ fichas de AI GENESIS, AMD ACT III, IBM Bob 2.0, Vultr, AssemblyAI, AMD AI Academy)
- https://luma.com/z3za7zow (Hack-Nation 7.ª Global AI Hackathon)
- https://hack-nation.ai/hackathon
- https://ethglobal.com/events
- https://ghw.mlh.com/ y https://www.mlh.com/events
- https://arcprize.org/competitions/2026 y https://www.kaggle.com/competitions/arc-prize-2026-paper-track
- https://www.spaceappschallenge.org/
- https://decentralizeai.tech/
- https://aihackathon.usaii.org/
- https://hackathon.supabase.com/supabase-select-2026-hackathon
- https://apiworld.co/hackathon/
- https://pytorch.org/event/openenv-ai-hackathon/
- https://cloud.google.com/resources/agents-for-impact-2026
- https://hack0.dev/
- https://zindi.world/competitions
- https://www.hackerearth.com/challenges/hackathon/
- https://hackatonacindar.com/

### Artículos y agregadores usados como pista (no como fuente primaria)
- https://www.thechangingbooth.com/post/the-ultimate-guide-to-the-best-free-hackathons-in-2026
- https://hackernoon.com/5-hackathons-you-can-enter-right-now
- https://mansimore3.substack.com/p/all-upcoming-google-cloud-hackathons
- https://www.forbesargentina.com/innovacion/transform-the-future-como-hackathon-buenos-aires-repartira-us-50000-n60484

> ⚠️ **Todo lo que salió de agregadores fue verificado contra la página oficial del organizador.** Es imprescindible: varios blogs de "oportunidades" seguían promocionando el EAZO Global Hackathon (USD 300.000) cuando su página ya devolvía un 410 Gone, y otros confundían las fechas de la edición 2025 del Cloud Run Hackathon con una supuesta edición 2026 que no se pudo confirmar.
