Contexto y línea de tiempo
Sep 2000: el FBI anuncia el programa Trilogy, con US$ 380 millones aprobados por el Congreso para modernizar la infraestructura de TI en tres partes: (1) hardware/PCs para las 56 oficinas de campo, (2) red segura (LAN/WAN), y (3) reemplazo del software de investigación (el obsoleto sistema ACS – Automated Case Support). Plazo original: 3 años.
Sep 2001: atentados del 11-S. La incapacidad del FBI para compartir información básica sobre Al Qaeda se vuelve noticia de tapa y genera presión política y del Congreso. Robert S. Mueller III asume como director del FBI, y bajo presión intensa acelera el programa Trilogy. 
SEBoK
Ene 2002: el FBI pide 70 millones adicionales para acelerar Trilogy, y el Congreso aprueba 78 millones. Acá empieza el quiebre del cronograma original. 
SEBoK
2003: se suceden rápidamente tres CIOs distintos antes de que Zal Azmi tomara el cargo, lo que refleja la inestabilidad de gobernanza. Pese a los problemas de desarrollo, SAIC (la contratista) entrega una versión de VCF en diciembre de 2003, que el FBI considera inadecuada. 
Wikipedia
Dic 2002: el FBI pide más fondos al Congreso al estar atrasado, y se aprueban 123 millones adicionales. 
Wikipedia
Ene/Abr 2005: el proyecto se cancela oficialmente. El costo estimado superó los 170 millones de dólares, un gasto de dinero público que generó fuertes críticas. 
California State University, San Bernardino
Según declaraciones del propio FBI, de los 170 millones invertidos, los proveedores habían entregado servicios y equipo reutilizable por 53,3 millones, con 12,2 millones sin gastar, resultando en una pérdida neta de 104,5 millones de dólares. 
Centre for Public Impact
Causas principales del fracaso

1. Cambio de alcance sin control (scope creep / gobernanza del alcance)

Los requerimientos de diseño de Trilogy estaban mal definidos y evolucionaban a medida que avanzaba el proyecto. Es más: algunos analistas señalan que es casi impropio hablar de "scope creep" en un proyecto donde el alcance nunca estuvo claramente definido desde el inicio. 
Strategic PPM
Strategic PPM
El objetivo original era mucho más modesto (poner una interfaz web sobre el ACS existente), pero tras el 11-S se decidió construir un sistema mucho más ambicioso, con gestión de casos, evidencia y registros integrados — sin replantear plazos ni presupuesto de forma realista.

2. Presión política y aceleración artificial del cronograma

El clima político post-11-S, sumado al caso de espionaje de Hanssen y los atentados de Oklahoma City, aumentó la presión para mostrar resultados rápido, sin importar si eso era técnicamente viable. 
Strategic PPM

3. Falta de gobernanza y rotación de liderazgo

Hubo rotación repetida en la gestión del proyecto, lo cual contribuyó a los problemas de especificación, y gran parte del personal del FBI involucrado tenía poco entrenamiento formal en gestión de proyectos de este tipo. 
Blogger
Blogger
En 2003 pasaron tres CIOs distintos en poco tiempo — sin continuidad no hay control efectivo del alcance ni rendición de cuentas.

4. Falta de arquitectura empresarial (enterprise architecture)

La ausencia de una arquitectura empresarial clara llevó a necesidades operativas mal definidas y resultados pobres; la complejidad del VCF creció por la expansión de requerimientos hasta superar las 700.000 líneas de código. 
Academia.edu

5. Comunicación deficiente con el Congreso / stakeholders

Pese a las garantías dadas al Congreso de que el proyecto avanzaba bien, en realidad estaba en serios problemas, y terminó siendo declarado inutilizable. 
Calleam
Cómo conectarlo con la teoría de dirección de proyectos (para tu análisis)

Para el caso práctico te conviene mapear esto a marcos conocidos (PMBOK / gobernanza de proyectos):

Gestión del alcance: no hubo línea base de alcance ni proceso formal de control de cambios (change control board). Cada nueva exigencia política se sumaba sin evaluar impacto en costo/cronograma/calidad.
Gobernanza: no existía un comité de dirección estable ni un "project sponsor" con continuidad — la rotación de CIOs equivale a cambiar de sponsor cada pocos meses.
Gestión de interesados (stakeholders): el Congreso, el FBI y el contratista (SAIC) tenían expectativas distintas y mal alineadas.
Triple restricción: se aceleró el cronograma (por presión política) sin ajustar alcance ni presupuesto — la ecuación clásica de "querer todo, rápido y barato" que no cierra.
Rol del contratista: SAIC fue acusada de facturar por horas sin suficiente supervisión de calidad ni entregables verificables — típico problema de contratos mal estructurados (falta de métricas de aceptación).
Lecciones (post-mortem/OIG): el caso derivó en un informe de la Oficina del Inspector General de EE.UU. que documentó estas fallas, y sirvió de base para el proyecto sucesor, Sentinel, que sí llegó a implementarse (con otro enfoque metodológico, más iterativo).