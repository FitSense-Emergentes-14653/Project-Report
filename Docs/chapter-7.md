## **UNIT VII**

---

### Product Implementation, Validation & Deployment

#### 7.1. Software Configuration Management

##### 7.1.1. Software Development Environment Configuration

### Procedimiento de Identificación del Entorno de Desarrollo del Software

### Selección de Elementos de Configuración

- Se identifican los productos de trabajo críticos para el proyecto.
- Se identifican los productos de trabajo que son utilizados por más de un equipo de desarrollo.

## Elementos de Configuración

### Project Management

- [Google Drive](https://drive.google.com/drive) se utiliza para organizar los puntos a realizar, pendientes y realizados.
- [Trello](https://trello.com) se utiliza para establecer hitos y fijar límites para las tareas pendientes.

### Requirements Management

- Se utiliza [Discord](https://discord.com/login) como canal de comunicación para revisar y sugerir cambios en las tareas asignadas a cada integrante.

### Product UX/UI Design

- Se utiliza [Figma](https://figma.com) para el diseño de wireframes de alta fidelidad, Mockup y prototipos móviles.

### Software Development

- [UXPressia](https://uxpressia.com) se utiliza en la creación de artefactos de la metodología Lean UX.
- [Trello](https://trello.com) se usa para dar seguimiento a las historias de usuario y la organización de equipos.
- [Vertabelo](https://vertabelo.com/) se utiliza para la creación de diagramas de bases de datos.
- [Lucid Chart](https://www.lucidchart.com) se utiliza para elaborar Wireflows, User Flows y diagramas de clases.
- [Structurizr](https://structurizr.com) se utiliza para la creación de C4 Context, Container y Component.
- [GitHub](https://github.com) se utiliza para almacenar los repositorios del proyecto.

### Esquema de Identificadores Únicos

Para este proyecto, se utiliza el siguiente esquema para la codificación de los elementos de configuración:

`<StartUp><proyecto><type><name><versión>`

- `<StartUp>`: Identificador de la StartUp (FW).
- `<proyecto>`: Identificador del tipo de proyecto (RKG).
- `<type>`: Identificador del tipo de elemento.
- `<name>`: Nombre del elemento.
- `<versión>`: Versión del elemento.

### Ejemplos de Identificadores Únicos

- Requisitos: FW-RKG-REQ
- User stories: FW-RKG-REQ-US-1.0.0
- Sprint Backlog: FW-RKG-REQ-SB-1.0.0
- Product Backlog: FW-RKG-REQ-PB-1.0.0

- Repositorios: FW-RKG-REP
- Landing Page Repository: FW-RKG-REP-LP
- Mobile App Repository: FW-RKG-REP-WA

- Arquitectura: FW-RKG-ARQ
- User stories: FW-RKG-REQ-US-1.0.0
- Sprint Backlog: FW-RKG-REQ-SB-1.0.0
- Product Backlog: FW-RKG-REQ-PB-1.0.0

##### 7.1.2. Source Code Management

### Modelo de Creación de Ramas Gitflow

Este proyecto utiliza el modelo de creación de ramas Gitflow para el desarrollo y gestión de versiones en GitHub.

### Repositorios

| Nombre           | Enlace                                                                                                                        |
| ---------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| Back-end         | [Arquitecturas-De-Software-Emergente/ModelHouseV2](https://github.com/Arquitecturas-De-Software-Emergente/ModelHouseV2)       |
| Front-end mobile | [Arquitecturas-De-Software-Emergente/ModelHouseMovil](https://github.com/Arquitecturas-De-Software-Emergente/ModelHouseMovil) |
| Front-end Web    | [Arquitecturas-De-Software-Emergente/ModelHouseV1](https://github.com/Arquitecturas-De-Software-Emergente/ModelHouseV1)       |
| Landing Page     | [Arquitecturas-De-Software-Emergente/LandingPage](https://github.com/Arquitecturas-De-Software-Emergente/LandingPage)         |

### Ramas en el Modelo Gitflow

- **Main Branch:** En esta rama se encuentra la versión completa, probada y sin problemas en su ejecución. Es la rama que se desplegará y mostrará a los usuarios.

- **Hotfix Branch:** Se utiliza en caso de problemas con la versión en la rama Main. Sirve como respaldo para encontrar y solucionar problemas lo más rápido posible.

- **Release Branch:** En esta rama, la aplicación móvil se ejecuta sin problemas, pero debe pasar por pruebas para validar todas las funcionalidades. Cuando las pruebas se completan sin errores, esta versión pasa a la rama Main.

- **Develop Branch:** Esta rama sigue en desarrollo y se utilizan para solucionar distintos problemas o requerimientos en desarrollo. Cuando esta rama está lista para un sprint, pasa a la rama Release.

- **Feature Branch:** Estas ramas se crean según sea necesario para agregar nuevas funcionalidades a la aplicación móvil.
  - Deben derivarse de la rama develop.
  - Deben fusionarse de vuelta a la rama develop.
  - Notación: `Name of feature`

##### 7.1.3. Source Code Style Guide & Conventions

<p align = justify>- Para el desarrollo de nuestro proyecto hemos adoptado algunas referencias para nombrar elementos y programar en los lenguajes utilizados para la solución. </p>

<p align = justify>- Convenciones de Idioma</p>

- Uso del **español** para todos los artefactos que sirven como evidencia de desarrollo de la aplicación.
- Uso del **inglés** para la elaboración del código de compilación, tanto en el Back-end como en el Front-end.

<p align = justify>- Nomenclatura</p>

<p align = justify>- Seguiremos utilizando la nomenclatura establecida en "Software Development Environment Configuration" para lo relacionado con el uso y modificación de los distintos repositorios.</p>

- Herramientas
  - Para el desarrollo de la aplicación, utilizaremos las siguientes tecnologías:
  - **Back-end**: Sprint Boot.
  - **Front-end**: Vue para la web.
  - **Base de datos**: MySQL.
  - **Mobile**: Flutter para las aplicaciones móviles
  - **IDEs**: Rider y Visual Studio Code para la codificación, Flutter y Dart para el desarrollo de aplicaciones móviles, y WebStorm para Vue.
  - **Control de versiones**: GitHub y Gitflow.
  - **Diseño de interfaz**: Figma.

#### Semantic Versioning

<p align = justify>- Seguiremos utilizando Semantic Versioning para controlar las versiones de nuestra aplicación.</p>

#### Conventional Commits

<p align = justify>- Seguiremos las convenciones de commits basadas en "Conventional Commits 1.0.0". Se debe seguir la siguiente estructura para un commit:</p>

```plaintext
git commit -m "<type> (optional scope) <title>" -m "<description>"
  <type> = feat | fix | docs | style | refactor | test | chore
  <title> = 50 caracteres máximo
  <description> = 72 caracteres máximo
```

- Types:
  - Add: se usará para indicar que se añadieron archivos o carpetas.
  - Fix: este tipo de commit se utilizará para la confirmación de una corrección de un error en el código.
  - Feat: este tipo de commit se utilizará para la confirmación de que se ha añadido una nueva funcionalidad.
  - Test: se usará para indicar que se añadieron archivos test.

#### Arquitectura de Vue(convenciones)

<p align = justify>- Para la arquitectura de Vue, se seguirá la siguiente estructura:</p>

```plaintext
src
├── assets
│   ├── css
│   ├── fonts
│   ├── img
│   └── js
├── components
│   ├── common
│   ├── layout
│   └── views
├── router
├── store
├── utils
└── views
```

- **assets**: contiene los recursos estáticos como imágenes, fuentes y archivos CSS.
- **components**: contiene los componentes de la aplicación.
- **router**: contiene los archivos de configuración de las rutas.
- **store**: contiene los archivos de configuración de Vuex.
- **utils**: contiene los archivos de configuración de la aplicación.
- **views**: contiene las vistas de la aplicación.

##### 7.1.4. Software Deployment Configuration

<p align = justify>Para el despliegue de nuestra plataforma, tenemos los siguientes productos.</p>

#### Landing Page

<p align = justify>Para el despliegue del landing page hemos utilizado las siguientes herramientas:</p>

- **Git**: Para manejar las versiones del código de la Landing Page.
- **GitHub**: Para almacenar el proyecto y permitir la colaboración en la codificación.
- **GitFlow**: Para controlar y visualizar el flujo de trabajo del equipo.
- **Trello**: Para dividir las tareas y documentar el sprint.

#### Despliegue

<p align = justify> Para el despliegue de nuestra plataforma, tenemos los siguientes productos.</p>

- Landing Page

<p align = justify> Para el despliegue del landing page hemos utilizado herramientas como:</p>

- **Git:** Para manejar las versiones del código de la Landing Page.
- **GitHub:** Para almacenar el proyecto y poder codificarlo colaborativamente.
- **GitFlow:** Para controlar y visualizar el flujo de trabajo del equipo.
- **Trello:** Para poder dividirnos las tareas a realizar para la documentación del sprint

<p align = justify>Para desplegar el landing page se ha utilizado la herramienta Page de GitHub que nos permitió generar un enlace con todas las características que la rama master contiene. Por otro lado, si quieres desplegarlo de manera remota a partir del repositorio del GitHub, puedes clonar nuestro proyecto con: git clone, en el git local.</p>

<table>
    <thead>
        <tr>
            <th>Backend</th>
            <th><a href="https://github.com/Arquitecturas-De-Software-Emergente/ModelHouseV2.git">https://github.com/Arquitecturas-De-Software-Emergente/ModelHouseV2.git</a></th>
        </tr>
        <tr>
            <th>Frontend</th>
            <th><a href="https://github.com/Arquitecturas-De-Software-Emergente/ModelHouseV1.git">https://github.com/Arquitecturas-De-Software-Emergente/ModelHouseV1.git</a></th>
        </tr>
        <tr>
            <th>Lading Page</th>
            <th><a href="https://github.com/Arquitecturas-De-Software-Emergente/LandingPage.git">https://github.com/Arquitecturas-De-Software-Emergente/LandingPage.git</a>
            </th>
        </tr>
        <tr>
            <th>Mobile</th>
            <th><a href="https://github.com/Arquitecturas-De-Software-Emergente/ModelHouseMovil.git">https://github.com/Arquitecturas-De-Software-Emergente/ModelHouseMovil.git</a></th>
        </tr>
    </thead>
</table>

#### 7.2. Solution Implementation

##### 7.2.1. Sprint 1

Durante la reunión de Sprint Planning 1 se acordó que el equipo se enfocara en lograr los siguientes objetivos clave: lanzar la primera versión de nuestro Landing Page, desarrollar un producto mínimo viable de nuestra plataforma que incluya sus características esenciales, lo cual implica el despliegue inicial de las versiones frontend y backend. Nos concentraremos en desarrollar las funcionalidades para los usuarios usuarios y empresas.

###### 7.2.1.1. Sprint Planning 1

| Sprint #                        | 1                                                                                                             |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| Sprint Planning Background      |                                                                                                               |
| Date                            | 04/10/2023                                                                                                    |
| Time                            | 13:00                                                                                                         |
| Location                        | Se usó la plataforma Discord                                                                                  |
| Prepared by                     | Miguel Garcia                                                                                                 |
| Attendees (to planning meeting) | Diego Porta, Luis Li y Samuel Maucille                                                                        |
| Sprint Review Summary           | Se revisaron los puntos a mejorar y lo que había que avanzar en con respecto al desarrollo de las plataformas |

###### 7.2.1.2. Sprint Backlog 1

| Sprint 1 | User Story | Work - item / Task            | ID     | Title                                            | Description                                                                   | Estimation (Hours) | Assigned To      | Status |
| -------- | ---------- | ----------------------------- | ------ | ------------------------------------------------ | ----------------------------------------------------------------------------- | ------------------ | ---------------- | ------ |
|          | US02       | Registro en la aplicación     | Task01 | Creación de la entidad, User                     | Se creará la capa de persistencia, servicios y controlador de la entidad User | 1h                 | Luis Li          | To do  |
|          | HU03       | Publicar empresa              | WI03   | Publicación y creación de empresas               | Se permite crear un perfil de empresa                                         | 3H                 | Diego Porta      | Done   |
|          | HU04       | Editar información de empresa | WI04   | Se permite editar información del perfil empresa | El usuario empresa puede editar su información                                | 3H                 | Miguel García    | To do  |
|          | HU05       | Crear cuenta como cliente     | WI05   | Register para cliente                            | El cliente puede crear su cuenta en la aplicación                             | 4H                 | Jasmin Pomasonco | Done   |
|          | US14       | Editar perfil                 | Task01 | Añadir la función para editar los datos          | Se implementará la funcionalidad para editar los datos del perfil             | 1h                 | Luis Li          | To do  |

###### 7.2.1.3. Development Evidence for Sprint Review

| Repository                                                                                                              | Branch | Commit Id                                | Commit Message                                 | Committed on (Date) |
| ----------------------------------------------------------------------------------------------------------------------- | ------ | ---------------------------------------- | ---------------------------------------------- | ------------------- |
| [Arquitecturas-De-Software-Emergente/ModelHouseV1](https://github.com/Arquitecturas-De-Software-Emergente/ModelHouseV1) | main   | 64b38cbaf292294147e44f6fb9ed323718f14600 | Merge pull request #8 from Model-House/develop | 05/05/2023          |
| [Arquitecturas-De-Software-Emergente/ModelHouseV2](https://github.com/Arquitecturas-De-Software-Emergente/ModelHouseV2) | main   | 5bcc5b602d412d2d9df190269725a5ca71b5879a | Merge pull request #4 from Model-House/develop | 05/05/2023          |
| [Arquitecturas-De-Software-Emergente/LandingPage](https://github.com/Arquitecturas-De-Software-Emergente/LandingPage)   | main   | 5bcc5b602d412d2d9df190269725a5ca71b5879a | Merge pull request #4 from Model-House/develop | 05/05/2023          |

###### 7.2.1.4. Testing Suite Evidence for Sprint Review

<div style="text-align: justify; align-items: center">
<table>
    <thead>
        <tr>
            <th>Repository</th>
            <th>Branch</th>
            <th>Commit Id</th>
            <th>Commit Mesagge Body</th>
            <th>Commited on (Date)</th>
        </tr>
        <tr>
            <th>
                <a href="https://github.com/Arquitecturas-De-Software-Emergente/ModelHouseV2">https://github.com/Arquitecturas-De-Software-Emergente/ModelHouseV2</a>
            </th>
            <th>main</th>
            <th>c8f4600a4fbee7f2b25f221bd7c1ccc6234b5357</th>
            <th>Merge branch 'master' of https://github.com/Arquitecturas-De-Software-Emergente/ModelHouseV2</th>
            <th>03/11/2023</th>
        </tr>
        <tr>
            <th>
                <a href="https://github.com/Arquitecturas-De-Software-Emergente/ModelHouseV1">https://github.com/Arquitecturas-De-Software-Emergente/ModelHouseV1</a>
            </th>
            <th>main</th>
            <th>ce58a230fd6667022c3f4a677b1274b96a74774b</th>
            <th>feat: added package-lock json</th>
            <th>03/11/2023</th>
        </tr>
    </thead>
</table>
</div>

###### 7.2.1.5. Execution Evidence for Sprint Review.

<div style="text-align: justify; align-items: center">
    <b>Security:</b><br>
    <center>
        <img align = middle src = "../images/Sec1.png">
    </center><br>
    <center>
        <img align = middle src = "../images/Sec2.png">
    </center><br>
    <center>
        <img align = middle src = "../images/Sec3.png">
    </center><br>
    <center>
        <img align = middle src = "../images/Sec4.png">
    </center><br>
    <b>Service Management:</b><br>
    <center>
        <img align = middle src = "../images/SM1.png">
    </center><br>
    <center>
        <img align = middle src = "../images/SM2.png">
    </center><br>
    <center>
        <img align = middle src = "../images/SM3.png">
    </center><br>
    <b>Subscription Payment:</b><br>
    <center>
        <img align = middle src = "../images/SP1.png">
    </center><br>
    <center>
        <img align = middle src = "../images/SP2.png">
    </center><br>
    <b>Mobile app:</b><br>
    <center>
        <img align = middle src = "../images/Movil1.jpeg">
    </center><br>
    <center>
        <img align = middle src = "../images/Movil2.jpeg">
    </center><br>
    <center>
        <img align = middle src = "../images/Movil3.jpeg">
    </center><br>
    <b>Web app:</b><br>
    <center>
        <img align = middle src = "../images/Web1.png">
    </center><br>
    <center>
        <img align = middle src = "../images/Web2.png">
    </center><br>
    <center>
        <img align = middle src = "../images/Web3.png">
    </center><br>
    <center>
        <img align = middle src = "../images/Web4.png">
    </center><br>
    <center>
        <img align = middle src = "../images/Web5.png">
    </center><br>
    <center>
        <img align = middle src = "../images/Web6.png">
    </center><br>
    <center>
        <img align = middle src = "../images/Web7.png">
    </center><br>
    <center>
        <img align = middle src = "../images/Web8.png">
    </center><br>
    <center>
        <img align = middle src = "../images/Web9.png">
    </center><br>
    <center>
        <img align = middle src = "../images/Web10.png">
    </center><br>
    <center>
        <img align = middle src = "../images/Web11.png">
    </center><br>
    <center>
        <img align = middle src = "../images/Web12.png">
    </center><br>
    <center>
        <img align = middle src = "../images/Web13.png">
    </center><br>
    <center>
        <img align = middle src = "../images/Web14.png">
    </center><br>
    <center>
        <img align = middle src = "../images/Web15.png">
    </center><br>
</div>

###### 7.2.1.6. Services Documentation Evidence for Sprint Review

<div style="text-align: justify; align-items: center">
    <p>Entre ellos el core principal de negocio son los orders que son las solicitudes de servicio de remodelación del cliente aceptadas y los projects son los proyectos mostrados en su información de perfil detallada por parte de las empresas para captar la atención de sus clientes potenciales.</p><br>
    <center>
        <img align = middle src = "../images/SM1.png">
    </center><br>
    <center>
        <img align = middle src = "../images/SM2.png">
    </center><br>
    <center>
        <img align = middle src = "../images/SM3.png">
    </center><br>
</div>

###### 7.2.1.7. Software Deployment Evidence for Sprint Review

Para el despliegue se utilizó una máquina virtual para su persistencia considerando una arquitectura modular. También se ha desarrollado el frotend del web y móvil.

## Despliegue del backend:

- http://modelhouse0.westus3.cloudapp.azure.com:8080/security/swagger-ui/index.html#/
- http://modelhouse0.westus3.cloudapp.azure.com:8081/service-management/swagger-ui/index.html#/
- http://modelhouse0.westus3.cloudapp.azure.com:8082/subscription-payment/swagger-ui/index.html#/

## Despliegue del frontend web:

- https://kaleidoscopic-bublanina-08fd5d.netlify.app

## Despliegue del frontend móvil:

- https://drive.google.com/file/d/1nR_UX8ezpHOfDGaK2Tb7lVoBrTcrIgl0/view?usp=sharing

## Despliegue del landing page:

https://arquitecturas-de-software-emergente.github.io/LandingPage/

##### 7.1.8.Team Collaboration Insights during Sprint

## Networking del backend:

<p>
    <center>
        <img align = middle src = "../images/network-backend.png">
    </center>
</p>

## Networking del frontend web:

<p>
    <center>
        <img align = middle src = "../images/network-frontend-web.png">
    </center>
</p>

## Networking del frontend móvil:

<p>
    <center>
        <img align = middle src = "../images/network-frontend-movil.png">
    </center>
</p>

##### 7.2.2. Sprint 2

Durante la reunión de Sprint Planning 2, se estableció como prioridad para el equipo la consecución de los siguientes hitos clave: culminar el lanzamiento de las versiones definitivas de nuestro Landing Page y aplicación móvil. Simultáneamente, se acordó la creación de un producto mínimo viable de nuestra plataforma, abarcando sus funcionalidades esenciales y culminando con la implementación final tanto del frontend como del backend. El enfoque principal se centrará en el desarrollo de características dirigidas tanto a usuarios individuales como a empresas, complementado con mejoras en los estilos del conjunto.

###### 7.2.2.1. Sprint Planning 2.

| Sprint #                        | 2                                                                                                             |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| Sprint Planning Background      |                                                                                                               |
| Date                            | 16/11/2023                                                                                                    |
| Time                            | 20:00                                                                                                         |
| Location                        | Se usó la plataforma Discord                                                                                  |
| Prepared by                     | Miguel Garcia                                                                                                 |
| Attendees (to planning meeting) | Diego Porta, Luis Li, Jasmin Pomasoncco ,Samuel Maucille y Diego De La Flor                                   |
| Sprint Review Summary           | Se revisaron los puntos a mejorar y lo que había que avanzar en con respecto al desarrollo de las plataformas |

###### 7.2.2.2. Sprint Backlog 2.

| Sprint 2 | User Story | Work - item / Task                                             | ID     | Title                                            | Description                                                                   | Estimation (Hours) | Assigned To      | Status |
| -------- |------------|----------------------------------------------------------------|--------|--------------------------------------------------| ----------------------------------------------------------------------------- |--------------------|------------------| ------ |
|          | US02       | Registro en la aplicación                                      | Task01 | Creación de la entidad, User                     | Se creará la capa de persistencia, servicios y controlador de la entidad User | 1h                 | Luis Li          | Done   |
|          | HU03       | Publicar empresa                                               | WI03   | Publicación y creación de empresas               | Se permite crear un perfil de empresa                                         | 3H                 | Diego Porta      | Done   |
|          | HU04       | Editar información de empresa                                  | WI04   | Se permite editar información del perfil empresa | El usuario empresa puede editar su información                                | 3H                 | Miguel García    | To do  |
|          | HU05       | Crear cuenta como cliente                                      | WI05   | Register para cliente                            | El cliente puede crear su cuenta en la aplicación                             | 4H                 | Jasmin Pomasonco | Done   |
|          | US14       | Editar perfil                                                  | Task01 | Añadir la función para editar los datos          | Se implementará la funcionalidad para editar los datos del perfil             | 1h                 | Luis Li          | To do  |
|          | US07       | Enviar una petición a una empresa                              | WI07   | Envío del request                                | Se implementará la funcionalidad para editar los datos del perfil             | 3h                 | Diego Porta      | Done   |
|          | US08       | Poder recibir, aceptar o denegar los pedidos de mis clientes   | WI08   | Se permite aceptar o denegar los request         | La empresa puede aceptar o denegar los request recibidos por el cliente       | 3h                 | Diego Porta      | Done   |
|          | US19       | Poder Encender y apagar el dispositivo de iluminacion de forma remota | WI09   | Encender y apagar el foco de luz                 | El dispositivo de iluminacion se enciende con la señal de encendido.<br />- El dispositivo de iluminacion se apaga con la señal de apagado       | 3h                 | Sr. Li           | Done   |
|          | US20       | Ajustar intensidad del dispositivo de iluminacion              | WI10   | Control de intensidad                 | La intensidad se ajusta en un rango específico.<br />- Cambios de intensidad se reflejan inmediatamente.| 8h                 | Sr. Li           | Done   |

###### 7.2.2.3. Development Evidence for Sprint Review.

| Repository                                                                                                                    | Branch   | Commit Id                                | Commit Message                                                 | Committed on (Date) |
| ----------------------------------------------------------------------------------------------------------------------------- | -------- | ---------------------------------------- | -------------------------------------------------------------- | ------------------- |
| [Arquitecturas-De-Software-Emergente/ModelHouseV1](https://github.com/Arquitecturas-De-Software-Emergente/ModelHouseV1)       | develop  | b2411b10c23d8419099fd2e9214bd6f13e8d3c16 | Update business card dimensions                                | 17/11/2023          |
| [Arquitecturas-De-Software-Emergente/ModelHouseV2](https://github.com/Arquitecturas-De-Software-Emergente/ModelHouseV2)       | develop  | 8fca93d9c6f6d6e8a402f82e771cf3aebfcf0bc6 | feat: Update service in security and service management module | 17/11/2023          |
| [Arquitecturas-De-Software-Emergente/LandingPage](https://github.com/Arquitecturas-De-Software-Emergente/LandingPage)         | gh-pages | 647ce7643beef70348e205ff0baf3e66c420fff9 | feat: Videos added                                             | 24/10/2023          |
| [Arquitecturas-De-Software-Emergente/ModelHouseMovil](https://github.com/Arquitecturas-De-Software-Emergente/ModelHouseMovil) | develop  | 51d1cc9974ad4ee9bd0c9329194647b0dc98e821 | feat: Update service in security and service management module | 24/10/2023          |

###### 7.2.2.4. Testing Suite Evidence for Sprint Review.

<div style="text-align: justify; align-items: center">
    <b>Security:</b><br>
    <center>
        <img align = middle src = "../images/Sec1.png">
    </center><br>
    <center>
        <img align = middle src = "../images/Sec2.png">
    </center><br>
    <center>
        <img align = middle src = "../images/Sec3.png">
    </center><br>
    <center>
        <img align = middle src = "../images/Sec4.png">
    </center><br>
    <b>Service Management:</b><br>
    <center>
        <img align = middle src = "../images/SM1.png">
    </center><br>
    <center>
        <img align = middle src = "../images/SM2.png">
    </center><br>
    <center>
        <img align = middle src = "../images/SM3.png">
    </center><br>
    <b>Subscription Payment:</b><br>
    <center>
        <img align = middle src = "../images/SP1.png">
    </center><br>
    <center>
        <img align = middle src = "../images/SP2.png">
    </center><br>
    <b>Mobile app:</b>
    <br>
    <center>
        <img align = middle src = "../images/Movil1.jpeg">
    </center><br>
    <center>
        <img align = middle src = "../images/Movil2.png">
    </center><br>
    <center>
        <img align = middle src = "../images/Movil3.png">
    </center><br>
    <center>
        <img align = middle src = "../images/Movil4.jpeg">
    </center><br>
    <center>
        <img align = middle src = "../images/Movil5.jpeg">
    </center><br>
    <center>
        <img align = middle src = "../images/Movil6.jpeg">
    </center><br>
    <center>
        <img align = middle src = "../images/Movil7.jpeg">
    </center><br>
    <center>
        <img align = middle src = "../images/Movil8.jpeg">
    </center><br>
    <center>
        <img align = middle src = "../images/Movil9.jpeg">
    </center><br>
    <center>
        <img align = middle src = "../images/Movil10.jpeg">
    </center><br>
    <center>
        <img align = middle src = "../images/Movil11.jpeg">
    </center><br>
    <center>
        <img align = middle src = "../images/Movil12.jpeg">
    </center><br>
    <center>
        <img align = middle src = "../images/Movil13.jpeg">
    </center><br>
    <center>
        <img align = middle src = "../images/Movil14.jpeg">
    </center><br>
    <center>
        <img align = middle src = "../images/Movil15.jpeg">
    </center><br>
    <center>
        <img align = middle src = "../images/Movil16.jpeg">
    </center><br>
    <center>
        <img align = middle src = "../images/Movil17.jpeg">
    </center><br>
    <center>
        <img align = middle src = "../images/Movil18.jpeg">
    </center><br>
    <center>
        <img align = middle src = "../images/Movil19.jpeg">
    </center><br>
    <center>
        <img align = middle src = "../images/Movil20.jpeg">
    </center><br>
    <center>
        <img align = middle src = "../images/Movil21.jpeg">
    </center><br>
    <center>
        <img align = middle src = "../images/Movil22.jpeg">
    </center><br>
    <br>
    <b>Web app:</b><br>
    <center>
        <img align = middle src = "../images/web_update/1.png">
    </center><br>
    <center>
        <img align = middle src = "../images/web_update/2.png">
    </center><br>
    <center>
        <img align = middle src = "../images/web_update/3.png">
    </center><br>
    <center>
        <img align = middle src = "../images/web_update/4.png">
    </center><br>
    <center>
        <img align = middle src = "../images/web_update/5.png">
    </center><br>
    <center>
        <img align = middle src = "../images/web_update/6.png">
    </center><br>
    <center>
        <img align = middle src = "../images/web_update/7.png">
    </center><br>
    <center>
        <img align = middle src = "../images/web_update/8.png">
    </center><br>
    <center>
        <img align = middle src = "../images/web_update/9.png">
    </center><br>
    <center>
        <img align = middle src = "../images/web_update/10.png">
    </center><br>
    <center>
        <img align = middle src = "../images/web_update/11.png">
    </center><br>
    <center>
        <img align = middle src = "../images/web_update/12.png">
    </center><br>
    <center>
        <img align = middle src = "../images/web_update/13.png">
    </center><br>
    <center>
        <img align = middle src = "../images/web_update/14.png">
    </center><br>
    <center>
        <img align = middle src = "../images/web_update/15.png">
    </center><br>
    <center>
        <img align = middle src = "../images/web_update/16.png">
    </center><br>
    <center>
        <img align = middle src = "../images/web_update/17.png">
    </center><br>
    <center>
        <img align = middle src = "../images/web_update/18.png">
    </center><br>
    

</div>

###### 7.2.2.5. Execution Evidence for Sprint Review.

<div style="text-align: justify; align-items: center">
    <b>Security:</b><br>
    <center>
        <img align = middle src = "../images/Sec1.png">
    </center><br>
    <center>
        <img align = middle src = "../images/Sec2.png">
    </center><br>
    <center>
        <img align = middle src = "../images/Sec3.png">
    </center><br>
    <center>
        <img align = middle src = "../images/Sec4.png">
    </center><br>
    <b>Service Management:</b><br>
    <center>
        <img align = middle src = "../images/SM1.png">
    </center><br>
    <center>
        <img align = middle src = "../images/SM2.png">
    </center><br>
    <center>
        <img align = middle src = "../images/SM3.png">
    </center><br>
    <b>Subscription Payment:</b><br>
    <center>
        <img align = middle src = "../images/SP1.png">
    </center><br>
    <center>
        <img align = middle src = "../images/SP2.png">
    </center><br>
</div>

###### 7.2.2.6. Services Documentation Evidence for Sprint Review.

<div style="text-align: justify; align-items: center">
    <p>Entre ellos el core principal de negocio son los orders que son las solicitudes de servicio de remodelación del cliente aceptadas y los projects son los proyectos mostrados en su información de perfil detallada por parte de las empresas para captar la atención de sus clientes potenciales.</p><br>
    <center>
        <img align = middle src = "../images/SM1.png">
    </center><br>
    <center>
        <img align = middle src = "../images/SM2.png">
    </center><br>
    <center>
        <img align = middle src = "../images/SM3.png">
    </center><br>
</div>

###### 7.2.2.7. Software Deployment Evidence for Sprint Review.

<p align = justify>Para el despliegue se utilizó una máquina virtual para su persistencia considerando una arquitectura modular. También se ha desarrollado el frotend del web y móvil.

###### 7.2.2.8. Team Collaboration Insights during Sprint.

## Networking del backend:

<p>
    <center>
        <img align = middle src = "../images/network-backend(2).png">
    </center>
</p>

## Networking del frontend web:

<p>
    <center>
        <img align = middle src = "../images/network-frontend-web(2).png">
    </center>
</p>

## Networking del frontend móvil:

<p>
    <center>
        <img align = middle src = "../images/network-frontend-movil(2).png">
    </center>
</p>

#### 7.3. Validation Interviews

##### 7.3.1. Diseño de Entrevistas

Las entrevistas a realizar sobre "Validation", se harán presentándole al usuario nuestra solución. Se le explicará la funcionalidad y se pedirá que use y navegue dentro de esta, para de esta manera realizar las validaciones con los usuarios. Las preguntas son las siguientes:

## Preguntas generales a la empresa:

1. ¿Cuál es la visión y el objetivo principal de la aplicación intermedia que conecta empresas de remodelación y sus clientes?
2. ¿Cuál es el alcance geográfico de su plataforma? ¿En qué regiones o países planean operar?
3. ¿Qué desafíos específicos enfrenta su empresa en la industria de remodelación que espera resolver con esta aplicación?
4. ¿Cuál es su modelo de negocio para esta plataforma? ¿Cómo planean monetizarla?
5. ¿Qué tecnologías o frameworks específicos se utilizan actualmente en el desarrollo de la aplicación?

## Preguntas adicionales sobre el proyecto para la empresa:

1. ¿Cuál es su enfoque en cuanto a la escalabilidad de la aplicación? ¿Esperan un crecimiento significativo en el número de usuarios?
2. ¿Cómo se gestionará la retroalimentación de los usuarios y las posibles mejoras en la aplicación una vez que esté en funcionamiento?
3. ¿Tienen algún requisito específico en cuanto a la velocidad y rendimiento de la aplicación, especialmente en dispositivos móviles?
4. ¿Cuál es su estrategia de respaldo y recuperación de datos en caso de fallos del sistema o pérdida de información crítica?
5. ¿Tienen consideraciones específicas en cuanto a la compatibilidad con múltiples navegadores y dispositivos móviles?
6. ¿Qué medidas se tomarán para garantizar la igualdad de oportunidades para las empresas de remodelación en su plataforma?
7. ¿Tienen algún requisito de cumplimiento normativo o legal que debamos tener en cuenta en el desarrollo de la aplicación?
8. ¿Cuál es la estrategia para garantizar la calidad y la prueba de la aplicación antes de su lanzamiento?
9. ¿Cuáles son las expectativas en cuanto al soporte técnico y el mantenimiento continuo de la aplicación?
10. ¿Cómo planean mantenerse al tanto de las tendencias tecnológicas y las necesidades cambiantes de los usuarios a lo largo del tiempo?

## Preguntas generales al cliente:

1. ¿Cuál es el motivo principal de buscar una aplicación intermediaria para conectarse con empresas de remodelación?
2. ¿Qué características o funcionalidades específicas esperas que tenga esta aplicación?
3. ¿Tienes alguna preferencia en cuanto a la plataforma móvil (iOS, Android) en la que debería estar disponible la aplicación?
4. ¿Qué tipo de presupuesto tienes disponible para este proyecto?
5. ¿Tienes algún plazo específico en mente para tener la aplicación en funcionamiento?

## Preguntas adicionales sobre el proyecto para el cliente:

1. ¿Tienes alguna preferencia en cuanto a la integración de funciones de geolocalización o mapas para encontrar empresas de remodelación cercanas?
2. ¿Qué tipo de información te gustaría ver en los perfiles de las empresas de remodelación dentro de la aplicación?
3. ¿Tienes algún requisito específico en cuanto a la capacidad de recibir y comparar cotizaciones de diferentes empresas de remodelación?
4. ¿Cómo te gustaría que se gestionara el proceso de pago y facturación con las empresas de remodelación?
5. ¿Tienes preferencias en cuanto a la posibilidad de calificar y dejar reseñas sobre las empresas de remodelación?
6. ¿Qué tipo de notificaciones o alertas te gustaría recibir de la aplicación, si es que alguna?
7. ¿Tienes algún requisito en cuanto a la comunicación y mensajería entre los clientes y las empresas de remodelación?
8. ¿Qué información personal estás dispuesto a compartir en la aplicación para recibir servicios de remodelación?
9. ¿Cómo te gustaría que se gestionen las citas o programaciones de trabajos con las empresas de remodelación?
10. ¿Tienes alguna preferencia en cuanto a la forma en que se autenticarán y protegerán tus datos en la aplicación?

##### 7.3.2. Registro de Entrevistas

### 2.2.2 Registro de entrevistas

**Usuario cliente**

**Entrevista 1**

<table>
    <tr>
        <th>Nombre</th>
        <th>Apellido</th>
        <th>Edad</th>
        <th>Distrito</th>
    </tr>
    <tr>
        <td>Eduardo</td>
        <td>-</td>
        <td>25 años</td>
        <td>El Agustino</td>
    </tr>
    <tr>
        <td colspan="4" align="center"><img src="../images/Entrevista1_jasmin.png"></td>
    </tr>
    <tr>
        <td colspan="4">URL: <a href="https://www.youtube.com/watch?v=h5nkNlMRuy4">https://www.youtube.com/watch?v=h5nkNlMRuy4</a></td>
    </tr>
    <tr> <td colspan="4" align="justify">
      Eduardo en remodelar de inmueble que recien se encuentra conociendo en el mercado, al mostrar la aplicación el nos comenta que la aplicación deber ser mas vistosa y que debe contener más imágenes, ademas que se deben clasificar los proyecto porque tan grande puede ser este. 
También nos recomienda que debe funcionar de manera fluida que con alertas que le indique cuál es el uso de cada funcionalidad.
</td> </tr>
</table>

**Entrevista 2**

<table>
    <tr>
        <th>Nombre</th>
        <th>Apellido</th>
        <th>Edad</th>
        <th>Distrito</th>
    </tr>
    <tr>
        <td>Daniel</td>
        <td> - </td>
        <td>26 años</td>
        <td>San Borja</td>
    </tr>
    <tr>
        <td colspan="4" align="center"><img src="../images/EntrevistaLuis1.png"></td>
    </tr>
    <tr>
        <td colspan="4">URL: <a href="https://youtu.be/EkHPd9EtGG0">https://youtu.be/EkHPd9EtGG0</a></td>
    </tr>
    <tr> <td colspan="4" align="justify">
      Daniel una persona que esta interesada en remodelar su hogar, al mostrar la aplicación él nos comenta que la aplicación deber ser mas vistosa y que debe contener más imágenes, ademas que se deben clasificar los proyecto porque tan grande puede ser este. También nos recomienda que debe funcionar de manera fluida que con alertas que le indique cuál es el uso de cada funcionalidad.
</td> </tr>
</table>

# 7.3.3. Evaluaciones según heurísticas

# Evaluación de Heurísticas y Principios de UX

## Usabilidad, Diseño Inclusivo, y Arquitectura de la Información

_Carrera:_ Ingeniería de Software

_Curso:_ Arquitectura de Software Emergentes

_Profesores:_ Todos

_Sitio o App a Evaluar:_ ModelHouse

### Tareas a Evaluar

1. Botón de 'Deshacer Requests' para retroceder acciones
2. Falta de opción clara para eliminar la cuenta del usuario
3. Atajos de teclado y opciones avanzadas para eficiencia
4. Acceso a tutoriales, preguntas frecuentes y chat en vivo
5. Retroalimentación clara al completar acciones importantes
6. Carga eficiente y respuesta rápida
<table>
  <tr>
    <th>Número de Tarea</th>
    <th>Problema</th>
    <th>Escala de Severidad</th>
    <th>Heurística/Principio Violado</th>
  </tr>
  <tr>
    <td>1</td>
    <td>Botón de 'Deshacer Requests' para retroceder acciones</td>
    <td>3</td>
    <td>Control y libertad del usuario</td>
  </tr>
  <tr>
    <td>2</td>
    <td>Falta de opción clara para eliminar la cuenta del usuario</td>
    <td>4</td>
    <td>Prevención de Errores</td>
  </tr>
  <tr>
    <td>3</td>
    <td>Atajos de teclado y opciones avanzadas para eficiencia</td>
    <td>2</td>
    <td>Flexibilidad y eficiencia de uso</td>
  </tr>
  <tr>
    <td>4</td>
    <td>Acceso a tutoriales, preguntas frecuentes y chat en vivo</td>
    <td>2</td>
    <td>Ayuda y documentación</td>
  </tr>
  <tr>
    <td>5</td>
    <td>Retroalimentación clara al completar acciones importantes</td>
    <td>1</td>
    <td>Feedback de confirmación</td>
  </tr>
  <tr>
    <td>6</td>
    <td>Carga eficiente y respuesta rápida</td>
    <td>1</td>
    <td>Eficiencia en la carga y rendimiento</td>
</tr>
</table>

# Control y libertad del usuario

## PROBLEMA #1:

- _Severidad:_ Moderada
- _Usability:_ La aplicación proporciona un botón de 'Deshacer Requests', lo que permite a los usuarios retroceder en su navegación. Sin embargo, su visibilidad y ubicación pueden ser mejoradas para hacerlo más fácilmente accesible.
- _Problema:_ El botón de 'Deshacer Requests' existe, pero su ubicación y visibilidad no son óptimas, lo que podría dificultar que los usuarios lo encuentren rápidamente.

## Prevención de Errores

## PROBLEMA #2:

- _Severidad:_ Alta
- _Usability:_ La plataforma no proporciona una forma clara y sencilla de eliminar una cuenta de usuario, lo que puede dar lugar a errores y frustración por parte de los usuarios que desean dar de baja su cuenta.
- _Problema:_ La falta de una opción clara para eliminar la cuenta de usuario puede resultar en errores y confusión para los usuarios que intentan realizar esta acción.

## Flexibilidad y eficiencia de uso

## PROBLEMA #3:

- _Severidad:_ Moderada
- _Usability:_ La aplicación web no proporciona atajos de teclado y opciones avanzadas para mejorar la eficiencia de uso, lo que podría dificultar la experiencia de usuarios experimentados.
- _Problema:_ La falta de atajos de teclado y opciones avanzadas podría reducir la eficiencia de uso para usuarios experimentados.

## Ayuda y documentación

## PROBLEMA #4:

- _Severidad:_ Baja
- _Usability:_ La aplicación web ofrece acceso a tutoriales, preguntas frecuentes y chat en vivo, lo que es positivo. Sin embargo, la visibilidad y la navegación de estos recursos podrían mejorarse para una mejor accesibilidad.
- _Problema:_ Los recursos de ayuda y documentación existen, pero su visibilidad y navegación pueden no ser óptimas, lo que podría dificultar que los usuarios encuentren la asistencia que necesitan.

## Feedback de confirmación

## PROBLEMA #5:

- _Severidad:_ Moderada
- _Usability:_ La aplicación proporciona retroalimentación clara al completar acciones importantes, lo que es positivo. Sin embargo, esta retroalimentación podría ser más destacada y visible.
- _Problema:_ La retroalimentación al completar acciones importantes es proporcionada, pero su visibilidad podría mejorarse para asegurarse de que los usuarios comprendan que la acción se ha realizado con éxito.

## Eficiencia en la carga y rendimiento

## PROBLEMA #6:

- _Severidad:_ Alta
- _Usability:_ La aplicación web no carga de manera eficiente ni responde rápidamente, lo que puede afectar negativamente la usabilidad.
- _Problema:_ Los tiempos de carga largos y los retrasos en la respuesta de la aplicación afectan negativamente la usabilidad, lo que puede resultar en una experiencia frustrante para los usuarios.

##### 7.4. Video About-the-Product

Link: https://youtu.be/EMHohbwrXDw