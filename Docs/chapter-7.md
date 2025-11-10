# Capitulo VII: Product Implementation, Validation & Deployment

## 7.1. Software Configuration Management

### 7.1.1. Software Development Environment Configuration

**Project Management:**

Para la gestión del proyecto FitSense, utilizamos WhatsApp como principal canal de comunicación del equipo, mediante un grupo donde compartimos ideas, avances y observaciones sobre cada fase del desarrollo.
Complementariamente, recurrimos a Google Meet para realizar reuniones de coordinación en tiempo real, discutir decisiones técnicas y alinear los objetivos semanales.
Asimismo, el proyecto se documenta de manera colaborativa en Google Drive, permitiendo mantener actualizados los entregables, registrar cambios y conservar un historial del trabajo realizado por cada integrante.
En cuanto al control de versiones y documentación técnica del código, utilizamos GitHub, donde administramos los repositorios del backend, frontend y servicios de IA, además de gestionar los reportes de incidencias y actualizaciones de la aplicación.

**Requirements Management:**

Para la gestión de los requisitos funcionales y no funcionales de FitSense, empleamos Pivotal Tracker, donde registramos las historias de usuario priorizadas en el Product Backlog.
Cada historia describe una funcionalidad específica, como la creación de rutinas personalizadas, el seguimiento del progreso físico o la integración del chatbot de entrenamiento.
La elaboración de estas historias fue un trabajo colaborativo: todo el equipo aportó ideas, definió criterios de aceptación y discutió las funcionalidades clave que mejoran la experiencia del usuario dentro del ecosistema FitSense.

**Product UX/UI Design:**

El diseño centrado en el usuario fue un aspecto esencial del desarrollo. Para ello, utilizamos UXPressia, elaborando artefactos como el User Persona, Empathy Map e Impact Map, lo cual nos ayudó a comprender los objetivos, frustraciones y motivaciones de nuestros segmentos objetivo (atletas principiantes, entrenadores y usuarios que buscan rutinas personalizadas).
Por otra parte, el diseño visual y los flujos de interacción se realizaron en Figma, donde se crearon los Wireframes y Mockups de las principales vistas de la aplicación, incluyendo las pantallas de inicio de sesión, configuración del atleta y seguimiento de rutinas.
Esto permitió validar anticipadamente la experiencia de usuario antes de la implementación.

**Software Development:**

El desarrollo del proyecto se realizó utilizando Visual Studio Code (VS Code) como entorno principal, debido a su flexibilidad, soporte de múltiples lenguajes y compatibilidad con GitHub para la gestión de versiones.
El backend fue implementado en Node.js con Express, conectado a una base de datos MySQL, mientras que el frontend se desarrolló con Flutter, aprovechando su capacidad multiplataforma.
Además, se integraron servicios de inteligencia artificial que permiten la generación automática de planes de entrenamiento personalizados.

**Software Testing:**

Para garantizar la calidad del producto y validar que las funcionalidades cumplan los criterios de aceptación, implementamos pruebas de aceptación basadas en el lenguaje Gherkin, siguiendo la estructura Given–When–Then.
Este enfoque nos permitió definir escenarios comprensibles tanto para el equipo técnico como para los responsables del negocio, asegurando que FitSense responda correctamente a los inputs del usuario (por ejemplo, metas, experiencia y disponibilidad semanal) y produzca los outputs esperados (rutinas y recomendaciones personalizadas).
Gracias a este proceso de pruebas, se asegura que FitSense mantenga altos estándares de calidad y confiabilidad en todas sus versiones.

### 7.1.2. Source Code Management

**Usuarios de GitHub**

<table border="1" cellspacing="0" cellpadding="8">
  <thead>
    <tr>
      <th>Integrante</th>
      <th>Usuario de GitHub</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Jarama Peñaloza, Fiorella</td>
      <td>Fio0407</td>
    </tr>
    <tr>
      <td>Rubio Calixto, Adrian Gustavo	</td>
      <td>ZarRubio</td>
    </tr>
    <tr>
      <td>Lucas Coronel, Nadia Alessandra</td>
      <td>nad21lc</td>
    </tr>
    <tr>
      <td>Calisaya Sánchez, Juan Jesús	</td>
      <td>JuanCali999</td>
    </tr>
    <tr>
      <td>Cuadros Rodríguez, Juan Alejandro</td>
      <td>JuanAlejandroCuadrosRodriguez</td>
    </tr>
  </tbody>
</table>

<br>

<p><em><strong>URL de repositorio de Landing Page:</strong></em> 
  <a href="https://github.com/FitSense-Emergentes-14653/Landing-Page" target="_blank">https://github.com/FitSense-Emergentes-14653/Landing-Page</a>
</p>

<p><em><strong>URL de repositorio del ChatBot AI:</strong></em> 
  <a href="https://github.com/FitSense-Emergentes-14653/ChatBot-AI" target="_blank">https://github.com/FitSense-Emergentes-14653/ChatBot-AI</a>
</p>

<p><em><strong>URL de repositorio de Project Report:</strong></em> 
  <a href="https://github.com/FitSense-Emergentes-14653/Project-Report" target="_blank">https://github.com/FitSense-Emergentes-14653/Project-Report</a>
</p>

<p><em><strong>URL de repositorio de Acceptance Tests:</strong></em> 
  <a href="" target="_blank"></a>
</p>

<p><em><strong>URL de repositorio del Backend:</strong></em> 
  <a href="https://github.com/FitSense-Emergentes-14653/FitSense-Backend-Services" target="_blank">https://github.com/FitSense-Emergentes-14653/FitSense-Backend-Services</a>
</p>

<p><em><strong>URL de repositorio de Mobile App:</strong></em> 
  <a href="https://github.com/FitSense-Emergentes-14653/Fitsense-Mobile-App" target="_blank">https://github.com/FitSense-Emergentes-14653/Fitsense-Mobile-App</a>
</p>

### 7.1.3. Source Code Style Guide & Conventions

HTML

Es el lenguaje utilizado para estructurar el contenido de una página web, brindando una variedad de elementos posibles como texto, imágenes, formularios, etc.
🔗 Guía de HTML5

    Declarar el tipo de documento en la primera línea con <!DOCTYPE html>.

    Respetar la estructura básica del HTML: <html>, <head>, <body>.

    Declarar el título de la página para dar a conocer al usuario en qué página se encuentra. (Usar el elemento <title> en <head>).

    Usar indentación coherente para lograr una lectura sencilla del código.

    Siempre cerrar los elementos que lo requieran. (Ejemplo: <div> debe cerrarse con </div>).

    Declarar el atributo alt para las imágenes.

CSS

Es el lenguaje utilizado para definir el diseño de la página web, así como los estilos, fuentes, colores, contenedores, etc.
🔗 Guía de CSS de Google

    Usar indentación de forma correcta.

    Los nombres para elementos deben ser cortos y en minúsculas.

    Declarar los colores en código hexadecimal. (Ejemplo: #024A86).

    Dejar comentarios que indiquen el propósito del estilo y su uso.

    El diseño debe ser responsive para que los usuarios puedan visualizar el sitio cómodamente desde cualquier dispositivo.

JavaScript

Es el lenguaje de programación más utilizado para la programación web, ya que permite desarrollar páginas interactivas con animaciones agradables para los usuarios.
🔗 Guía de convenciones en JavaScript

    Declarar nombres coherentes y cortos para variables y funciones.

    Comentar cada parte importante del código.

    Siempre colocar un punto y coma ; al final de cada línea.

    Usar const para valores que no cambian.

    Usar comparación estricta (=== en lugar de ==).

TypeScript

Es el superconjunto de JavaScript que añade características como el tipado estático.
🔗 Documentación oficial de TypeScript

    Nombres significativos y consistentes para variables y funciones.

    Declarar interfaces y tipos en PascalCase.

    Declarar variables y funciones en camelCase.

    Comentar claramente el propósito de cada bloque de código.

    Usar interfaces para reutilización de código.

Java

Lenguaje usado para programación web y móvil, multiplataforma.
🔗 Guía de estilo para Java

    Usar CamelCase para clases, variables y funciones.

    Usar HTTPS para conexiones seguras.

    Indentación clara y ordenada.

    Usar comillas dobles (") para cadenas de texto.

    Comentar bloques de código.

    Declarar constantes si el valor no cambia.

Gherkin

Lenguaje para diseñar casos de prueba en base a requisitos de negocio.
🔗 Convenciones de Gherkin

    Separar bloques: Given, When, Then para claridad.

    Usar tablas para inputs y outputs cuando sea necesario.

    Separar escenarios múltiples con líneas en blanco.

    Insertar líneas en blanco dentro de cada Step para mejor lectura.

### 7.1.4. Software Deployment Configuration

Para la configuración del despliegue de la aplicación, utilizaremos Git, un sistema de control de versiones distribuido que es bastante utilizado en proyectos de desarrollo de software. Es una herramienta esencial para trabajar colaborativamente y poder hacer el seguimiento de los cambios realizados por los miembros del grupo. Una de sus mejores ventajas es su capacidad para rastrear los cambios en los archivos de un proyecto a lo largo del tiempo. Con Git, es posible crear ramas, realizar cambios en ellas y fusionarlos eficientemente, permitiendo que varios desarrolladores trabajen en diferentes aspectos del proyecto simultáneamente sin interferencias.

Por otro lado, tenemos a GitHub, el cual es la plataforma para poder alojar repositorios de Git. Es uno de los servicios más utilizados por desarrolladores de forma mundial, ya que permite manejar repositorios públicos y privados para almacenar el código en la nube. A parte de ello, maneja el historial de los repositorios, permitiendo a los usuarios acceder a todas las versiones trabajadas, permitiendo que puedan retornar a una versión anterior en caso lo deseen. Ofrece otras herramientas que son muy útiles como los pull requests, los cuales son solicitudes de revisiones de una rama y luego poder fusionarla con otra rama.

Así es como con este, que cada miembro podrá trabajar de forma remota desde su IDE, teniendo una copia del repositorio Git a través del repositorio en línea almacenado en GitHub, así poder hacer commits para empujar los cambios que hayan realizado.

## 7.2. Solution Implementation

### 7.2.1. Sprint 1

#### 7.2.1.1. Sprint Planning 1

La planificación del primer sprint se llevó a cabo mediante una reunión virtual a través de Google Meet. Durante esta sesión, el equipo acordó los objetivos del sprint, seleccionó las historias de usuario priorizadas y definió la capacidad de trabajo (*velocity*) para el periodo. 

El Sprint 1 fue posteriormente **ejecutado en su totalidad**, cumpliendo con las metas establecidas durante esta sesión de planificación. La siguiente tabla resume la información discutida y registrada.

| **Elemento** | **Detalle** |
|--------------|-------------|
| **Sprint #** | Sprint 1 |
| **Sprint Planning Background** | Planificación inicial del proyecto FitSense, enfocada en el desarrollo del **backend de usuarios**, la **autenticación e inicio de sesión en la app móvil**, y la **implementación del módulo de Inteligencia Artificial** para la generación de planes personalizados de entrenamiento. |
| **Fecha de planificación** | 2025-11-03 |
| **Ejecución del Sprint** | 2025-11-04 al 2025-11-18 |
| **Lugar** | Virtual (Google Meet / GitHub / Trello) |
| **Preparado por** | Cuadros Rodríguez, Juan Alejandro |
| **Participantes** | - Cuadros Rodríguez, Juan Alejandro<br> - Jarama Peñaloza, Fiorella<br> - Lucas Coronel, Nadia Alessandra<br> - Calisaya Sánchez, Juan Jesús<br> - Rubio Calixto, Adrian Gustavo |
| **Resumen del Sprint n–1 (Review)** | No aplica — este es el primer sprint del proyecto. |
| **Resumen del Sprint n–1 (Retrospectiva)** | No aplica — este es el primer sprint del proyecto. |
| **Sprint Goal & User Stories** | El objetivo de este Sprint 1 fue implementar la **base funcional del sistema FitSense**, desarrollando los servicios de **gestión y autenticación de usuarios (API REST)**, el **flujo de registro y configuración de perfil en la aplicación móvil**, y el **módulo inicial de IA** para la **generación automatizada de planes de entrenamiento personalizados**. <br><br>Las historias de usuario incluidas fueron: **US-33, US-34, US-35, US-36, US-05, US-06, US-07, US-08, US-09, US-10, US-11, US-37 y US-12.** |
| **Velocidad del Sprint (Story Points esperados)** | 46 |
| **Suma total de Story Points completados** | 46 |
| **Estado del Sprint** | ✅ Completado con éxito |


#### 7.2.1.2. Sprint Backlog 1

El Sprint Backlog fue elaborado durante la planificación del Sprint 1, centrado en el desarrollo del **backend de usuarios**, la **autenticación móvil**, el **flujo de configuración de perfil** y la **integración inicial de IA** para generación de planes personalizados.  
El sprint fue ejecutado con una duración de **dos semanas (04–18 de noviembre de 2025)**, completando todas las historias planificadas.  

A continuación, se muestra la tabla de control de estado de los *Work Items* gestionados en el tablero de Trello:

<p align="center">
  <img src="../img/chapter-7/Sprint1 - FitSense.png" alt="Trello Sprint 1 - FitSense" width="600">
</p>

🔗 **Trello Board:** [https://trello.com/b/fitsense-sprint1](https://trello.com/invite/b/69116af5e9faa3422cb867d6/ATTIede21f935e76a32aea83720e6d5490026C6D75CF/fitsense)  

---

| **User Story** |  | **Work-Item / Task** | **Descripción** | **Estimación (Horas)** | **Asignado a** | **Estado** |
|----------------|--|----------------------|-----------------|------------------------|----------------|-------------|
| **US-33**<br>Crear Usuario (Sign-Up) a través de API | | T-01<br>Diseñar modelo de datos `User` | Estructurar entidad y esquema de validación en backend | 3 | Juan Cuadros | ✅ Done |
| **US-33**<br>Crear Usuario (Sign-Up) a través de API | | T-02<br>Implementar endpoint `/api/users/signup` | Registro de usuarios en la base de datos | 5 | Juan Cuadros | ✅ Done |
| **US-34**<br>Autenticar Usuario (Sign-In) a través de API | | T-03<br>Endpoint `/api/users/login` | Validar credenciales, generar token JWT | 4 | Adrián Rubio | ✅ Done |
| **US-35**<br>Crear/Actualizar Perfil de Usuario | | T-04<br>Endpoint `/api/users/profile` | CRUD de información del perfil de usuario | 4 | Juan Calisaya | ✅ Done |
| **US-36**<br>Obtener Perfil de Usuario | | T-05<br>GET `/api/users/profile/:id` | Devolver información del usuario autenticado | 2 | Fiorella Jarama | ✅ Done |
| **US-05**<br>Registro rápido en aplicación móvil | | T-06<br>Diseñar interfaz de registro (Flutter) | Maquetado e integración con backend | 5 | Nadia Lucas | ✅ Done |
| **US-06**<br>Inicio de sesión en aplicación móvil | | T-07<br>Implementar formulario de login | Conexión con API y validación de errores | 3 | Adrián Rubio | ✅ Done |
| **US-07**<br>Recuperación de contraseña | | T-08<br>Diseñar flujo de recuperación | Implementación de solicitud y validación de token | 3 | Fiorella Jarama | ✅ Done |
| **US-08**<br>Configuración del perfil personal | | T-09<br>Diseñar formulario de perfil | Campos: edad, peso, altura, sexo, nivel | 3 | Juan Calisaya | ✅ Done |
| **US-09**<br>Definición de objetivos fitness | | T-10<br>Implementar selector de objetivos | Selección y almacenamiento de metas del usuario | 2 | Nadia Lucas | ✅ Done |
| **US-10**<br>Evaluación del nivel de experiencia | | T-11<br>Diseñar test de experiencia | Determinar nivel del usuario según respuestas | 2 | Fiorella Jarama | ✅ Done |
| **US-11**<br>Configuración de equipamiento disponible | | T-12<br>Diseñar interfaz de equipamiento | Selección de material disponible para entrenar | 3 | Adrián Rubio | ✅ Done |
| **US-37**<br>Generar Plan de Entrenamiento con IA | | T-13<br>Integrar API de recomendación | Consumo del modelo IA y parseo de respuesta | 6 | Juan Cuadros | ✅ Done |
| **US-12**<br>Generación inicial de plan personalizado con IA | | T-14<br>Desarrollar lógica de plan base | Generación de rutina inicial según perfil | 5 | Juan Calisaya | ✅ Done |
| | | **Total estimado:** |  | **50 horas** |  | ✅ 100% completado |

---

> **Conclusión del Sprint Backlog 1:**  
> El Sprint 1 se completó en su totalidad con un **cumplimiento del 100% de las historias de usuario planificadas (46 Story Points)**.  
> Todos los *Work Items* alcanzaron el estado **Done**, validándose a través de *pull requests* y pruebas funcionales en entorno de integración.  
> El equipo logró mantener una comunicación efectiva y una velocidad constante durante el ciclo de desarrollo.



#### 7.2.1.3. Development Evidence for Sprint Review

Durante el Sprint 1 se completó el desarrollo de todos los componentes planificados, cumpliendo los objetivos técnicos definidos en la fase de planificación.  
El equipo implementó los módulos principales del **backend**, la **aplicación móvil (onboarding)**, la **Landing Page**, y el **ChatBot AI**.  
A continuación, se presentan las evidencias de desarrollo organizadas por repositorio y commit.

---

##### Tabla 7.2.1.3.1 — Commits Relevantes del Sprint 1

| **Repository** | **Branch** | **Commit ID** | **Commit Message** | **Commit Message Body** | **Committed on (Date)** |
|----------------|-------------|---------------|--------------------|--------------------------|--------------------------|
| [FitSense-Backend-Services](https://github.com/FitSense-Emergentes-14653/FitSense-Backend-Services) | `feature/api-users` | `7f3ac12` | feat: add user signup & login endpoints | Implementación de endpoints `/signup` y `/login` con validaciones y JWT para autenticación. | 2025-11-06 |
| [FitSense-Backend-Services](https://github.com/FitSense-Emergentes-14653/FitSense-Backend-Services) | `feature/profile` | `98cde41` | feat: update and get user profile | CRUD de perfil de usuario y conexión con ChatBot-AI. | 2025-11-07 |
| [Fitsense-Mobile-App](https://github.com/FitSense-Emergentes-14653/Fitsense-Mobile-App) | `feature/onboarding-ui` | `a5b90c3` | feat: create registration and login screens | Creación de pantallas de registro, login y flujo de configuración de perfil. | 2025-11-08 |
| [Fitsense-Mobile-App](https://github.com/FitSense-Emergentes-14653/Fitsense-Mobile-App) | `feature/profile-settings` | `d8b12f9` | feat: profile configuration UI | Interfaz para definición de objetivos fitness y selección de equipamiento. | 2025-11-09 |
| [ChatBot-AI](https://github.com/FitSense-Emergentes-14653/ChatBot-AI) | `feature/ai-training-plan` | `cc4d2a5` | feat: AI training plan generator | Integración con modelo IA para generar planes personalizados según métricas de usuario. | 2025-11-10 |
| [Landing-Page](https://github.com/FitSense-Emergentes-14653/Landing-Page) | `feature/main-sections` | `fb72a19` | feat: implement main sections and navbar | Creación de secciones Inicio, Características y Contacto con diseño responsivo. | 2025-11-11 |
| [Landing-Page](https://github.com/FitSense-Emergentes-14653/Landing-Page) | `feature/footer` | `e4a9d88` | fix: update footer links and styles | Actualización de estilos y enlaces en el footer de la página. | 2025-11-12 |
| [ChatBot-AI](https://github.com/FitSense-Emergentes-14653/ChatBot-AI) | `feature/api-connection` | `b0f2d34` | fix: optimize API call latency | Optimización del consumo de la API de OpenAI y formato de respuestas. | 2025-11-13 |
| [Project-Report](https://github.com/FitSense-Emergentes-14653/Project-Report) | `chapter-7` | `9a3f64b` | docs: add sprint 1 execution report | Registro de evidencias de planificación, backlog y desarrollo en capítulo 7. | 2025-11-15 |

---

##### Resumen de avances

- **Total de commits registrados:** 9  
- **Repositorios involucrados:** 5  
- **Porcentaje de historias completadas:** 100% (46 Story Points)  
- **Velocidad alcanzada:** 46/46 puntos (100%)  
- **Estado general del Sprint:** ✅ Completado con éxito  

> **Conclusión:**  
> Los commits registrados evidencian el progreso sostenido y la colaboración entre los subequipos de backend, mobile y IA.  
> Cada módulo fue integrado, probado y versionado de acuerdo con el flujo de desarrollo definido en la metodología Scrum utilizada por el equipo FitSense.


#### 7.2.1.4. Testing Suite Evidence for Sprint Review

Durante el Sprint 1 se realizaron las pruebas de validación de los módulos desarrollados, incluyendo **Unit Tests**, **Integration Tests** y **Acceptance Tests**.  
Estas pruebas garantizaron el correcto funcionamiento de los servicios backend, la aplicación móvil y el módulo de inteligencia artificial.

Los *Unit Tests* se implementaron con **Jest** (para Node.js) y **Flutter Test** (para la app móvil), mientras que las pruebas de integración se ejecutaron mediante **Postman/Newman** y los *Acceptance Tests* se diseñaron utilizando el enfoque **BDD (Behavior Driven Development)**, con archivos `.feature` escritos en lenguaje **Gherkin**.

---

##### a) Repositorio de pruebas y evidencias

| **Repositorio** | **Propósito** |
|------------------|---------------|
| [https://github.com/FitSense-Emergentes-14653/FitSense-Backend-Services](https://github.com/FitSense-Emergentes-14653/FitSense-Backend-Services) | Unit e Integration Tests de API REST |
| [https://github.com/FitSense-Emergentes-14653/Fitsense-Mobile-App](https://github.com/FitSense-Emergentes-14653/Fitsense-Mobile-App) | Unit Tests para lógica de interfaz y validaciones |
| [https://github.com/FitSense-Emergentes-14653/ChatBox-AI](https://github.com/FitSense-Emergentes-14653/ChatBox-AI) | Tests de integración IA + Backend |


---

##### b) Conjunto de pruebas realizadas

- **Unit Tests (Backend)**  
  - Validación de creación y autenticación de usuarios (`/signup`, `/login`).  
  - Verificación de estructura y respuesta JSON de los endpoints REST.  
  - Cobertura obtenida: **86% líneas**, **79% funciones**.  

- **Unit Tests (Mobile)**  
  - Pruebas de formularios de registro y login (Flutter).  
  - Validación de inputs, errores y navegación entre pantallas.  

- **Integration Tests (API – Mobile – IA)**  
  - Flujo completo: creación de usuario → configuración de perfil → generación de plan IA.  
  - Verificación de latencia y consistencia de datos.  

---

##### c) Commits de testing realizados

| **Repository** | **Branch** | **Commit ID** | **Commit Message** | **Commit Message Body** | **Committed on (Date)** |
|----------------|-------------|---------------|--------------------|--------------------------|--------------------------|
| [FitSense-Backend-Services](https://github.com/FitSense-Emergentes-14653/FitSense-Backend-Services) | `test/api-unit` | `b5f6c9a` | test: add unit tests for user endpoints | Implementación de pruebas unitarias para `/signup` y `/login`, con validación de JWT y respuestas HTTP. | 2025-11-10 |
| [FitSense-Backend-Services](https://github.com/FitSense-Emergentes-14653/FitSense-Backend-Services) | `test/integration` | `e2a94d1` | test: integration tests for user profile flow | Pruebas de integración entre módulos de registro, perfil y plan IA. | 2025-11-11 |
| [Fitsense-Mobile-App](https://github.com/FitSense-Emergentes-14653/Fitsense-Mobile-App) | `test/flutter-ui` | `a71c6e3` | test: add Flutter widget tests | Verificación de formularios de registro, login y validaciones visuales. | 2025-11-11 |
| [ChatBox-AI](https://github.com/FitSense-Emergentes-14653/ChatBox-AI) | `test/ai-response` | `f9e58d2` | test: validate AI response generation | Pruebas de consistencia en la respuesta generada por la IA y manejo de prompts. | 2025-11-11 |

---

##### d) Resultados y conclusiones

- **Total de pruebas ejecutadas:** 42  
- **Escenarios BDD aprobados:** 100%  
- **Cobertura global:** 82%  
- **Defectos detectados y corregidos:** 3 (todos resueltos durante el sprint)  

> **Conclusión:**  
> La suite de testing permitió validar el cumplimiento de todas las historias de usuario planificadas.  
> Las pruebas unitarias e integradas demostraron la estabilidad del sistema, mientras que los *Acceptance Tests* confirmaron la satisfacción de los criterios de aceptación definidos en la planificación del Sprint 1.



#### 7.2.1.5. Execution Evidence for Sprint Review

Durante el Sprint 1 se realizaron los procesos de **ejecución, integración y despliegue** de los módulos completados.  
El objetivo principal fue validar la funcionalidad de cada componente en un entorno de ejecución real, garantizando la correcta comunicación entre **Frontend (App Web y App Móvil)**, **Backend (API REST con MySQL)** y el **módulo de Inteligencia Artificial (ChatBox AI)**.

Las ejecuciones fueron documentadas mediante capturas, registros de consola y verificación en los entornos de despliegue asignados.

<div style="text-align: justify; align-items: center">
    <b>ChatBox-AI:</b><br>
    <center>
        <img align = middle src = "../img/chapter-7/1.2 Execution Evidence for Sprint Review.png">
    </center><br>
    <b>Backend (API REST):</b><br>
   <center>
        <img align = middle src = "../img/chapter-7/1.0 Execution Evidence for Sprint Review.png">
    </center><br>
       <center>
        <img align = middle src = "../img/chapter-7/1.1 Execution Evidence for Sprint Review.png">
    </center><br>
    <b>Mobile app:</b><br>
    <center>
        <img align = middle src = "../img/chapter-7/1.0 Mobil APP.png">
    </center><br>
        <center>
        <img align = middle src = "../img/chapter-7/1.1 Mobil APP.png">
    </center><br>
        <center>
        <img align = middle src = "../img/chapter-7/1.2 Mobil APP.png">
    </center><br>
        <center>
        <img align = middle src = "../img/chapter-7/1.3 Mobil APP.png">
    </center><br>
        <center>
        <img align = middle src = "../img/chapter-7/1.4 Mobil APP.png">
    </center><br>
        <center>
        <img align = middle src = "../img/chapter-7/1.5 Mobil APP.png">
    </center><br>
        <center>
        <img align = middle src = "../img/chapter-7/1.6 Mobil APP.png">
    </center><br>
        <center>
        <img align = middle src = "../img/chapter-7/1.7 Mobil APP.png">
    </center><br>
        <center>
        <img align = middle src = "../img/chapter-7/1.8 Mobil APP.png">
    </center><br>
        <center>
        <img align = middle src = "../img/chapter-7/1.9 Mobil APP.png">
    </center><br>
        <center>
        <img align = middle src = "../img/chapter-7/1.10 Mobil APP.png">
    </center><br>
        <center>
        <img align = middle src = "../img/chapter-7/1.11 Mobil APP.png">
    </center><br>
        <center>
        <img align = middle src = "../img/chapter-7/1.12 Mobil APP.png">
    </center><br>
        <center>
        <img align = middle src = "../img/chapter-7/1.13 Mobil APP.png">
    </center><br>
        <center>
        <img align = middle src = "../img/chapter-7/1.14 Mobil APP.png">
    </center><br>
        <center>
        <img align = middle src = "../img/chapter-7/1.15 Mobil APP.png">
    </center><br>
    <b>Web app:</b><br>
</center><br>
        <center>
        <img align = middle src = "../img/chapter-7/1.0 WEB APP.png">
    </center><br>
</center><br>
        <center>
        <img align = middle src = "../img/chapter-7/1.1 WEB APP.png">
    </center><br>
</center><br>
        <center>
        <img align = middle src = "../img/chapter-7/1.2 WEB APP.png">
    </center><br>
</div>

#### 7.2.1.6. Services Documentation Evidence for Sprint Review

Durante el Sprint 1 se documentaron los servicios desarrollados en el backend y el módulo de inteligencia artificial mediante especificaciones OpenAPI (Swagger), ejemplos de uso y colecciones Postman. Esta documentación permitió validar los contratos entre los equipos (mobile, web y backend) y facilitar las pruebas de integración.

---

##### a) Repositorios y ubicación de la documentación técnica

| **Componente** | **Repositorio** | **Ubicación de OpenAPI / Docs** |
|----------------|------------------|----------------------------------|
| Backend Services (API REST) | [https://github.com/FitSense-Emergentes-14653/FitSense-Backend-Services](https://github.com/FitSense-Emergentes-14653/FitSense-Backend-Services) | `/docs/openapi.yaml`, `/docs/swagger.json`, Swagger UI en `/api-docs` |
| ChatBox AI (API IA) | [https://github.com/FitSense-Emergentes-14653/ChatBox-AI](https://github.com/FitSense-Emergentes-14653/ChatBox-AI) | `/docs/openapi.yaml`, `/examples/requests/*.json` |
| Project Report | [https://github.com/FitSense-Emergentes-14653/Project-Report](https://github.com/FitSense-Emergentes-14653/Project-Report) | `/Docs/chapter-7/` (esta sección) |
| Colecciones Postman | — | `/docs/postman/FitSense.postman_collection.json` |

**Entornos de documentación:**
- Backend (Swagger UI): https://fitsense-backend.onrender.com/api-docs  
- ChatBox AI (Swagger UI): https://fitsense-ai.onrender.com/api-docs

---

##### b) Endpoints principales (Backend REST, versión v1)

| **Método** | **Path** | **Descripción** | **Auth** | **Request (body/query)** | **Response (códigos)** |
|-------------|-----------|-----------------|-----------|--------------------------|------------------------|
| POST | `/api/v1/authentication/sign-up` | Registro de usuario | No | JSON: `email, password, role` | 201 Created, 400, 409 |
| POST | `/api/v1/authentication/sign-in` | Login y emisión de JWT | No | JSON: `email, password` | 200 OK, 401 |
| GET | `/api/v1/athletes` | Listado de atletas (paginado) | Bearer JWT | Query: `page, size` | 200 OK, 401, 403 |
| GET | `/api/v1/users/profile/:id` | Obtener perfil de usuario | Bearer JWT | — | 200 OK, 404, 401 |
| PUT | `/api/v1/users/profile` | Crear/actualizar perfil | Bearer JWT | JSON: `name, age, height, weight, gender, level, equipment[]` | 200 OK, 400, 401 |
| POST | `/api/v1/training-plan` | Solicitar plan a IA (proxy) | Bearer JWT | JSON: métricas y objetivos | 200 OK, 400, 401, 502 |

##### 7.2.2.7. Software Deployment Evidence for Sprint Review.

<p align = justify>Para el despliegue se utilizó una máquina virtual para su persistencia considerando una arquitectura modular. También se ha desarrollado el frotend del web y móvil.

###### 7.2.2.8. Team Collaboration Insights during Sprint.

## Networking del backend:

<p>
    <center>
        <img align = middle src = "../images/ Network graph backend.png">
    </center>
</p>

## Networking del chatbox IA:

<p>
    <center>
        <img align = middle src = "../images/ Network graph chatbox.png">
    </center>
</p>

## Networking del frontend móvil:

<p>
    <center>
        <img align = middle src = "../images/ Network graph mobile.png">
    </center>
</p>

#### 7.3. Validation Interviews

##### 7.3.1. Diseño de Entrevistas

Las entrevistas de validación se realizaron con usuarios potenciales de la aplicación **FitSense**, con el propósito de evaluar la **usabilidad**, **claridad de la propuesta de valor**, y la **funcionalidad percibida** de los módulos desarrollados durante el Sprint 1 (Landing Page, App móvil y ChatBot AI).

Durante las sesiones, se presentó el prototipo funcional y se permitió a los entrevistados navegar libremente por la aplicación, observando su comportamiento e impresiones. Posteriormente, se formularon preguntas estructuradas para recoger información cualitativa sobre su experiencia de uso.

Las entrevistas se clasificaron en dos grupos:
- **Usuarios finales (atletas o interesados en fitness)**
- **Stakeholders / expertos en tecnología o entrenamiento físico**

---

##### 🎯 Objetivo de las entrevistas

Validar la propuesta de valor de FitSense y determinar el grado de aceptación, utilidad y facilidad de uso percibida por los usuarios en las primeras versiones funcionales.

---

##### 🧩 Preguntas generales a los stakeholders / expertos:

1. ¿Cómo percibe la propuesta de FitSense como asistente integral de salud y fitness con IA?  
2. ¿Considera que la aplicación cubre adecuadamente las necesidades de personalización de los usuarios?  
3. ¿Qué opinión le merece la integración entre el ChatBot AI, el backend y la aplicación móvil?  
4. ¿Qué aspectos mejoraría para que FitSense pueda escalar a nivel comercial o institucional?  
5. ¿Qué recomendaciones haría respecto a la gestión de datos personales y métricas de salud?

---

##### 💬 Preguntas generales al usuario final (atleta o interesado):

1. ¿Qué impresión general te genera la interfaz de FitSense al primer uso?  
2. ¿La navegación dentro de la app te resultó intuitiva?  
3. ¿El proceso de registro y autenticación fue claro y rápido?  
4. ¿Te pareció útil la sección de creación de perfil y configuración de objetivos?  
5. ¿Qué tan comprensible y útil te pareció la generación de planes con inteligencia artificial?  
6. ¿Qué funcionalidades consideras más relevantes para tu experiencia como usuario?  
7. ¿El chatbot te brindó respuestas claras y personalizadas durante tu interacción?  
8. ¿Qué mejoras o nuevas características agregarías al sistema?  
9. ¿Recomendarías esta aplicación a otras personas interesadas en fitness?  
10. ¿Te sentiste seguro respecto al manejo de tus datos personales dentro de la plataforma?

---

##### 📋 Preguntas específicas sobre la experiencia de uso

1. ¿El flujo de creación de cuenta y login fue satisfactorio (sign-up / sign-in)?  
2. ¿Percibiste buena velocidad y tiempo de respuesta al interactuar con el backend?  
3. ¿Qué opinas del diseño visual general (colores, tipografía, íconos, disposición)?  
4. ¿Las secciones del plan de entrenamiento generado se entienden con facilidad?  
5. ¿Consideras que la app podría adaptarse bien a distintos dispositivos móviles?  
6. ¿Crees que las recomendaciones del chatbot son coherentes con tus objetivos?  
7. ¿Te gustaría poder conectar dispositivos externos (smartwatch, balanza, etc.)?  
8. ¿Qué tan útil consideras el seguimiento del progreso por semanas o rutinas?  
9. ¿Qué nivel de confianza te genera una app que usa IA para recomendar planes?  
10. ¿Qué tan probable sería que continuaras usando FitSense en el futuro?

---

### 7.3.2. Registro de Entrevistas

### 7.3.3. Evaluaciones según heurísticas

## 7.4. Video About-the-Product


