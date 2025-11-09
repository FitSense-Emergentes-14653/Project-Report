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

La planificación del primer sprint se llevó a cabo mediante una reunión virtual a través de Google Meet. Durante esta sesión, el equipo acordó los objetivos del sprint, estimó las historias de usuario y definió la capacidad de trabajo (*velocity*) para el periodo. La siguiente tabla resume la información discutida y registrada durante dicha sesión.

| **Elemento** | **Detalle** |
|--------------|-------------|
| **Sprint #** | Sprint 1 |
| **Sprint Planning Background** | Planificación inicial del proyecto FitSense, priorizando la entrega de interfaces clave tanto en la landing page como en la primera versión funcional del mobile app y chatbot AI. |
| Fecha | 2025-11-03 |
| Hora | 10:00 PM |
| Lugar | Virtual (Google Meet) |
| Preparado por | Cuadros Rodríguez, Juan Alejandro |
| Participantes de la reunión de planificación | - Cuadros Rodríguez, Juan Alejandro<br> - Jarama Peñaloza, Fiorella<br> - Lucas Coronel, Nadia Alessandra<br> - Calisaya Sánchez, Juan Jesús	<br> - Rubio Calixto, Adrian Gustavo |
| Resumen del Sprint n–1 (Review) | No aplica — este es el primer sprint del proyecto. |
| Resumen del Sprint n–1 (Retrospectiva) | No aplica — este es el primer sprint del proyecto. |
| **Sprint Goal & User Stories** | Nuestro objetivo para este Sprint 1 es entregar una **primera versión de la Landing Page**,  **Mobile app de FitSense** y **ChatBot AI**, que permitan comunicar de manera clara la propuesta de valor de la plataforma, la creacion de planes de rutina basados en las caracteristicas del usuario, e implementar las funcionalidades base del sistema. Esto incluirá componentes clave como Navbar, Footer, secciones informativas (Inicio, Acerca de, Características, Contacto), así como los primeros módulos de gestiones de rutinas, peso y altura. El éxito del sprint se evaluará mediante la validación visual, funcional y la ejecución de pruebas de aceptación automatizadas. |
| Velocidad del Sprint (Story Points esperados) | 72 |
| Suma total de Story Points asignados | 72 |

#### 7.2.1.2. Sprint Backlog 1

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
