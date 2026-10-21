# Sistema móvil de generación fotovoltaica en vehículo de transporte pesado

Trabajo Fin de Grado de Ingeniería Mecánica centrado en el diseño de un generador fotovoltaico móvil integrado en un semirremolque. El proyecto recorre las etapas de definición, diseño mecánico y eléctrico y evaluación económica.

> **Autor:** Antonio Serrano Corral
>
> **Documentación:** la memoria completa del TFG no se publica en este repositorio. Se presenta una síntesis del trabajo con imágenes y esquemas representativos.

## Objetivo y aportación

El proyecto estudia cómo llevar energía fotovoltaica a emplazamientos temporales o con acceso limitado a la red. Los módulos viajan protegidos en un semirremolque y se despliegan al llegar al destino. La aportación consiste en integrar en una propuesta de ingeniería la configuración transportable, sus mecanismos, el dimensionamiento eléctrico y un análisis preliminar de viabilidad.

## Desarrollo del proyecto por fases

La secuencia organiza el trabajo como un proyecto de ingeniería: cada fase concreta una decisión de diseño y produce información para la siguiente.

| Fase | Trabajo | Resultado documentado |
|---|---|---|
| 1. Definición y concepto | Necesidad, restricciones de transporte y exploración de alternativas (*brainstorming*) | Selección de una configuración fotovoltaica desplegable |
| 2. Diseño preliminar | Distribución del equipo, configuración de transporte y secuencia de despliegue | Ensamblaje CAD y propuesta de mecanismos |
| 3. Diseño mecánico de detalle | Modelado del conjunto, dimensionamiento de actuadores y comprobación estructural | Diseño final representado en CAD y análisis de una guía extensible |
| 4. Diseño eléctrico | Dimensionamiento del generador, almacenamiento, conversión, conductores y protecciones | Arquitectura eléctrica y esquema unifilar simplificado |
| 5. Viabilidad | Estimación de inversión, ingresos y mantenimiento bajo hipótesis de uso | Evaluación económica preliminar del concepto |

### Fase 1 — Definición y diseño conceptual

Se parte de la necesidad de disponer de suministro eléctrico móvil y se consideran las restricciones de transporte por carretera y la protección de los módulos durante el traslado. Se exploran distintas configuraciones mediante *brainstorming* y se desarrolla la alternativa de un semirremolque que despliega su superficie fotovoltaica en destino.

![Propuesta conceptual del generador solar móvil](docs/images/01-diseno-conceptual.jpg)

### Fase 2 — Diseño preliminar y despliegue

La propuesta se lleva a un ensamblaje CAD para estudiar la integración con el vehículo tractor y el paso entre las configuraciones de transporte y de generación. El diseño contempla paneles protegidos durante el traslado, alas abatibles, apoyos estabilizadores y guías extensibles.

![Ensamblaje CAD del tractor y el semirremolque](docs/images/02-ensamblaje-del-semirremolque.jpg)

*La memoria indica que el modelo de la cabeza tractora se obtuvo de GrabCAD y se adaptó para el ensamblaje.*

![Configuración del generador durante el transporte](docs/images/03-configuracion-de-transporte.jpg)

![Inicio de la secuencia de despliegue](docs/images/04-inicio-del-despliegue.jpg)

### Fase 3 — Diseño mecánico de detalle y cálculos

Se desarrolla el modelo del chasis y de los mecanismos de apertura, inclinación y extensión de los paneles hasta representar la configuración final desplegada.

![Modelo CAD del generador fotovoltaico desplegado](docs/images/05-generador-desplegado.jpg)

![Render del conjunto desplegado](docs/images/06-render-fotorrealista.jpg)

#### Dimensionamiento de mecanismos y cargas

El mecanismo de apertura de las alas contempla **ocho cilindros hidráulicos LARZEP SM01035**, seleccionados con apoyo de información del fabricante para las cargas consideradas en el diseño.

Para las guías extensibles, el cálculo considera **tres módulos por guía (67,5 kg)**, una inclinación máxima de **45°** y una presión de viento de **1,05 kN/m²**, estimada según el CTE, que se traduce en una acción de viento de **6,3 kN** en el caso estudiado. El equilibrio estático da componentes de reacción de **4.454,77 N** y **4.785,77 N**; la resultante empleada para dimensionar el cilindro hidráulico es **6.538,24 N**. Para la comprobación a flexión de la guía se aplica un factor de 1,25 a la componente correspondiente, obteniendo una carga de **5.982,21 N**.

#### Comprobación por elementos finitos

La memoria presenta un análisis estático de una guía extensible de acero **AISI 1020**, con una cara fijada y una carga de **5.982 N**. La malla contiene **82.595 nodos** y **51.822 elementos**, con un tamaño aproximado de **5,93 mm**. El análisis se realizó con **SOLIDWORKS Simulation**.

El informe obtiene una tensión de von Mises máxima de **305,3 MPa**, frente a un límite elástico indicado de **350 MPa**, y un desplazamiento máximo de **10,72 mm**. Estos resultados corresponden al modelo y las condiciones de carga descritos; no representan ensayos físicos ni validan el semirremolque completo.

![Malla de elementos finitos de la guía extensible](docs/images/08-malla-guia-extensible.jpg)

<p align="center">
  <img src="docs/images/09-tension-von-mises.jpg" alt="Resultado de tensión de von Mises en la guía" width="49%" />
  <img src="docs/images/10-desplazamiento-guia.jpg" alt="Resultado de desplazamiento de la guía" width="49%" />
</p>

*La forma deformada se representa con una escala visual ampliada; el desplazamiento máximo calculado es 10,72 mm.*

### Fase 4 — Dimensionamiento eléctrico y esquema unifilar

La memoria plantea un sistema aislado con acoplamiento en alterna (*AC coupling*) y recoge el siguiente dimensionamiento:

- **Generador fotovoltaico:** 63 módulos de 400 W, equivalentes a **25,2 kWp**.
- **Strings:** cuatro grupos de **16, 16, 16 y 15 módulos**, conectados a cuatro seguidores MPPT.
- **Conversión:** dos inversores híbridos trifásicos de 10 kW, con salida de 400 V trifásica.
- **Almacenamiento:** 30 baterías de litio de 3,55 kWh (**106,5 kWh nominales**); 15 por inversor, en tres grupos paralelos de cinco.
- **Conductores:** secciones calculadas de **2,5 mm²** entre strings e inversores y **6 mm²** entre inversores y caja de protecciones.

La selección de conductores contempla intensidad admisible, caída de tensión y cortocircuito. El diagrama resume la arquitectura y las protecciones descritas en el TFG.

![Esquema unifilar simplificado de la instalación fotovoltaica](docs/images/esquema-unifilar-simplificado.svg)

*Esquema didáctico basado en el plano unifilar del TFG; no sustituye al plano eléctrico original ni es documentación de montaje.*

### Fase 5 — Estudio de viabilidad

El estudio estima un presupuesto de **162.734,04 € con IVA** y unos ingresos de **32.000 €/año**, bajo la hipótesis de prestar el servicio a 25 €/hora durante ocho horas al día, cinco días por semana y ocho meses al año. Con esos supuestos, la memoria estima un periodo de recuperación de alrededor de **seis años** y un mantenimiento de **400 €/año**.

Son estimaciones académicas basadas en precios y condiciones de uso de la fecha del TFG. No constituyen una cotización actual ni una garantía de rentabilidad; el resultado depende, entre otros factores, de la demanda efectiva y del uso del sistema.

## Alcance del repositorio

El repositorio resume el diseño propuesto y una selección de sus representaciones y cálculos. No incluye la memoria completa ni los planos originales. Las imágenes muestran modelos y renders CAD; el TFG no documenta la fabricación y validación física del conjunto completo.

Este repositorio no concede una licencia abierta para el diseño ni para el contenido original del TFG. Algunas imágenes o modelos pueden incorporar recursos de terceros; consulta sus fuentes y licencias antes de reutilizarlos.
