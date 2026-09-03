# Práctico Unidad 6 — Evaluación económica de proyectos
## Caso: Comité de Inversiones — ALFA S.A.

**Asignatura:** Dirección de Proyectos  
**Unidad:** 6 — Indicadores económicos, incertidumbre y decisión de inversión  
**Rol:** Comité de Inversiones  
**Presupuesto:** USD 5.000.000  
**Tasa inicial:** 10 % (pasa a 18 % en la etapa 3)

---

## Contexto

ALFA S.A. es una empresa industrial con operaciones en Latinoamérica. Tras varios años de buenos resultados, el Directorio dispone de **USD 5 millones** para invertir y tiene cinco iniciativas estratégicas sobre la mesa. No alcanza el cupo para ejecutarlas todas.

Los flujos de cada proyecto salen de la planilla del práctico. Sobre esos flujos se calcularon VAN, TIR y ROI, y después se incorporaron incertidumbre y un cambio de tasa. La pregunta no es “¿cuál proyecto es el más rentable?”, sino **qué mix cabe en el presupuesto y crea más valor** para el accionista.

**Fórmulas usadas**

- VAN: `=VNA(r; años 1–5) + inversión` (la inversión, negativa, se suma afuera de `VNA`).
- TIR: `=TIR(año 0 : año 5)` (el rango **incluye** la inversión; sin ese cambio de signo Excel devuelve `#¡NUM!`).
- ROI: `=SUMA(flujos 0 a 5) / (−inversión)`.

---

## Etapa 1 — Solo rentabilidad

Tasa de descuento **r = 10 %**. Todavía no hay información de riesgo. El criterio es: aceptar proyectos con VAN > 0 y TIR > 10 %, y, como el capital está racionado, **elegir la combinación de mayor VAN que no supere USD 5 M**.

### Indicadores por iniciativa

| Proyecto     | Inversión   | VAN          | TIR    | ROI     | Decisión preliminar |
|--------------|-------------|--------------|--------|---------|---------------------|
| ERP          | 1.500.000   | 1.448.730    | 42,3 % | 160,6 % | Candidato           |
| Planta       | 2.800.000   | 1.254.728    | 24,5 % | 96,4 %  | Candidato           |
| IA           | 1.200.000   | 899.473      | 31,6 % | 140,8 % | Candidato           |
| App          | 700.000     | 292.847      | 30,3 % | 75,7 %  | Candidato           |
| Data Center  | 1.800.000   | 232.629      | 14,8 % | 50,0 %  | Candidato           |

Los cinco son viables por separado. El cuello de botella no es la viabilidad individual: es el capital.

### Portafolios que caben en USD 5 M

| Portafolio            | Inversión | Sobra     | VAN del mix | vs. ganador |
|-----------------------|-----------|-----------|-------------|-------------|
| **ERP + Planta + App** | 5.000.000 | 0         | **2.996.305** | —         |
| ERP + Planta          | 4.300.000 | 700.000   | 2.703.458   | −292.847    |
| ERP + IA + App        | 3.400.000 | 1.600.000 | 2.641.050   | −355.255    |
| ERP + DC + IA         | 4.500.000 | 500.000   | 2.580.832   | −415.473    |
| Planta + IA + App     | 4.700.000 | 300.000   | 2.447.048   | −549.257    |

ERP + Planta dejan exactamente USD 700.000, que es la App. Esa terna usa el cupo completo y maximiza el VAN.

### ¿Qué proyectos recomendarían únicamente considerando la rentabilidad?

**ERP + Planta + App.**

No se elige “el de mayor TIR”. El ranking individual por TIR/ROI sería ERP (42,3 %), IA (31,6 %) y App (30,3 %). Ese mix (ERP + IA + App) invierte solo USD 3,4 M y deja **USD 355 mil de VAN** sobre la mesa.

Por qué no entran los otros dos:

- **IA.** VAN y TIR sólidos, pero ERP + Planta ya suman 4,3 M y el residual no alcanza para 1,2 M. Meter la IA obliga a sacar la Planta (ERP + Planta + IA = 5,5 M, fuera de cupo) y el VAN del portafolio cae de 2,996 M a 2,641 M.
- **Data Center.** Es el de menor VAN (USD 232.629) y su TIR apenas supera el 10 % por 4,8 puntos. Cada dólar rinde poco. Sustituirlo por Planta + App junto al ERP crea mucho más valor.

Esta recomendación es **solo rentabilidad**. Todavía no se miró la incertidumbre.

---

## Etapa 2 — Incertidumbre y valor esperado

El Directorio entrega antecedentes cualitativos, un análisis de sensibilidad y escenarios para ERP e IA.

| Proyecto    | Perfil                                              | En el mix de etapa 1 | Qué aporta esta etapa                                      |
|-------------|-----------------------------------------------------|----------------------|------------------------------------------------------------|
| ERP         | Reduce riesgos. Poca incertidumbre. Beneficios estables. | Aprobado            | Se refuerza: piso alto y baja sensibilidad                 |
| Planta      | Gran VAN, pero depende del mercado.                 | Aprobado             | Se mantiene por valor; exige seguimiento de demanda        |
| Data Center | Beneficio moderado. Muy robusto.                    | Fuera                | Sigue fuera: robustez cara (VAN 233 mil)                   |
| IA          | Muy rentable. Muy riesgosa.                         | Fuera                | Se confirma el rechazo: cola negativa y sensibilidad extrema |
| App         | Recuperación muy rápida. Puede quedar obsoleta.     | Aprobado             | Se mantiene: ticket chico y payback corto mitigan la obsolescencia |

### Sensibilidad

| Proyecto | Shock         | Efecto sobre el VAN      | Lectura                                      |
|----------|---------------|--------------------------|----------------------------------------------|
| ERP      | Costos +10 %  | El VAN cae apenas 3 %    | Robusto: el caso de negocio sigue en pie     |
| IA       | Ventas −10 %  | El VAN desaparece        | Un desvío menor anula el proyecto            |

### Valor esperado (p = 25 % / 50 % / 25 %)

$$VE = 0{,}25 \times VAN_{opt} + 0{,}50 \times VAN_{base} + 0{,}25 \times VAN_{pes}$$

| Proyecto | Optimista | Base    | Pesimista | **VE**      |
|----------|-----------|---------|-----------|-------------|
| ERP      | 1.600.000 | 1.450.000 | 1.200.000 | **1.425.000** |
| IA       | 2.800.000 | 900.000   | −600.000  | **1.000.000** |

El ERP nunca cruza cero. La IA gana en el escenario optimista y **destruye USD 600 mil** en el pesimista.

Para Planta, App y Data Center el enunciado no trae escenarios; se usa el VAN de etapa 1.

| Portafolio                 | Inversión | VE / VAN mixto | Cola de riesgo                                      |
|----------------------------|-----------|----------------|-----------------------------------------------------|
| **ERP + Planta + App**     | 5,00 M    | **2.972.575**  | Planta–mercado; App–obsolescencia. ERP sin cola negativa. |
| ERP + IA + App             | 3,40 M    | 2.717.847      | IA pesimista −600 mil. VE unos USD 255 mil más abajo.    |
| ERP + DC + App (máx. robustez) | 4,00 M | ~1,95 M        | Muy estable, sacrifica ~USD 1,0 M de valor.         |

### ¿Cambiarían su recomendación?

**No. El mix no cambia: sigue siendo ERP + Planta + App.** Cambia el argumento frente al Directorio.

- El ERP pasa de “mejor VAN unitario” a “mejor VAN y mejor riesgo”.
- La IA, que ya no cabía con ERP + Planta, **tampoco se cuela ahora por rentabilidad ajustada por riesgo**. Sustituir Planta por IA deja el VE del portafolio unos USD 255 mil más abajo y agrega cola negativa.
- La Planta se mantiene por valor, con **seguimiento de mercado**.
- La App se mantiene: ticket de USD 700 mil y recuperación rápida, así que la obsolescencia duele poco.
- El Data Center sigue fuera: muy robusto, poco valor. Solo entraría si el Directorio vetara la Planta.

---

## Etapa 3 — Revisión por suba de tasa

El Banco Central aumenta la tasa de interés del **10 % al 18 %**. El VAN se recalcula. La TIR **no cambia**: cambia el listón de corte (ahora TIR > 18 %).

### VAN a 10 % vs VAN a 18 %

| Proyecto    | VAN 10 %  | VAN 18 %   | Caída del VAN | TIR vs 18 % | Decisión          |
|-------------|-----------|------------|---------------|-------------|-------------------|
| ERP         | 1.448.730 | 922.520    | 36 %          | Por encima  | Se mantiene       |
| Planta      | 1.254.728 | 476.304    | **62 %**      | Por encima  | Deja de forzar    |
| IA          | 899.473   | 475.534    | 47 %          | Por encima  | Entra al mix      |
| App         | 292.847   | 154.842    | 47 %          | Por encima  | Se mantiene       |
| Data Center | 232.629   | **−131.789** | Cruza a negativo | **Por debajo** | **Rechazar**  |

La Planta cobra tarde (800 → 1.400 mil). A 18 % esos flujos lejanos se evaporan. El Data Center queda entre 10 % y 18 %: viable en etapa 1, inviable ahora.

### Portafolios factibles a 18 %

| Portafolio             | Inversión | Sobra     | VAN a 18 % | Lectura                                                      |
|------------------------|-----------|-----------|------------|--------------------------------------------------------------|
| ERP + Planta + App     | 5,00 M    | 0         | 1.553.667  | Máximo VAN por USD 770. Inmoviliza todo el cupo en la Planta. |
| **ERP + IA + App**     | **3,40 M** | **1,60 M** | **1.552.897** | Mismo valor, menos capital, más colchón de TIR.           |
| ERP + Planta           | 4,30 M    | 0,70 M    | 1.398.825  | Dejar afuera la App destruye VAN sin aliviar el riesgo Planta. |
| Planta + IA + App      | 4,70 M    | 0,30 M    | 1.106.681  | Sacar el ERP pierde el ancla más estable.                    |

### Revisión de la recomendación

**Sí cambia la recomendación.** El mix pasa a **ERP + IA + App**. El Data Center queda fuera.

1. **Data Center se cae.** TIR 14,8 %: pasaba el listón del 10 % y no pasa el del 18 %. VAN −USD 131.789. Robustez operativa no sustituye rentabilidad.
2. **ERP y App se quedan.** Siguen con VAN positivo y TIR holgada (42,3 % y 30,3 %). La App, de recuperación rápida, resiste mejor la tasa que los proyectos de flujos tardíos.
3. **Planta vs IA: empate de VAN, no de capital.** La diferencia es **USD 770**. La IA deja el mismo valor con **USD 1,6 M** menos inmovilizados (IR a 18 %: IA 1,40 vs Planta 1,17). A esta tasa no tiene sentido forzar la Planta.

El riesgo de etapa 2 de la IA no desaparece (ventas −10 % anulan su VAN). Entra porque ya no se elige una lotería contra un VAN claramente mayor: se elige el mismo valor con menos caja y más colchón de TIR (31,6 % vs 24,5 %).

**Plan B** si el Directorio veta la IA: ERP + Planta + App sigue siendo aceptable (TIR de los tres > 18 % y VAN apenas USD 770 mayor). El costo es inmovilizar el cupo entero en el proyecto más sensible a la tasa y al mercado.

---

## Etapa 4 — Recomendación al Directorio

**ALFA S.A. — Comité de Inversiones**  
Asunto: Aprobación de iniciativas estratégicas — presupuesto USD 5.000.000  
Tasa de corte vigente: **18 %** (tras la decisión del Banco Central)

### Proyecto(s) recomendados

**ERP + IA + App.**  
Inversión: USD 3.400.000. Liquidez remanente: USD 1.600.000.  
VAN del portafolio a 18 %: **USD 1.552.897**.

Quedan **fuera** el Data Center (VAN negativo a la nueva tasa) y la Planta (no se fuerza: mismo valor que la IA con USD 1,6 M más de capital inmovilizado).

### Indicadores considerados

- **VAN del portafolio** a la tasa vigente (criterio de maximización de valor con capital racionado).
- **TIR** contra el listón de corte (10 % en etapas 1–2; 18 % en etapas 3–4). Explica el rechazo del Data Center.
- **ROI / índice de rentabilidad** como apoyo cuando dos mixes empatan en VAN y compiten por caja.
- **Valor esperado y sensibilidad** (etapa 2): VE(ERP) USD 1.425.000 vs VE(IA) USD 1.000.000; costos +10 % apenas mueven al ERP; ventas −10 % anulan a la IA.

### Principales riesgos

- **IA — demanda.** Un −10 % de ventas hace desaparecer su VAN. El escenario pesimista destruye USD 600 mil. Se mitiga no concentrando USD 2,8 M en un solo activo de mercado y dejando USD 1,6 M líquidos.
- **App — obsolescencia.** Puede quedar desactualizada. El ticket es USD 700 mil y la recuperación es rápida: el daño está acotado.
- **Tasa.** Una nueva suba por encima de ~24 % pondría en duda a la Planta (plan B) y, más allá de ~30 %, a App e IA. El ERP tiene el colchón más amplio (TIR 42,3 %).
- **Riesgo que ya no se corre:** el Data Center a 18 % destruye valor. No se aprueba “por robustez”.

### Justificación

El Comité recorrió tres filtros. Con **solo rentabilidad** (r = 10 %) el mix de mayor VAN era ERP + Planta + App (USD 2.996.305). Con **incertidumbre**, ese mix se sostenía: el ERP es el ancla estable y la IA no compensaba, en valor esperado, el riesgo de sustituir a la Planta. Con la **tasa en 18 %** el ranking de valor se aplana: Planta e IA aportan casi el mismo VAN (~USD 476 mil), pero la Planta exige USD 1,6 M extra y cobra tarde. El Data Center queda por debajo del nuevo costo de capital.

La recomendación vigente es, por tanto, **ERP + IA + App**: ancla de bajo riesgo (ERP), ticket chico de recupero rápido (App) y el proyecto de mayor rendimiento por dólar que todavía crea valor a 18 % (IA), sin agotar el cupo. Si el Directorio no acepta el perfil de la IA, el plan B es volver a ERP + Planta + App.

---

**Firma**  
Comité de Inversiones  
ALFA S.A.

---

## Preguntas de discusión

### ¿Qué indicador usaron primero?

El **VAN**, junto con la TIR como filtro de corte.

La primera pasada fue mecánica: calcular VAN, TIR y ROI de cada iniciativa a r = 10 %. El VAN respondió “cuánto valor crea, en dólares de hoy”. La TIR respondió “¿supera el costo de capital?”. El ROI sirvió de lectura auxiliar de rentabilidad sobre la inversión, pero no para racionar el cupo.

Con los cinco proyectos viables, el indicador que **decidió el mix** ya en etapa 1 no fue la TIR más alta, sino el **VAN del portafolio** sujeto a USD 5 M.

### ¿Cuál terminó siendo el más importante?

El **VAN recalculado a la tasa vigente**.

Es el único que se movió cuando cambió el contexto y el que, al final, cambió la decisión. La TIR fue decisiva para **rechazar** el Data Center (no se movió; se movió el listón). El valor esperado y la sensibilidad fueron decisivos para **no enamorarse de la IA** en etapa 2, pero no alcanzaron para cambiar el mix. Cuando la tasa subió, el VAN de la Planta se desplomó (−62 %) y empató con el de la IA: ahí el VAN —leído junto con el capital inmovilizado— mandó más que cualquier ranking de TIR o ROI.

En una frase: se empezó por VAN + TIR; se terminó gobernando por **VAN del portafolio al nuevo costo de capital**.

### ¿Cambió la decisión cuando aumentó la tasa?

**Sí.**

| Momento              | Mix recomendado      | Inversión | Qué quedó fuera      |
|----------------------|----------------------|-----------|----------------------|
| Etapas 1 y 2 (10 %)  | ERP + Planta + App   | 5,00 M    | Data Center e IA     |
| Etapas 3 y 4 (18 %)  | **ERP + IA + App**   | **3,40 M** | Data Center y Planta |

Tres cosas concretas:

1. El Data Center pasa de “viable, pero poco valioso” a **inviable** (VAN negativo).
2. La Planta deja de ser el segundo pilar: pierde el 62 % de su VAN y ya no justifica inmovilizar USD 2,8 M.
3. La IA, descartada dos veces (por cupo y por riesgo), **entra** no porque se haya vuelto más segura, sino porque a 18 % crea el mismo valor que la Planta con menos caja.

El ERP y la App son la continuidad: sobreviven las tres etapas.
