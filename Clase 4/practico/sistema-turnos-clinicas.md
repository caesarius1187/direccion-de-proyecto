# Práctico Unidad 4 — Estimación de proyectos
## Caso: Sistema de turnos online para cadena de clínicas

**Asignatura:** Dirección de Proyectos  
**Unidad:** 4 — Estimación de proyectos  
**Título del caso:** *“El proyecto que cambia mientras lo descubrimos”*  
**Rol:** consultora encargada del desarrollo

---

## 0. Lectura del enunciado y del descubrimiento

El pedido inicial es deliberadamente incompleto: cadena de clínicas, turnos por web, “plazo breve”, integración con médicos / especialidades / prácticas, recordatorios y anulaciones. Con eso **no hay una línea base de alcance**. Estimar ahí es dar un orden de magnitud, no un compromiso.

En clase se descubrió el producto (tres roles, maestros de red, OS/planes, semáforo, check-in, varios países). Después se **cerraron** las reglas que más movían la estimación: países de la 1ra entrega, idioma, mail, cobro, forma de los maestros de OS, quién carga la agenda, quién cancela y qué pasa si el paciente no asiste.

Ese salto entre el brief y las respuestas **es el punto del caso**: el proyecto cambia mientras se pregunta. La estimación de abajo es sobre el **alcance ya cerrado**, no sobre el enunciado de una página.

---

## 1. Alcance de la 1ra entrega (cerrado)

Plazo de calendario: **3 meses** (el “plazo breve” del enunciado).

| Tema | Decisión |
|------|----------|
| Países | **Argentina, Bolivia y Chile** entran en la 1ra entrega |
| Idioma | Solo **castellano** (no hay i18n) |
| Notificaciones | Solo **mail** a pacientes y profesionales |
| Cobro | **Efectivo en la clínica**, no sistematizado. No hay pasarela ni caja en el sistema |
| Obras sociales | Listado: código + nombre. Planes relacionados: código + nombre. No se valida cobertura en línea |
| Agenda | El **administrador** carga, para cada profesional: profesión, consultorio y horario en el que atiende |
| Cancelación | La pueden hacer **paciente, profesional y administrador**. Siempre con **motivo** |
| Inasistencia | Si no asiste: **bloquea reservas nuevas por 1 mes** y se muestra **rojo** hasta que asista con éxito a un turno futuro |

**Sigue dentro** (de las notas de clase, no contradicho): login de los tres perfiles; filtros del paciente (ciudad, profesión, país/dirección); tope de reserva a 2 meses; no dos turnos del mismo paciente a la misma hora; cancelación del paciente hasta 1 h antes; check-in del profesional; precio particular informativo (no se cobra en el sistema); tiempo de atención por profesión; semáforo de calificación.

**Fuera de la 1ra entrega:** app nativa; SMS/WhatsApp; cobro o facturación; países distintos de AR/BO/CL; validación de cobertura con la obra social; integración con historia clínica / migración desde un legado.

**Supuestos que todavía sostienen el número** (si se rompen, hay que reestimar):

| # | Supuesto | Impacto si se rompe |
|---|----------|---------------------|
| 1 | El tope de **1 h** para cancelar aplica al **paciente**. Profesional y admin pueden anular después, siempre con motivo (operación: médico enfermo, cierre de consultorio). | Si los tres perfiles tienen el tope de 1 h, hay que definir excepciones. |
| 2 | Durante el mes de bloqueo el paciente **no reserva turnos nuevos**; los ya agendados se mantienen y el check-in de esos puede levantar el rojo. | Si también se cancelan los turnos futuros, hay que avisar por mail en lote. |
| 3 | Obras sociales y planes van **por país** (los catálogos de AR, BO y CL no se mezclan). | Un maestro único para los tres países es más simple; uno federado con un pagador regional es más complejo. |
| 4 | El rojo lo ven **profesional y administrador**, no es un “castigo” visible para el paciente en la pantalla de reserva (sí el bloqueo: no puede sacar turno). | Si el paciente ve el semáforo, hay que diseñar el mensaje y el riesgo reputacional. |
| 5 | Husos: Argentina UTC−3, Bolivia UTC−4, Chile con **horario de verano**. Las reglas de “1 h antes” y “2 meses” se calculan en la zona de la **clínica**. | Ignorar el DST de Chile genera turnos a la hora incorrecta. |
| 6 | No hay sistema de turnos previo que migrar. | Aparece un frente de datos. |
| 7 | Referente de negocio disponible semanalmente. Equipo con stack web conocido. | Espera o curva de aprendizaje alargan el camino crítico. |

---

## 2. Estimación

Con más reglas cerradas baja la incertidumbre de alcance y **sube el tamaño** (tres países y la máquina de estados de inasistencia entran sí o sí). Las obras sociales, al ser solo catálogo, **achican** ese módulo. El neto queda un poco por encima de la primera pasada (10 PM, un país).

### 2.1 Duración

Tres meses **ya no es una estimación**: es la **restricción** del cliente. Lo que se estima es si el alcance cerrado entra en ese calendario, y con qué equipo.

| Escenario | Duración | Qué cubre |
|-----------|----------|-----------|
| Optimista | 2,75 meses | Datos maestros listos, DST de Chile resuelto temprano, pocos cambios. |
| **Más probable** | **3 meses** | 1ra entrega completa, con el equipo de la § 2.3. |
| Pesimista | 4 meses | Husos/DST, bloqueo por inasistencia mal definido, o maestros de tres países tardíos. |

**PERT (duración):** \((O + 4M + P) / 6 = (2{,}75 + 4 \times 3 + 4) / 6 \approx\) **3,1 meses**.

Se presenta **3 meses de calendario**. El 0,1 de holgura PERT se cubre con contingencia de esfuerzo y con no aceptar más alcance.

### 2.2 Esfuerzo

Horas de trabajo (no de calendario). 1 persona-mes ≈ 160 h.

| Módulo | Alcance resumido | Esfuerzo (h) | Personas-mes |
|--------|------------------|--------------|--------------|
| Definición y UX | Reglas cerradas, wireframes de las 3 vistas, flujos de cancelación e inasistencia | 96 | 0,60 |
| Autenticación y perfiles | Login paciente, profesional y administrador; permisos | 80 | 0,50 |
| Administración (red) | Clínicas en AR/BO/CL, consultorios, profesionales; el admin arma profesión + consultorio + horario | 280 | 1,75 |
| Obras sociales y planes | ABM código/nombre y planes relacionados, por país | 48 | 0,30 |
| Reserva (paciente) | Filtros ciudad/profesión, restricción por país, tope 2 meses, no solapar, bloqueo 1 mes | 240 | 1,50 |
| Vista profesional | Agenda, check-in (asistió / no asistió), semáforo, precio particular informativo | 176 | 1,10 |
| Cancelación | Tres actores, motivo obligatorio, aviso por mail | 48 | 0,30 |
| Multi-país (transversal) | País en clínica y en paciente, husos, DST Chile, “1 h” y “2 meses” en hora local | 72 | 0,45 |
| Notificaciones | Mails de confirmación, recordatorio y anulación (con motivo) | 80 | 0,50 |
| Pruebas, UAT y producción | Concurrencia de slots, los tres países, inasistencia, cancelaciones | 200 | 1,25 |
| Gestión del proyecto | Coordinación, riesgos, cliente | 80 | 0,50 |
| **Total base** | | **≈ 1.400 h** | **≈ 8,8 PM** |
| **+ contingencia 25%** | Incertidumbre media: reglas más claras, queda huso/legal/datos | **≈ 1.750 h** | **≈ 11 PM** |

Qué se movió respecto de la primera estimación (~10 PM, un país, OS “completas”, multi-país en fase 2):

- **Suma:** AR/BO/CL en v1, DST, cancelación con motivo por tres roles, bloqueo 1 mes + rojo hasta asistencia exitosa.
- **Resta:** OS/planes pasan de módulo de cobertura a catálogo; no hay cobro; un solo idioma.
- **Contingencia:** de 30% a **25%** (hay más respuestas; el plazo sigue justo).

**Esfuerzo que se informa:** **11 personas-mes** (rango 9–13).

### 2.3 Personas necesarias


| Rol | Dedicación | Para qué |
|-----|------------|----------|
| Project manager / analista | 70% | Alcance ya inestable una vez; hay que congelarlo. |
| Desarrollador backend | 100% | Agenda, husos, bloqueo, mails, concurrencia. |
| Desarrollador frontend | 100% | Tres vistas, filtros por país, semáforo, admin de red. |
| QA | 100% | Tres países, inasistencia, tres caminos de cancelación. QA a medio tiempo no cubre este backlog de prueba. |

**4 personas, ~3,7 FTE.** Meter una quinta persona full-time en un proyecto de 3 meses **no acorta el calendario en la misma proporción** (comunicación y onboarding). Si el plazo se aprieta, el recurso correcto es **no aceptar más alcance**, no inflar el equipo.

### 2.4 Principales riesgos

| Riesgo | Estado | Efecto sobre la estimación |
|--------|--------|----------------------------|
| Alcance que sigue creciendo | Sigue abierto: ya pasó una vez | Cada módulo nuevo rompe los 3 meses |
| Tres países en v1 | Aceptado, no eliminado | Husos (sobre todo Chile), catálogos distintos, leyes de datos de tres estados |
| Doble reserva | Técnico, desde el día 1 | No es un CRUD; hay que probarlo |
| Inasistencia (bloqueo + rojo) | Regla nueva y fácil de malinterpretar | Retrabajo si no se cierra qué pasa con turnos ya dados |
| Maestros tardíos | El admin carga toda la oferta | Sin horarios/consultorios el sistema no se puede usar en UAT |
| Calificación / bloqueo del paciente | Dato sensible en tres jurisdicciones | Riesgo legal, no solo de desarrollo |
| Plazo = 3 meses fijos | Ya no hay “breve” ambiguo; hay fecha | No hay colchón de calendario; el colchón es el 25% de esfuerzo |

---

## 3. Preguntas del práctico

### 3.1 Gestión de riesgos — ¿Qué riesgos se detectaron desde el principio?

Estos se ven **con el enunciado original**, antes de preguntar:

1. **Alcance ambiguo.** “Integrarse con los médicos, especialidades y prácticas” no dice si hay un sistema existente, qué es una “práctica” ni quién mantiene los maestros.
2. **Plazo sin ancla.** “Listo en un plazo breve” no era un hito. Cualquier número se podía leer como compromiso. *(Después se ancló en 3 meses.)*
3. **Cadena de clínicas.** Varias sedes implican maestros, horarios y posiblemente países; el brief no cuantificaba.
4. **Recordatorios y anulaciones sin reglas.** Canal, anticipación, quién anula y hasta cuándo son el corazón del producto y no estaban definidos.
5. **El título del caso.** Si el proyecto se descubre mientras se construye, el riesgo dominante es **creep de alcance**, no la tecnología web.

Lo que apareció al preguntar (AR/BO/CL, OS catálogo, tres canceladores, bloqueo 1 mes) **confirma** 1 y 5: no eran visibles como módulos, sí como incertidumbre de alcance.

### 3.2 Dividir — ¿Qué módulos se habrían separado?

Por **entregable / dominio**, no por capa técnica:

1. **Identidad y accesos** — paciente, profesional, administrador.
2. **Maestros de red** — clínicas (con país), consultorios, profesionales; el admin arma profesión + consultorio + horario; tiempo de atención por profesión.
3. **Obras sociales** — catálogo código/nombre y planes relacionados, por país. No es un motor de cobertura.
4. **Reserva de turnos** — búsqueda, filtros, país del paciente, tope 2 meses, no solapar, bloqueo por inasistencia.
5. **Agenda del profesional** — ver turnos, check-in, semáforo, precio particular informativo.
6. **Cancelación** — tres actores, motivo, efecto en la agenda.
7. **Notificaciones** — mails de confirmación, recordatorio y anulación.

Multi-país no es un módulo de pantalla: es **transversal** a 2, 4 y 7 (país, huso, plantillas). Separarlo evita que “Chile” se cuele como un extra al final.

### 3.3 Validación temprana — ¿Qué prototipo se habría construido primero?

**Un corte vertical de reserva, ya con país:** un paciente con dirección en Argentina busca un profesional en una ciudad argentina, toma un hueco; un paciente de Chile **no** ve esa clínica; el profesional hace check-in; un no-show deja al paciente en rojo y sin poder reservar.

No se prototipa primero el ABM de obras sociales: es un listado. Lo que hay que probar pronto:

- búsqueda + slot + confirmación por mail;
- **restricción por país**;
- cancelación con motivo (al menos paciente y profesional);
- **no-show → rojo + bloqueo**, y asistencia posterior que apaga el rojo.

Formato: wireframe de las tres vistas + flujo real con **una clínica por país**, un consultorio y un médico. Datos de juguete. Días, no semanas.

### 3.4 Datos — ¿Qué preguntas se le harían al cliente antes de seguir estimando?

**Ya respondidas** (y usadas en esta estimación): países de v1; idioma; canal de aviso; cobro fuera del sistema; forma de OS/planes; plazo = 3 meses; quién carga la agenda; quién cancela y con motivo; efecto de la inasistencia.

**Seguirían haciéndose**, porque todavía mueven esfuerzo o riesgo:

- ¿Cuántas clínicas y profesionales el día 1 en cada país?
- ¿Hay sistema de turnos hoy? ¿Hay que migrar pacientes y turnos?
- ¿Profesión, especialidad y práctica son el mismo catálogo?
- El tope de 1 h para cancelar: ¿solo el paciente, o también profesional y admin?
- En el mes de bloqueo: ¿se conservan los turnos ya dados?
- ¿El paciente ve el semáforo o solo el bloqueo al intentar reservar?
- ¿El profesional asocia planes, o el listado de OS/planes es puramente administrativo?
- ¿El precio particular lo ve el paciente al reservar?
- ¿Leyes de datos: el profesional de una clínica de Chile puede ver la inasistencia de un paciente en Argentina?
- ¿Volumen y picos (apertura de agenda)?

Sin **volumen de sedes**, **migración** y **quién ve el semáforo**, las 11 PM se pueden comprometer como orden de magnitud, no como precio cerrado de contrato.

---

## 4. Cómo se estimaría con más información

Con las respuestas de 3.4 se baja otra vez la incertidumbre y se cruzan métodos (no usar uno solo).

### Analogía

Comparar con una **agenda web multi-sede** ya entregada. Ajustar por: tres países vs. uno, husos, tres roles, si había o no cobro, si el no-show bloqueaba. Sirve para el orden de magnitud. No sirve si el análogo era un CRUD de turnos en un solo huso.

### Juicio experto

Un PM o desarrollador que haya puesto en producción turnos en **más de un país** revisa el backlog y da O/M/P por módulo. Es el método que mejor captura **DST de Chile, doble booking y la máquina de inasistencia**. Sesgo a vigilar: estima *su* velocidad, no la del equipo que va a construir.

### Story points

Historias del tipo “como paciente en Bolivia, filtro profesionales de mi país por ciudad y profesión”. Relativo (1-2-3-5-8). Capacidad: 6 sprints de 2 semanas en 3 meses. Con velocidad inicial conservadora de ~22 SP/sprint hay **~132 SP** de techo. Si el backlog cerrado supera eso, no entra: se recorta o se alarga. Útil *durante* el proyecto; al día 1 la velocidad es un supuesto.

### Puntos de función

Conteo sobre el alcance cerrado:

- **ILF:** usuarios, clínicas (con país), consultorios, profesionales, asignaciones horario–consultorio–profesión, turnos, inasistencias/calificación, precios particulares, obras sociales, planes.
- **EI:** login, ABM de maestros, reserva, cancelación con motivo (×3 actores), check-in.
- **EO:** mails, semáforo, agenda del médico.
- **EQ:** búsqueda con filtros y país.

Orden de magnitud: **140–200 PF**. A 8–12 h/PF → **1.100–2.400 h**, coherente con las **1.750 h** de la § 2. Tres países no triplican los PF (no hay tres sistemas); suman atributos, reglas y consultas. El bloqueo por inasistencia **sí** suma archivos e interfases: no era visible en el brief.

---

## 5. Cifras a presentar (resumen)

| Variable | Valor |
|----------|--------|
| **Duración** | **3 meses** de calendario (restricción del cliente; PERT ≈ 3,1) |
| **Esfuerzo** | **11 personas-mes** (≈ 1.750 h con 25% de contingencia) |
| **Personas** | **4 perfiles / ~3,7 FTE** (PM-analista 70%, backend, frontend, QA 100%) |
| **Riesgos principales** | Creep de alcance, tres países/husos, doble reserva, regla de inasistencia, maestros tardíos, datos sensibles, plazo sin colchón de calendario |

**Recomendación al cliente:** comprometer los 3 meses **sobre este alcance cerrado** (web, castellano, AR/BO/CL, mail, OS/planes catálogo, agenda cargada por admin, cancelación con motivo, bloqueo 1 mes + rojo). Cobro, app, otros países y cobertura en línea quedan explícitamente **fuera**. Cualquier ítem nuevo se evalúa como cambio: o se saca otra cosa, o se mueve la fecha.
