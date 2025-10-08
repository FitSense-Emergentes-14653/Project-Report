<p align="center">
  <img src="img/chapter-1/upc.png" alt="Logo de UPC" width="100%">
</p>

<div align="center">

# <span style="color:red">**Universidad Peruana de Ciencias Aplicadas**</span>
## Carrera de Ingeniería de Software

Ciclo: 2025 - 20

Curso: Arquitecturas De Software Emergentes

NRC: 14653

Profesor: Berrocal Navarro, Richard Leonardo

“Informe de Trabajo Final"

Startup: TechSolutions

Producto: FitSense

Grupo: 2

|          Integrantes          |      Código      |
|:-----------------------------:|:-------------------:|
|   Calisaya Sánchez, Juan Jesús    |    u202121935    |
|   Cuadros Rodríguez, Juan Alejandro  |    u20221a359    |
|   Jarama Peñaloza, Fiorella    |   u202120418  |
|  Lucas Coronel, Nadia Alessandra   |    U202120430    |
|  Rubio Calixto, Adrian Gustavo   |    u202017622    |


Setiembre 2025 

</div>

---

## Registro de Versiones Del Informe

<table>
  <thead>
    <tr>
        <th>Versión</th>
        <th>Fecha</th>
        <th>Autor</th>
        <th>Descripción de modificación</th>
    </tr>
  </thead>
  <tbody>
  <tr>
      <td><strong>TB1</strong></td>
      <td>Sábado 16 de Setiembre</td>
      <td>
        <ul>
            <li>Calisaya Sánchez, Juan Jesús</li>
            <li>Cuadros RodriguVz, Juan Alejandro</li>
            <li>Jarama Peñaloza, Fiorella</li>
            <li>Lucas Coronel, Nadia Alessandra</li>
            <li>Rubio Calixto, Adrian Gustavo</li>
        </ul>
      </td>
      <td>
        Se han incluído los siguientes capítulos:
        <ul>
          <li>Capítulo I: Introducción</li>
          <li>Capítulo II: Requirements Elicitation & Analysis</li>
          <li>Capítulo III: Requirements Specification</li>
          <li>Capítulo IV: Strategic-Level Software Design</li>
          <li>Avance de Conclusiones, Bibliografía y Anexos</li>
        </ul>
      </td>
  </tr>
  </tbody>
</table>

## Project Report Collaboration Insights

URL Project Report (Github): https://github.com/FitSense-Emergentes-14653/Project-Report

![Insight](img/chapter-4/tb1-contribuidores.PNG)

![Insight](img/chapter-4/tb1-insight-2.PNG)

![Insight](img/chapter-4/tb1-insight-3.PNG)

![Insight](img/chapter-4/tb1-insight-4.PNG)

.
------

# Contenido

## [Capítulo I: Introducción](#capítulo-i-introducción)
- [1.1. Startup Profile](#11-startup-profile)
  - [1.1.1. Descripción de la Startup](#111-descripción-de-la-startup)
  - [1.1.2. Perfiles de integrantes del equipo](#112-perfiles-de-integrantes-del-equipo)
- [1.2. Solution Profile](#12-solution-profile)
  - [1.2.1. Antecedentes y problemática](#121-antecedentes-y-problemática)
  - [1.2.2. Lean UX Process](#122-lean-ux-process)
    - [1.2.2.1. Lean UX Problem Statements](#1221-lean-ux-problem-statements)
    - [1.2.2.2. Lean UX Assumptions](#1222-lean-ux-assumptions)
    - [1.2.2.3. Lean UX Hypothesis Statements](#1223-lean-ux-hypothesis-statements)
    - [1.2.2.4. Lean UX Canvas](#1224-lean-ux-canvas)
- [1.3. Segmentos objetivo](#13-segmentos-objetivo)

## [Capítulo II: Requirements Elicitation & Analysis](#capítulo-ii-requirements-elicitation--analysis)
- [2.1. Competidores](#21-competidores)
  - [2.1.1. Análisis competitivo](#211-análisis-competitivo)
  - [2.1.2. Estrategias y tácticas frente a competidores](#212-estrategias-y-tácticas-frente-a-competidores)
- [2.2. Entrevistas](#22-entrevistas)
  - [2.2.1. Diseño de entrevistas](#221-diseño-de-entrevistas)
  - [2.2.2. Registro de entrevistas](#222-registro-de-entrevistas)
  - [2.2.3. Análisis de entrevistas](#223-análisis-de-entrevistas)
- [2.3. Needfinding](#23-needfinding)
  - [2.3.1. User Personas](#231-user-personas)
  - [2.3.2. User Task Matrix](#232-user-task-matrix)
  - [2.3.3. User Journey Mapping](#233-user-journey-mapping)
  - [2.3.4. Empathy Mapping](#234-empathy-mapping)
  - [2.3.5. As-is Scenario Mapping](#235-as-is-scenario-mapping)
- [2.4. Ubiquitous Language](#24-ubiquitous-language)

## [Capítulo III: Requirements Specification](#capítulo-iii-requirements-specification)
- [3.1. To-Be Scenario Mapping](#31-to-be-scenario-mapping)
- [3.2. User Stories](#32-user-stories)
- [3.3. Impact Mapping](#33-impact-mapping)
- [3.4. Product Backlog](#34-product-backlog)

## [Capítulo IV: Solution Software Design](#capítulo-iv-solution-software-design)
- [4.1. Strategic-Level Domain-Driven Design](#41-strategic-level-domain-driven-design)
  - [4.1.1. Design Purpose](#411-eventstorming)
  - [4.1.2. Attribute-Driven Design Inputs](#412-context-mapping)
    - [4.1.2.1. Primary Functionality (Primary User Stories)](#4131-system-landscape-diagram)
    - [4.1.2.2. Quality attribute Scenarios](#4132-context-level-diagrams)
    - [4.1.2.2. Constraints](#4132-container-level-diagrams)
    - [4.1.2.3. Deployment Diagrams](#4133-deployment-diagrams)
- [4.1.3. Architectural Drivers Backlog](#413-software-architecture)
- [4.1.4. Architectural Design Decisions](#413-software-architecture)
- [4.1.5. Quality Attribute Scenario Refinements](#413-software-architecture)
- [4.2.  Strategic-Level Domain-Driven Design](#41-strategic-level-domain-driven-design)
  - [4.2.1. EventStorming](#413-software-architecture)
  - [4.2.2. Candidate Context Discovery](#413-software-architecture)
  - [4.2.3. Domain Message Flows Modeling](#413-software-architecture)
  - [4.2.4. Bounded Context Canvases](#413-software-architecture)
  - [4.2.5. Context Mapping](#413-software-architecture)
- [4.2.  Software Architecture](#41-strategic-level-domain-driven-design)
    - [4.3.1. Software Architecture System Landscape Diagram](#4131-system-landscape-diagram)
    - [4.3.2. Software Architecture Context Level Diagrams](#4132-context-level-diagrams)
    - [4.3.2. Software Architecture Container Level Diagrams](#4132-container-level-diagrams)
    - [4.3.3. Software Architecture Deployment Diagrams](#4133-deployment-diagrams)

## [Capítulo V: Tactical-Level Domain-Driven Design](#capítulo-iv-solution-software-design)
  - [5.1. Bounded Context: Security](#421-bounded-context-security)
    - [5.1.1. Domain Layer](#4211-domain-layer)
    - [5.1.2. Interface Layer](#4212-interface-layer)
    - [5.1.3. Application Layer](#4213-application-layer)
    - [5.1.4. Infrastructure Layer](#4214-infrastructure-layer)
    - [5.1.5. Bounded Context Software Architecture Component Level Diagrams](#4215-component-level-diagrams)
    - [5.1.6. Bounded Context Software Architecture Code Level Diagrams](#4215-component-level-diagrams)
      - [5.1.6.1. Domain Layer Class Diagrams](#42161-domain-layer-class-diagrams)
      - [5.1.6.2. Database Design Diagram](#42162-database-design-diagram)

## [Capítulo VI: Solution UI/UX Design](#capítulo-v-solution-uiux-design)
- [6.1. Style Guidelines](#51-style-guidelines)
  - [6.1.1. General Style Guidelines](#511-general-style-guidelines)
  - [6.1.2. Web, Mobile and IoT Style Guidelines](#512-web-mobile-and-iot-style-guidelines)
- [6.2. Information Architecture](#52-information-architecture)
  - [6.2.1. Organization Systems](#521-organization-systems)
  - [6.2.2. Labeling Systems](#522-labeling-systems)
  - [6.2.3. SEO Tags and Meta Tags](#523-seo-tags-and-meta-tags)
  - [6.2.4. Searching Systems](#524-searching-systems)
  - [6.2.5. Navigation Systems](#525-navigation-systems)
- [6.3. Landing Page UI Design](#53-landing-page-ui-design)
  - [6.3.1. Landing Page Wireframe](#531-landing-page-wireframe)
  - [6.3.2. Landing Page Mock-up](#532-landing-page-mock-up)
- [6.4. Applications UX/UI Design](#54-applications-uxui-design)
  - [6.4.1. Applications Wireframes](#541-applications-wireframes)
  - [6.4.2. Applications Wireflow Diagrams](#542-applications-wireflow-diagrams)
  - [6.4.2. Applications Mock-ups](#542-applications-mock-ups)
  - [6.4.3. Applications User Flow Diagrams](#543-applications-user-flow-diagrams)
- [6.5. Applications Prototyping](#55-applications-prototyping)

## [Capítulo VII: Product Implementation, Validation & Deployment](#capítulo-vi-product-implementation-validation--deployment)
- [7.1. Software Configuration Management](#61-software-configuration-management)
  - [7.1.1. Development Environment Configuration](#611-development-environment-configuration)
  - [7.1.2. Source Code Management](#612-source-code-management)
  - [7.1.3. Style Guide & Conventions](#613-style-guide--conventions)
  - [7.1.4. Deployment Configuration](#614-deployment-configuration)
- [7.2. Implementation](#62-implementation)
  - [7.2.1. Sprint 1](#621-sprint-1)
    - [7.2.1.1. Sprint Planning](#6211-sprint-planning)
    - [7.2.1.2. Aspect Leaders and Collaborators](#62x2-aspect-leaders-and-collaborators)
    - [7.2.1.3. Sprint Backlog](#6213-sprint-backlog)
    - [7.2.1.4. Development Evidence](#6214-development-evidence)
    - [7.2.1.5. Testing Suite Evidence](#6215-testing-suite-evidence)
    - [7.2.1.6. Execution Evidence](#6216-execution-evidence)
    - [7.2.1.7. Services Documentation](#6217-services-documentation)
    - [7.2.1.8. Software Deployment Evidence for Sprint Review](#6218-software-deployment-evidence)
    - [7.2.1.9. Team Collaboration Insights](#6219-team-collaboration-insights)

- [7.3. Validation Interviews](#63-validation-interviews)
  - [7.3.1. Diseño de Entrevistas](#631-diseño-de-entrevistas)
  - [7.3.2. Registro de Entrevistas](#632-registro-de-entrevistas)
  - [7.3.3. Evaluaciones según heurísticas](#633-evaluaciones-según-heurísticas)
- [7.4. Video About-the-Product](#64-video-about-the-product)

## [Conclusiones](#conclusiones)
- [Conclusiones y recomendaciones](#conclusiones-y-recomendaciones)
- [Video About-the-Team](#video-about-the-team)
- [Bibliografía](#bibliografía)
- [Anexos](#anexos)

## Student Outcome

<table border="1" cellpadding="8" cellspacing="0">
  <tr>
    <th>Criterio específico</th>
    <th>Acciones realizadas</th>
    <th>Conclusiones TB1</th>
  </tr>
  <tr>
    <td>Comunica oralmente sus ideas y/o resultados con objetividad a público de diferentes especialidades y niveles jerarquicos, en el marco del desarrollo de un proyecto en ingeniería. </td>
    <td>
        <strong>Cuadros Rodriguez, Juan Alejandro</strong><br>
        <em>TB1</em><br>
       Durante el desarrollo de FitSense se llevó a cabo el diseño arquitectónico siguiendo el enfoque Attribute-Driven Design (ADD), priorizando las funcionalidades de mayor impacto en la arquitectura y definiendo escenarios representativos junto con sus soluciones, así como los drivers arquitectónicos que guiaron las decisiones clave; tras evaluar distintas alternativas estructurales, se optó por una arquitectura de tipo monolito modular por su adecuación al contexto del proyecto, y finalmente se elaboraron dos escenarios de prueba con sus respectivas soluciones para validar la solidez y el desempeño de la propuesta.<br>
        <strong>Calisaya Sánchez, Juan Jesús</strong><br>
        <em>TB1</em><br>
        Durante el proyecto FitSense, presenté los resultados del Impact Mapping, User Stories y requisitos del sistema a diferentes audiencias del proyecto. Comuniqué de forma clara cómo las épicas y features se conectan con los objetivos de negocio, adaptando la explicación para que tanto stakeholders como el equipo técnico entendieran la priorización y el valor de cada funcionalidad. <br>
        <em>TP</em><br>
        Durante el desarrollo del Tactical-Level Software Design para FitSense, presenté oralmente el diseño detallado de los bounded contexts Social y Notification, explicando la estructura de capas (Domain, Application, Interface e Infrastructure) siguiendo principios de Domain-Driven Design. Comuniqué de manera clara cómo los agregados, entidades y value objects encapsulan la lógica de negocio, adaptando mi discurso tanto para stakeholders técnicos como no técnicos. Esta presentación permitió que el equipo comprendiera las decisiones arquitectónicas, las relaciones entre componentes y cómo estos contextos interactúan mediante eventos de dominio para mantener la cohesión del sistema monolítico modular de FitSense. <br>
        <strong>Jarama Peñaloza, Fiorella</strong><br>
        <em>TB1</em><br>
        Realicé el EventStorming para mapear eventos, comandos, políticas, puntos de dolor y momentos clave; identifiqué bounded contexts (Plan, Monitoring, Notification, Security y Social) y modelé sus interacciones mediante context mapping. También generé los artefactos de arquitectura: System Landscape, Context, Container y Deployment Diagrams siguiendo el enfoque C4.<br>
               <em>TP</em><br>
        Realicé la Information Architecture considerando los sistemas de labeling, organization y navigation, con el fin de estructurar la experiencia del usuario y el flujo de información. Además, diseñé tanto los wireframes como los mockups de la aplicación móvil y algunos mockups web, que permiten visualizar la interacción, jerarquía de contenidos y navegación del sistema antes de su desarrollo.<br>
        <strong>Lucas Coronel, Nadia Alessandra</strong><br>
        <em>TB1</em><br>
        Durante el avance de este TB1 pude identificar la falta de soluciones integrales y accesibles en el ámbito del fitness digital y plantear a FitSense como respuesta innovadora, basada en IA, métricas personalizadas y motivación social. A través del análisis competitivo y el Lean UX Canvas, se definieron estrategias, hipótesis y un MVP que facilitarán validar la propuesta. En conjunto, se comunica de forma objetiva un proyecto de ingeniería con impacto positivo en la salud y la constancia de los usuarios.<br>
      <em>TP</em><br>
       He comunicado de manera clara y objetiva las ideas y resultados del proyecto FitSense, incluyendo los wireframes y mockups de la landing page y la aplicación web. La documentación y presentación del diseño, flujos de interacción y estilo visual permiten que tanto especialistas en ingeniería como stakeholders no técnicos comprendan fácilmente la propuesta y su valor, cumpliendo así con el objetivo de transmitir resultados de forma profesional y efectiva.<br>
        <strong>Rubio Calixto, Adrian Gustavo</strong><br>
        <em>TB1</em><br>
        Durante el desarrollo de FitSense, diseñé, registré y analicé entrevistas para identificar necesidades clave de los usuarios. Posteriormente, elaboré el proceso de Needfinding mediante User Personas, User Task Matrix, Empathy Mapping y As-is Scenario Mapping, lo que permitió comprender a fondo su contexto. Además, definí el Ubiquitous Language para unificar la comunicación entre el equipo y realicé el To-Be Scenario Mapping en el Capítulo III, proyectando escenarios futuros alineados con los objetivos del proyecto.<br>
        <br>
    </td>
    <td>
        <em>TB1</em><br>
        En conclusión, el desarrollo de FitSense permitió comunicar con objetividad y claridad los resultados obtenidos, abarcando desde el análisis de necesidades y la definición de requisitos hasta el diseño de la arquitectura emergente. De esta manera, logramos transmitir a públicos diversos técnicos y no técnicos, el valor, la viabilidad y el impacto positivo de la propuesta en el ámbito del fitness digital.<br>
        <em>TP</em><br>
        El trabajo práctico permitió consolidar la propuesta técnica y visual de FitSense, pasando del diseño conceptual a una solución arquitectónica y de experiencia de usuario completa. A través de la aplicación de metodologías como Domain-Driven Design, C4 Model y Lean UX, se logró integrar coherentemente el diseño táctico, la arquitectura de información y los prototipos interactivos, garantizando la alineación entre los objetivos de negocio, las necesidades del usuario y las decisiones de ingeniería.
        <br>
    </td>
  </tr>
  <tr>
    <td>Comunica en forma escrita ideas y/o resultados con objetividad a público de diferentes especialidades y niveles jerarquicos, en el marco del desarrollo de un proyecto en ingeniería.</td>
    <td>
        <strong>Cuadros Rodriguez, Juan Alejandro</strong><br>
        <em>TB1</em><br>
       El diseño arquitectónico se basó en el enfoque ADD, priorizando funcionalidades clave, definiendo escenarios representativos y alineando decisiones con drivers de negocio como rapidez, evolución y confianza del usuario; se optó por una arquitectura monolítica para una implementación ágil, dejando abierta la posibilidad de migrar a microservicios cuando el sistema crezca, y se aplicó el Reglamento de Protección de Datos para garantizar un entorno seguro y confiable para los usuarios.<br>
        <strong>Calisaya Sánchez, Juan Jesús</strong><br>
        <em>TB1</em><br>
        Elaboré la documentación de requisitos de FitSense (Capítulos III y IV) creando User Stories, Impact Mapping y Product Backlog que comunican las necesidades del usuario y objetivos de negocio. La documentación incluye desde épicas comprensibles para product owners hasta especificaciones técnicas detalladas, permitiendo que diferentes niveles del equipo entiendan los requisitos y su priorización.<br>
        <em>TP</em><br>
        Elaboré la documentación técnica completa del Tactical-Level Design para los bounded contexts Social y Notification de FitSense, incluyendo diagramas de clases del dominio, diagramas de componentes y modelos de base de datos. La documentación detalla cada capa arquitectónica con tablas estructuradas que describen agregados, entidades, value objects, servicios de dominio y repositorios, facilitando su comprensión tanto para desarrolladores como para arquitectos de software. Además, utilicé diagramas UML y Structurizr DSL para representar visualmente las relaciones entre componentes, asegurando que la documentación sea accesible y comprensible para públicos de diferentes especialidades dentro del marco del proyecto de ingeniería de software.<br>
        <strong>Jarama Peñaloza, Fiorella</strong><br>
        <em>TB1</em><br>
        Realicé el EventStorming para mapear eventos, comandos, políticas, puntos de dolor y momentos clave; identifiqué bounded contexts (Plan, Monitoring, Notification, Security y Social) y modelé sus interacciones mediante context mapping. También generé los artefactos de arquitectura: System Landscape, Context, Container y Deployment Diagrams siguiendo el enfoque C4.<br>
               <em>TP</em><br>
        Realicé la Information Architecture considerando los sistemas de labeling, organization y navigation, con el fin de estructurar la experiencia del usuario y el flujo de información. Además, diseñé tanto los wireframes como los mockups de la aplicación móvil y algunos mockups web, que permiten visualizar la interacción, jerarquía de contenidos y navegación del sistema antes de su desarrollo.<br>
        <strong>Lucas Coronel, Nadia Alessandra</strong><br>
        <em>TB1</em><br>
        El desarrollo de FitSense me permitió analizar de manera objetiva la problemática del mercado fitness digital y proponer una solución innovadora que combina personalización mediante IA, seguimiento de métricas y motivación social. Los resultados obtenidos, plasmados en el Lean UX Canvas y el análisis competitivo, fueron presentados de forma clara y estructurada para que puedan ser comprendidos por públicos de distintas especialidades y niveles jerárquicos, garantizando así una comunicación efectiva en el marco de un proyecto de ingeniería orientado a la mejora del bienestar de los usuarios.<br>
      <em>TP</em><br>
        El proyecto FitSense ha sido documentado y presentado de manera escrita con claridad y objetividad, integrando los wireframes y mockups de la landing page y la aplicación web. La información se estructuró de forma que pueda ser comprendida tanto por especialistas en ingeniería como por stakeholders de otras áreas, destacando los aspectos clave del diseño, la experiencia de usuario y la propuesta de valor de la plataforma, cumpliendo así con el objetivo de comunicar resultados de manera profesional y accesible a públicos de distintos niveles jerárquicos y especializaciones.<br>
        <strong>Rubio Calixto, Adrian Gustavo</strong><br>
        <em>TB1</em><br>
        Desarrollé el diseño, registro y análisis de entrevistas para recopilar información relevante sobre las necesidades de los usuarios. A partir de ello, elaboré el proceso de Needfinding, creando User Personas, User Task Matrix, Empathy Mapping y As-is Scenario Mapping, lo que permitió identificar puntos críticos de la experiencia. Además, definí el Ubiquitous Language para unificar la comunicación entre el equipo y los interesados. Finalmente, realicé el To-Be Scenario Mapping en el 
        Capítulo III, proyectando escenarios futuros que orientan el diseño de la solución y alinean los objetivos del proyecto con las expectativas de los usuarios.<br>
        <em>TP</em><br>
        Elaboré la documentación técnica completa del Tactical-Level Design para los bounded contexts Monitoring y Security de FitSense, incluyendo diagramas de clases del dominio, diagramas de componentes y modelos de base de datos. La documentación detalla cada capa arquitectónica con tablas estructuradas que describen agregados, entidades, value objects, servicios de dominio y repositorios, facilitando su comprensión tanto para desarrolladores como para arquitectos de software. Además, utilicé diagramas UML y Structurizr DSL para representar visualmente las relaciones entre componentes, asegurando que la documentación sea accesible y comprensible para públicos de diferentes especialidades dentro del marco del proyecto de ingeniería de software.<br>
        </td>

       <em>TB1</em><br>
        En conjunto, el desarrollo de FitSense permitió al equipo plasmar de manera escrita y objetiva los avances del proyecto, desde el análisis de necesidades de los usuarios y la definición de requisitos, hasta el diseño de la arquitectura emergente y la propuesta de solución innovadora. A través de técnicas como entrevistas, Needfinding, Impact Mapping, EventStorming, Lean UX Canvas y el enfoque C4, se generó documentación clara, estructurada y comprensible tanto para públicos técnicos como no técnicos. De esta forma, se aseguró una comunicación efectiva que integra la visión de negocio, la perspectiva del usuario y la solidez técnica en el marco de un proyecto de ingeniería orientado a la salud y el bienestar.<br>
        <em>TP</em><br><br>
        A nivel de comunicación y colaboración, el equipo demostró competencias sólidas en la transmisión oral y escrita de resultados técnicos, presentando documentación clara, diagramas estructurados y diseños visuales comprensibles para públicos técnicos y no técnicos. Este proceso fortaleció la capacidad de expresar ideas con objetividad, evidenciando madurez profesional y un enfoque interdisciplinario en el desarrollo de soluciones de software innovadoras orientadas al bienestar digital.
    </td>
  </tr>
</table>
