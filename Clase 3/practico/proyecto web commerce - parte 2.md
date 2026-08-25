# Práctico Unidad 3 — Parte 2
## Cambios de alcance: ¿seguimos teniendo el mismo proyecto?

**Asignatura:** Dirección de Proyectos  
**Unidad:** 3 — Alcance, Tiempo y Recursos  
**Proyecto:** Canal de ventas online para empresa mediana de artículos deportivos  
**Línea base:** [proyecto web commerce.md](proyecto%20web%20commerce.md) (Parte 1)

---

## 0. Respuesta al Director General

> **«Si aprobamos estos cambios... ¿seguimos teniendo el mismo proyecto?»**

**No.** Si el Directorio aprueba el paquete completo, deja de existir el proyecto aprobado (un canal web transaccional listo en seis meses para Navidad) y aparece **otro emprendimiento**: un programa de transformación digital con ocho frentes adicionales, otros usuarios, otras integraciones y otra fecha de entrega.

El proyecto no se define por el nombre (*«la web de e-commerce»*), sino por **objetivo + alcance + plazo + criterio de éxito**. Cambiar las tres primeras variables al mismo tiempo no es un ajuste: es un proyecto distinto, o varios proyectos disfrazados de uno solo.

| Dimensión | Proyecto aprobado (línea base) | Si se aprueba todo el paquete |
|-----------|--------------------------------|-------------------------------|
| Objetivo | Vender online en todo el país **antes de Navidad** | Plataforma digital amplia (fidelización, app, proveedores, IA, fiscalidad) |
| Producto | Sitio web transaccional (6 requerimientos) | Sitio + app + portal B2B + motor de lealtad + IA + facturación + WhatsApp |
| Usuarios | Cliente final y operador interno | + proveedores, + usuarios de app, + AFIP, + bots/IA |
| Plazo | 26 semanas (camino crítico saturado, holgura 0) | ~40 semanas o más (Navidad perdida) |
| Éxito | Go-live vendible en la campaña | «Tener todo»; el hito comercial que justificó la inversión desaparece |

**Recomendación antes de aprobar:** no firmar el paquete como un único cambio. Proteger la línea base de Navidad, incorporar solo lo que **habilita la venta** en esa ventana, y tratar el resto como fases o proyectos aparte. Aprobar todo ahora pone en riesgo **las ganancias que el canal sí podría generar en diciembre** si se mantiene el alcance original.

---

## 1. Contexto: de dónde venimos y qué pide ahora el Directorio

La empresa está en un buen momento comercial y quiere acelerar la transformación digital. El Directorio considera que un canal online incrementará ventas y cobertura geográfica **sin abrir sucursales**. Ese argumento es el mismo que justificó el proyecto original; no exige, por sí solo, app nativa, portal de proveedores ni recomendaciones con IA.

Durante la ejecución, distintas áreas empujaron pedidos «estratégicos». El Directorio, luego de analizarlos, decidió **ampliar el alcance originalmente aprobado**. El equipo debe evaluar el impacto sobre la planificación **antes** de que esa decisión se vuelva definitiva.

Los ocho requerimientos nuevos:

1. Programa de fidelización  
2. Integración con Mercado Pago  
3. Integración con WhatsApp  
4. Desarrollar la App móvil  
5. Portal para proveedores  
6. Recomendaciones mediante IA  
7. Facturación electrónica  
8. Programa de puntos  

Dos observaciones de control de cambios, antes de estimar:

- **Fidelización y puntos son el mismo producto.** Un programa de puntos es el mecanismo habitual de un programa de fidelización. Tratarlos como dos iniciativas duplica EDT, presupuesto y expectativa. Se consolidan en una sola: *fidelización (puntos)*.
- **Mercado Pago no es necesariamente alcance extra.** La línea base ya incluye *pago con tarjeta* vía pasarela de terceros. En el mercado local, Mercado Pago suele **ser** esa pasarela. Si se decide ahora, sustituye el paquete 3.2.1; no suma un segundo cobro. Si se suma *además* de otra pasarela, sí es alcance nuevo.

---

## 2. Priorización respecto del objetivo de Navidad

El filtro no es «¿suena estratégico?». Es: **¿este cambio aumenta la probabilidad de vender online en todo el país en la campaña navideña, sin romper el plazo de 26 semanas?**

Lo que no contribuye a ese hito puede ser valioso *después*. Incorporarlo ahora desvía recursos del camino crítico y pone en riesgo el retorno que el Directorio ya esperaba de diciembre.

### 2.1 Clasificación

| Cambio | Alineación con el objetivo (Navidad) | Criticidad | Tratamiento |
|--------|--------------------------------------|------------|-------------|
| **Integración con Mercado Pago** | Alta. Es el medio con el que el cliente local efectivamente paga. Sin un cobro usable, el canal no vende. | Crítico para el go-live | **Fase 1 — sustituir** la pasarela genérica (no sumar una segunda). Decisión de proveedor sobre el paquete 3.2.1. Impacto de calendario bajo si se cierra en requerimientos. |
| **WhatsApp (versión liviana)** | Media-alta. Canal de confianza del cliente (consulta, aviso de pedido). Un botón de WhatsApp Business y notificaciones de estado no son un nuevo producto. | Útil, no bloqueante | **Fase 1 acotada:** enlace + plantillas de aviso. Fuera: chat commerce, catálogo en WhatsApp, atención 24/7 con bot. |
| **Facturación electrónica** | Media. La empresa ya factura en sucursal; el canal puede arrancar facturando con el proceso actual (lote / ERP) y automatizar después. Integrar AFIP al checkout es excelencia operativa, no el hito comercial. | Operativa / cumplimiento a mediano plazo | **Fase 2.** En Fase 1: procedimiento transitorio (el pedido online dispara factura por el circuito existente). No bloquear Navidad por el conector fiscal. |
| **Fidelización / programa de puntos** | Baja *para Navidad*. Sirve para retener a quien **ya compró**. En el primer diciembre el problema es adquirir y cobrar, no premiar recurrencia. Encaja en carrito y checkout: contamina el camino crítico. | No crítico | **Fase 2** (post-campaña), cuando haya base de clientes y tickets reales sobre los cuales acreditar puntos. |
| **Recomendaciones mediante IA** | Baja. Un motor de recomendación necesita historial de navegación y compra. En el lanzamiento no hay datos; el algoritmo no tiene con qué aprender. El catálogo y la búsqueda de la línea base ya permiten vender. | No crítico / prematuro | **Fase 3 o proyecto aparte**, después de meses de tráfico. Hasta entonces: destacados y «combina con» editoriales desde el panel. |
| **App móvil** | Baja para el hito. El objetivo es cobertura geográfica, no presencia en stores. Un sitio responsive cubre celular (donde se hace gran parte del e-commerce). La app es **otro producto** (iOS, Android, publicación, mantenimiento). | No crítico; es otro proyecto | **Proyecto separado**, recién cuando el canal web esté estable y se demuestre demanda de app. |
| **Portal para proveedores** | Nula respecto de Navidad. Cambia el usuario (B2B), el proceso (abastecimiento) y el beneficio (backoffice de compras, no venta al consumidor). Puede hasta retrasar el catálogo B2C si se mezcla la carga de productos. | No crítico; es otro proyecto | **Proyecto separado** de operaciones / supply chain. El e-commerce de Navidad se alimenta del catálogo interno, como está previsto. |

### 2.2 Lectura de la priorización

- **Alineados con el objetivo (entrar en Fase 1):** Mercado Pago como pasarela; WhatsApp liviano.  
- **Valiosos pero no críticos para diciembre (Fase 2):** facturación electrónica integrada; fidelización/puntos.  
- **Se desvían del objetivo o son otro proyecto (no mezclar):** app móvil, portal de proveedores, IA.

Aprobar los tres últimos *dentro* de este proyecto es la forma más rápida de dejar de tener el mismo proyecto.

---

## 3. Impacto sobre la EDT

La EDT aprobada tiene cinco entregables (definición, diseño, desarrollo, validación, producción). El paquete completo no entra como tareas sueltas: ensancha esas ramas y agrega productos que no eran el sitio (app, portal de proveedores). Deja de ser la misma WBS y, por tanto, el mismo objeto de control.

---

## 4. Impacto sobre recursos

El equipo de la Parte 1 está dimensionado justo para el flujo de compra. Mercado Pago como pasarela y un WhatsApp liviano entran; el resto exige perfiles que no están (fiscal, mobile, proveedores, datos). Sin contratar, el crítico se serializa; si se contrata para abarcar todo, el proyecto pasa a ser un programa. El PM a tiempo parcial no puede gobernar varios frentes.

---

## 5. Riesgos

| # | Riesgo | Prob. | Impacto | Relación con Navidad / ganancias |
|---|--------|-------|---------|----------------------------------|
| R1 | **Pérdida del hito navideño** por saturación del camino crítico | Alta si se aprueba el paquete | Muy alto | El canal no está en producción (o está inestable) en el pico anual de retail. |
| R2 | **Costo de oportunidad comercial** | Alta | Muy alto | Se dejan de cobrar ventas online de noviembre–diciembre que **sí** se podrían captar con el alcance original. Ver §6. |
| R3 | Gold plating: features sin usuarios | Alta (IA, app, puntos día 1) | Alto | Se invierte en capacidad que no genera ticket en la ventana que importa. |
| R4 | El proyecto se convierte en programa sin gobierno de programa | Alta | Alto | Nadie prioriza; todo es «estratégico»; nada termina. |
| R5 | Contagio de calidad: QA insuficiente | Alta | Alto | Un checkout con puntos, AFIP y dos medios de pago mal probado **no cobra** en diciembre. Peor que un sitio simple bien cobrado. |
| R6 | Dependencias de terceros (MP, WhatsApp, AFIP, stores, motor de IA) | Media-alta | Alto | Colas de homologación que el equipo no controla. |
| R7 | Conflicto de recursos / burnout | Alta sin contratar | Alto | Atraso del catálogo y del pago, núcleo de la venta. |
| R8 | Portal de proveedores retrasa el catálogo B2C | Media | Alto | Dos dueños del dato de producto; el paquete D (crítico) se traba. |
| R9 | Alcance fiscal mal dimensionado | Media | Alto | AFIP no es un «módulo más»; un error impide operar o genera contingencia. |
| R10 | Pérdida de foco del sponsor | Media | Medio | El Directorio mide «transformación digital»; el mercado mide si puede comprar antes de Navidad. |

La Parte 1 ya advertía que el proyecto no tiene colchón interno. Estos cambios no introducen un riesgo nuevo de tipo desconocido: **activan el riesgo que ya estaba identificado**, con más superficie.

---

## 6. Ganancias en riesgo: el costo de no llegar a Navidad

El caso de negocio no es «tener más tecnología». Es **incrementar ventas y cobertura geográfica** en una fecha fija. En retail, la campaña navideña concentra una parte desproporcionada de la demanda anual (equipamiento, regalos, temporada). Ese pico **no se recupera en enero**: el cliente ya compró, en la sucursal o en el competidor digital que el propio enunciado menciona.

### 6.1 Dos escenarios de resultado

**Escenario A — se protege el proyecto (recomendado)**  
Go-live en semana 26, alcance mínimo + Mercado Pago + WhatsApp liviano.  
Durante noviembre–diciembre el canal cobra. Cada pedido es ingreso que **hoy no existe** (la empresa solo vende en sucursal). Esos ingresos pagan el proyecto y justifican las fases siguientes.

**Escenario B — se aprueba el paquete**  
Go-live estimado ~semana 40 (febrero/marzo).  
En Navidad no hay canal, o hay un sitio a medias. Las features extra (puntos, IA, app, portal) **no facturan** porque no hay base de clientes online. La inversión del semestre se consume en construcción, no en venta.

### 6.2 Qué se pone en riesgo 

No hace falta un número exacto de facturación para decidir: la dirección ya creyó que el canal **incrementaría ventas**. Ese incremento, en el primer año, está concentrado en la campaña. Aprobar los cambios implica aceptar, en la práctica:

1. **Dejar de ganar lo que el canal original sí podría generar en el pico.** No es un costo contable de desarrollo; es margen no cobrado. Es irreversible en el ejercicio.
2. **Seguir limitados a sucursales en el momento de mayor demanda**, que es exactamente el problema que el proyecto venía a resolver.
3. **Regalar la ventana a los nuevos actores** del mercado. El enunciado de la Parte 2 dice que la empresa quiere competir con ellos. Competir en diciembre con un sitio que cobra vale más que competir en marzo con app, IA y puntos.
4. **Pagar dos veces el aprendizaje.** Fidelización, IA y app rinden cuando hay tráfico e historial. Construirlos antes del primer pedido es invertir en el vacío; después hay que rehacer reglas con datos reales.
5. **Un go-live tardío y recargado puede vender menos que un go-live a tiempo y simple.** Un checkout inestable en diciembre no solo no gana: puede dañar marca y forzar a apagar el canal en el peor momento.

En una frase para el Directorio: **los cambios no solo amenazan el cronograma; amenazan el ingreso que el cronograma original estaba diseñado para capturar.** Llegar tarde con más alcance es, en este caso, un peor negocio que llegar a tiempo con el alcance aprobado.

---

## 7. Síntesis

El Directorio no enfrenta un retoque de alcance: enfrenta la decisión de **abandonar el proyecto que aprobó** a cambio de un programa más ambicioso, incompatible con el plazo que el propio Directorio fijó.

- La EDT se parte en productos que no estaban en la línea base.  
- El cronograma deja de cerrar en 26 semanas; el camino crítico se alarga y se duplica (web recargada + app).  
- Los recursos de la Parte 1 no escalan; o se serializa el trabajo o se cambia el modelo de equipo.  
- El riesgo dominante no es técnico: es **perder Navidad y, con ella, las ganancias que un canal simple sí podría generar**.  
- Prioridad: Mercado Pago (sustitución) y WhatsApp liviano. Diferir facturación integrada y fidelización. No mezclar app, portal de proveedores ni IA.

**Respuesta formal:** no se recomienda aprobar definitivamente estas modificaciones como ampliación del proyecto en curso. Se recomienda aprobar una **Fase 1 acotada** que preserve el mismo proyecto —el mismo objetivo, el mismo hito y el mismo criterio de éxito— y tratar el resto como decisiones posteriores, con su propia planificación.
)
