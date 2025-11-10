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

🔗 **Trello Board:** [https://trello.com/b/fitsense-sprint1](https://trello.com/b/fitsense-sprint1)  
📸 *Ver Figura 7.2.1.2.1 — Tablero Kanban del Sprint 1 (To-Do / In-Progress / Done)*

---

| **User Story** |  | **Work-Item / Task** | **Descripción** | **Estimación (Horas)** | **Asignado a** | **Estado** |
|----------------|--|----------------------|-----------------|------------------------|----------------|-------------|
| **US-33**<br>Crear Usuario (Sign-Up) a través de API | | T-01<br>Diseñar modelo de datos `User` | Estructurar entidad y esquema de validación en backend | 3 | Juan Cuadros | ✅ Done |
| | | T-02<br>Implementar endpoint `/api/users/signup` | Registro de usuarios en la base de datos | 5 | Juan Cuadros | ✅ Done |
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

#### 7.2.1.4. Testing Suite Evidence for Sprint Review

#### 7.2.1.5. Execution Evidence for Sprint Review.

#### 7.2.1.6. Services Documentation Evidence for Sprint Review

#### 7.2.1.7. Software Deployment Evidence for Sprint Review

### 7.1.8.Team Collaboration Insights during Sprint

## 7.3. Validation Interviews

### 7.3.1. Diseño de Entrevistas

### 7.3.2. Registro de Entrevistas

### 7.3.3. Evaluaciones según heurísticas

## 7.4. Video About-the-Product
