## Capítulo IV: Strategic-Level Software Design

Este capítulo documenta las decisiones estratégicas del diseño de software para FitSense. Aplicamos Attribute-Driven Design (ADD) bajo un enfoque Domain-Driven Design (DDD) para garantizar que la arquitectura soporte los objetivos de negocio (p. ej. Goal 4: 4.5 estrellas). Presentamos: propósito del diseño, entradas, drivers arquitectónicos, decisiones de diseño clave, escenarios de calidad (Quality Attribute Scenarios), identificación de bounded contexts y su mapeo, y las vistas arquitectónicas iniciales usando C4 Model (nivel Context y Container).

## 4.1. Strategic-Level Attribute-Driven Design

### 4.1.1. Design Purpose

El propósito del proceso de diseño arquitectónico para FitSense es crear una solución de software robusta, escalable y centrada en el usuario que aborde directamente las problemáticas identificadas en el mercado de aplicaciones de fitness.

### 4.1.2. Attribute-Driven Design Inputs

Esta sección documenta los insumos que guiarán el diseño arquitectónico de FitSense utilizando el enfoque Attribute-Driven Design (ADD). Incluye las funcionalidades clave (Primary User Stories), los escenarios de atributos de calidad que condicionan decisiones de diseño, y las restricciones impuestas por el negocio o el entorno tecnológico.

#### 4.1.2.1. Primary Functionality (Primary User Stories)

Las siguientes épicas y user stories fueron priorizadas por su alto impacto en la arquitectura del sistema. Se centran en los componentes críticos: adquisición de usuarios, personalización con IA, seguimiento diario, dashboard de métricas, notificaciones inteligentes y backend API.

<table>
<thead>
<tr>
<th>Epic / User Story ID</th>
<th>Título</th>
<th>Descripción</th>
<th>Criterios de Aceptación (resumen)</th>
<th>Relacionado con (Epic ID)</th>
</tr>
</thead>
<tbody>
<tr>
<td>EP01</td>
<td>Presencia Digital y Adquisición de Usuarios</td>
<td>Landing page y marketing para captar y convertir visitantes en usuarios activos.</td>
<td>Debe tener secciones de hero, beneficios, planes y CTA de registro funcional.</td>
<td>—</td>
</tr>
<tr>
<td>US-04</td>
<td>Registro desde landing page</td>
<td>Permitir que los visitantes se registren desde la landing.</td>
<td>Redirige a la app móvil, crea cuenta y comienza onboarding.</td>
<td>EP01</td>
</tr>
<tr>
<td>EP02</td>
<td>Onboarding y Configuración del Perfil Inicial</td>
<td>Registro y configuración rápida del perfil para crear un plan personalizado.</td>
<td>Captura edad, peso, altura, objetivos, nivel y equipamiento de forma segura.</td>
<td>—</td>
</tr>
<tr>
<td>US-05</td>
<td>Registro rápido en app</td>
<td>Registro con email, Google o Apple.</td>
<td>Crear cuenta en 201 y redirigir a onboarding.</td>
<td>EP02</td>
</tr>
<tr>
<td>US-08</td>
<td>Configuración del perfil personal</td>
<td>Ingreso de datos físicos y validación.</td>
<td>Guarda y valida la información de forma segura.</td>
<td>EP02</td>
</tr>
<tr>
<td>US-09</td>
<td>Definición de objetivos fitness</td>
<td>Establecer metas iniciales (perder peso, ganar músculo, etc.)</td>
<td>Prioriza planes según objetivos elegidos.</td>
<td>EP02</td>
</tr>
<tr>
<td>EP03</td>
<td>Generación y Adaptación de Planes con IA</td>
<td>Creación y ajuste dinámico de planes de entrenamiento y nutrición.</td>
<td>Genera rutinas personalizadas y las adapta al progreso.</td>
<td>—</td>
</tr>
<tr>
<td>US-12</td>
<td>Generación inicial de plan personalizado</td>
<td>Generar plan completo en menos de 3 segundos.</td>
<td>Incluye ejercicios semanales y nutrición básica.</td>
<td>EP03</td>
</tr>
<tr>
<td>US-13</td>
<td>Adaptación dinámica basada en progreso</td>
<td>Ajustar automáticamente según desempeño y feedback.</td>
<td>Incrementa dificultad o recalibra al instante.</td>
<td>EP03</td>
</tr>
<tr>
<td>EP04</td>
<td>Seguimiento y Registro Diario de Actividades</td>
<td>Registro ágil de entrenos, comidas e hidratación.</td>
<td>Captura datos diarios para retroalimentar a la IA.</td>
<td>—</td>
</tr>
<tr>
<td>US-15</td>
<td>Registro rápido de entrenamientos</td>
<td>Marcar ejercicios completados en un tap.</td>
<td>Guarda fecha, hora, duración y notas.</td>
<td>EP04</td>
</tr>
<tr>
<td>US-16</td>
<td>Registro de comidas</td>
<td>Registro manual o escaneo de código de barras.</td>
<td>Registra calorías y nutrientes.</td>
<td>EP04</td>
</tr>
<tr>
<td>EP05</td>
<td>Dashboard de Progreso y Métricas Visuales</td>
<td>Visualizar evolución y progreso del usuario.</td>
<td>Mostrar peso, IMC, calorías y logros en dashboard.</td>
<td>—</td>
</tr>
<tr>
<td>US-19</td>
<td>Dashboard principal de progreso</td>
<td>Vista central de progreso.</td>
<td>Resumen semanal de métricas y logros.</td>
<td>EP05</td>
</tr>
<tr>
<td>US-22</td>
<td>Balance calórico visual</td>
<td>Mostrar calorías ingeridas vs quemadas.</td>
<td>Vista diaria y semanal con tendencias.</td>
<td>EP05</td>
</tr>
<tr>
<td>EP08</td>
<td>Notificaciones y Recordatorios Inteligentes</td>
<td>Recordatorios personalizados para mantener constancia.</td>
<td>Recordatorios de entrenamientos, hidratación y logros.</td>
<td>—</td>
</tr>
<tr>
<td>US-28</td>
<td>Recordatorios inteligentes de entrenamientos</td>
<td>Alertas adaptativas según hábitos del usuario.</td>
<td>Ajusta horarios automáticamente y respeta “no molestar”.</td>
<td>EP08</td>
</tr>
<tr>
<td>US-31</td>
<td>Personalización de notificaciones</td>
<td>Control de qué y cuándo notificar.</td>
<td>Configuración granular por tipo y horario.</td>
<td>EP08</td>
</tr>
<tr>
<td>EP09</td>
<td>Backend y API RESTful para FitSense</td>
<td>Soporte técnico para toda la lógica de negocio y datos.</td>
<td>Servicios seguros, escalables y con alta disponibilidad.</td>
<td>—</td>
</tr>
<tr>
<td>US-33</td>
<td>Crear Usuario (API)</td>
<td>Endpoint POST para registrar usuario.</td>
<td>201 con userId y token, 400 si email en uso.</td>
<td>EP09</td>
</tr>
<tr>
<td>US-37</td>
<td>Generar Plan de Entrenamiento con IA (API)</td>
<td>Generar plan según perfil.</td>
<td>201 con plan semanal, 400 si perfil incompleto.</td>
<td>EP09</td>
</tr>
<tr>
<td>US-39</td>
<td>Obtener Datos para el Dashboard</td>
<td>Endpoint para métricas históricas.</td>
<td>Devuelve peso, IMC y calorías últimos 30 días.</td>
<td>EP09</td>
</tr>
</tbody>
</table>

---

#### 4.1.2.2. Quality Attribute Scenarios

<table>
<thead>
<tr>
<th>Atributo</th>
<th>Fuente</th>
<th>Estímulo</th>
<th>Artefacto</th>
<th>Entorno</th>
<th>Respuesta</th>
<th>Medida</th>
</tr>
</thead>
<tbody>
<tr>
<td>Escalabilidad</td>
<td>Usuario concurrente</td>
<td>Se conectan 10 000 usuarios nuevos en 24h</td>
<td>API Gateway + Microservicios Backend</td>
<td>Cloud Kubernetes con autoescalado</td>
<td>Se crean nuevas réplicas automáticamente.</td>
<td>Mantener latencia &lt; 2s con 10k usuarios</td>
</tr>
<tr>
<td>Rendimiento</td>
<td>Usuario</td>
<td>Solicitud de generación de plan IA con alta concurrencia</td>
<td>Servicio de IA</td>
<td>Backend bajo carga alta</td>
<td>Genera el plan en menos de 3 segundos.</td>
<td>Tiempo de respuesta &lt; 3s</td>
</tr>
<tr>
<td>Disponibilidad</td>
<td>Usuario</td>
<td>Acceso durante mantenimiento planificado</td>
<td>Aplicación Móvil</td>
<td>Microservicios replicados</td>
<td>Usuario redirigido a instancias saludables.</td>
<td>99.9% de uptime mensual</td>
</tr>
<tr>
<td>Seguridad</td>
<td>Atacante externo</td>
<td>10 intentos de login fallidos en 1 minuto</td>
<td>Servicio de Autenticación</td>
<td>Producción</td>
<td>Bloquea cuenta y activa MFA obligatoria.</td>
<td>Bloqueo tras 5 intentos fallidos</td>
</tr>
<tr>
<td>Privacidad</td>
<td>Usuario</td>
<td>Solicitud de eliminación de cuenta y datos personales</td>
<td>Servicio de Perfiles</td>
<td>Producción</td>
<td>Elimina toda la información personal y confirma la acción.</td>
<td>100% de datos eliminados en &lt; 48h</td>
</tr>
</tbody>
</table>

---

#### 4.1.2.3. Constraints

<table>
<thead>
<tr>
<th>Technical Story ID</th>
<th>Título</th>
<th>Descripción</th>
<th>Criterios de Aceptación</th>
<th>Relacionado con (Epic ID)</th>
</tr>
</thead>
<tbody>
<tr>
<td>CT01</td>
<td>Cumplimiento con GDPR</td>
<td>Los datos deben almacenarse y procesarse cumpliendo el GDPR.</td>
<td>Anonimiza datos personales y permite eliminación total bajo solicitud del usuario.</td>
<td>EP09</td>
</tr>
</tbody>
</table>

---

### 4.1.3. Architectural Drivers Backlog

<table>
<thead>
<tr>
<th>Driver ID</th>
<th>Título de Driver</th>
<th>Descripción</th>
<th>Importancia para Stakeholders</th>
<th>Impacto en Architecture Technical Complexity</th>
</tr>
</thead>
<tbody>
<tr>
<td>FD01</td>
<td>Registro y autenticación de usuarios</td>
<td>Base para adquirir y activar usuarios.</td>
<td>Alta</td>
<td>Alta</td>
</tr>
<tr>
<td>FD02</td>
<td>Generación de planes personalizados</td>
<td>Núcleo de valor: rutinas y dietas basadas en IA.</td>
<td>Alta</td>
<td>Alta</td>
</tr>
<tr>
<td>FD03</td>
<td>Registro y seguimiento de actividades</td>
<td>Permite capturar datos de progreso para la IA.</td>
<td>Alta</td>
<td>Alta</td>
</tr>
<tr>
<td>QD01</td>
<td>Alta disponibilidad</td>
<td>Garantizar acceso continuo sin interrupciones.</td>
<td>Alta</td>
<td>Alta</td>
</tr>
<tr>
<td>QD02</td>
<td>Alto rendimiento</td>
<td>Responde rápido incluso con alta concurrencia.</td>
<td>Alta</td>
<td>Alta</td>
</tr>
<tr>
<td>QD03</td>
<td>Escalabilidad horizontal</td>
<td>Escalar automáticamente con demanda variable.</td>
<td>Alta</td>
<td>Alta</td>
</tr>
<tr>
<td>QD04</td>
<td>Protección de datos personales</td>
<td>Manejo seguro y confidencial de datos sensibles.</td>
<td>Alta</td>
<td>Media</td>
</tr>
<tr>
<td>CT01</td>
<td>Cumplimiento con GDPR</td>
<td>Restricción legal obligatoria.</td>
<td>Alta</td>
<td>Media</td>
</tr>
<tr>
<td>CT03</td>
<td>Uso de tecnologías aprobadas</td>
<td>Limita el stack tecnológico.</td>
<td>Media</td>
<td>Media</td>
</tr>
</tbody>
</table>

---

### 4.1.4. Architectural Design Decisions

<table>
<thead>
<tr>
<th>Driver ID</th>
<th>Título de Driver</th>
<th>Pattern 1: Microservicios</th>
<th></th>
<th>Pattern 2: Monolito Modular</th>
<th></th>
</tr>
</thead>
<tbody>
<tr>
<td></td>
<td></td>
<td><b>Pro:</b> Escalabilidad, despliegue independiente</td>
<td><b>Con:</b> Mayor complejidad operativa</td>
<td><b>Pro:</b> Simplicidad inicial</td>
<td><b>Con:</b> Escalabilidad limitada</td>
</tr>
<tr>
<td>FD01</td>
<td>Registro y autenticación</td>
<td>Escalabilidad horizontal</td>
<td>Más complejidad DevOps</td>
<td>Rápido de implementar</td>
<td>Riesgo de cuellos de botella</td>
</tr>
<tr>
<td>FD02</td>
<td>Generación de planes IA</td>
<td>Aislamiento de cargas IA</td>
<td>Orquestación compleja</td>
<td>Simple para prototipo</td>
<td>Mala separación de responsabilidades</td>
</tr>
</tbody>
</table>

---

### 4.1.5. Quality Attribute Scenario Refinements

### Scenario Refinement #1
- **Scenario(s):** Escalabilidad bajo carga extrema  
- **Business Goals:** Soportar el crecimiento rápido de usuarios  
- **Relevant Quality Attributes:** Escalabilidad, Disponibilidad  
- **Stimulus:** Llegan 10 000 nuevos usuarios en 24 horas  
- **Scenario Components**  
  - **Stimulus Source:** Nuevos usuarios  
  - **Environment:** Producción  
  - **Artifact:** API Gateway, microservicios backend  
  - **Response:** Autoescalado de pods y balanceo de carga automático  
  - **Response Measure:** Mantener latencia &lt;2s  
- **Questions:** ¿Cómo se gestionarán las migraciones de BD con tráfico en vivo?  
- **Issues:** Costos elevados de infraestructura

### Scenario Refinement #2
- **Scenario(s):** Protección de datos sensibles  
- **Business Goals:** Cumplir normativa y generar confianza  
- **Relevant Quality Attributes:** Seguridad, Privacidad  
- **Stimulus:** Usuario solicita la eliminación completa de su cuenta  
- **Scenario Components**  
  - **Stimulus Source:** Usuario  
  - **Environment:** Producción  
  - **Artifact:** Servicio de Perfiles  
  - **Response:** Elimina datos personales de BD y caché, y confirma por correo  
  - **Response Measure:** 100% de datos eliminados en &lt;48h  
- **Questions:** ¿Cómo asegurar que backups no retengan datos personales?  
- **Issues:** Riesgo de datos residuales en logs o backups antiguos

## Capítulo IV: Solution Software Design
## 4.2. Strategic-Level Domain-Driven Design. 
### 4.2.1. EventStorming. 

<p>Realizamos nuestro proceso de event storming a través de la herramienta Figma, donde trazamos todo el recorrido del sistema. Iniciamos con la fase inicial de Unstructured Exploration, en la cual discutimos y contrastamos nuestras ideas respecto a los eventos clave del dominio, guiándonos por las sugerencias recomendadas y centrandonos en el objetivo numero uno de nuestro proyecto. Asimismo, tomamos en cuenta diversos aspectos al elegir los eventos, tales como su importancia, recurrencia y momento de ocurrencia.<p>

🔗 [Ver Figma](https://www.figma.com/design/d79XNdidl0cHYUaA9o8zsj/Figma---Emergentes?t=GWl8L6Gfl27XnxeW-1)
<br>

**Step 1: Unstructured Exploration**

<p>Iniciamos con una exploración libre del dominio, donde cada integrante propuso eventos clave desde su perspectiva. Esta etapa nos permitió intercambiar ideas, descubrir puntos relevantes y construir una comprensión compartida del proceso. Para seleccionar los eventos, consideramos criterios como relevancia, frecuencia y temporalidad.<p>

<img src="../img/chapter-4/es_unstructuredExploration.png" alt="Unstructured Exploration" width="80%">


**Step 2: Timelines**
<p>En esta fase organizamos los eventos del dominio de forma cronológica. Esto nos permitió visualizar el flujo completo del sistema, identificar el orden natural de los eventos y comprender mejor cómo interactúan los usuarios con FitSense en el proceso de registro, generación de planes, seguimiento y mejora física.</p>

<img src="../img/chapter-4/es_timelines1.png" alt="Timelines 1" width="80%">

<img src="../img/chapter-4/es_timelines2.png" alt="Timelines 2" width="80%">

**Step 3: Pain Points**
<p>Detectamos los puntos críticos o problemáticos que enfrentan tanto los usuarios como el sistema actual. Estos incluían desde notificaciones poco visibles que podrían ser ignoradas, hasta la dificultad de generar planes realistas cuando los datos ingresados son incompletos o inconsistentes.</p>

<img src="../img/chapter-4/es_painPoints1.png" alt="Pain Points 1" width="80%">
<img src="../img/chapter-4/es_painPoints2.png" alt="Pain Points 2" width="80%">
<br>
<br>
<br>

**Step 4: Pivotal Points**
<p>Identificamos los momentos clave que marcan cambios importantes dentro del proceso, como cuando se genera un nuevo plan personalizado, cuando el usuario recibe una alerta de inactividad o cuando se detecta una mejora en las métricas físicas mediante IA. Estos puntos nos ayudaron a definir posibles mejoras de alto impacto en la experiencia de uso.</p>

<img src="../img/chapter-4/es_pivotalPoints1.png" alt="Pivotal Points 1" width="80%">
<br>
<br>
<br>

**Step 5: Commands**
<p>Aquí definimos las acciones que los usuarios o el sistema pueden ejecutar, como "Registrar Usuario", "Generar Plan de Entrenamiento", "Enviar Notificación de Hidratación" o "Subir Foto de Progreso". Cada comando representa una intención concreta que da lugar a eventos dentro de FitSense.</p>

<img src="../img/chapter-4/es_commands.png" alt="Commands 1" width="80%">
<img src="../img/chapter-4/es_commands2.png" alt="Commands 2" width="80%">
<br>
<br>
<br>

**Step 6: Policies**
<p>Establecimos las reglas de negocio que deben ejecutarse de forma automática ante ciertos eventos. Por ejemplo, si el sistema detecta inactividad por más de tres días, se activa una política que genera y envía una notificación push al usuario. O si se sube una foto de progreso, se activa una política de privacidad y de procesamiento de la imagen con IA.</p>

<img src="../img/chapter-4/es_policies1.png" alt="Policies 1" width="80%">
<img src="../img/chapter-4/es_policies2.png" alt="Policies 2" width="80%">
<br>
<br>
<br>

**Step 7: Read Models**
<p>Diseñamos los modelos de lectura que permitirán consultar el estado del usuario, como el dashboard con métricas de IMC, calorías recomendadas, gráficos de progreso semanal, historial de planes y logros sociales. Estos modelos están optimizados para ofrecer al usuario información clara, motivadora y accesible.</p>

<img src="../img/chapter-4/es_readModels.png" alt="Read Models" width="80%">
<br>
<br>
<br>

**Step 8: External Systems**
<p>Identificamos los sistemas externos que interactúan con FitSense, como servicios de autenticación (Firebase Auth), APIs de notificaciones push, motores de IA de recomendación, librerías de visualización de gráficos y APIs de visión por computadora para el análisis de imágenes. También se contemplaron integraciones con redes sociales para compartir logros.</p>

<img src="../img/chapter-4/es_externalSystems.png" alt="External Systems" width="80%">
<br>
<br>
<br>

**Step 9: Aggregates**
<p>Por último, definimos los aggregates, que representan los límites consistentes del dominio. Un ejemplo claro fue el aggregate de <b>Plan Personalizado</b>, que encapsula la lógica de generación y adaptación de planes de entrenamiento y alimentación. Otro aggregate clave fue <b>Monitoring</b>, que centraliza el seguimiento de métricas y la detección de mejoras físicas. Estos aggregates permiten mantener la coherencia del dominio y garantizar que cada área funcional de FitSense evolucione de manera independiente pero alineada.</p>

<img src="../img/chapter-4/es_aggregates.png" alt="Aggregates" width="80%">

### 4.2.2 Candidate Context Discovery. 

**Identificación de Valores del Negocio:**  
<p>Analizamos los aspectos fundamentales del negocio: la personalización de planes de ejercicio y alimentación mediante IA, el seguimiento del progreso físico con métricas de salud, la entrega de notificaciones y recordatorios oportunos, la generación de reportes y visualizaciones motivadoras, y la interacción social para compartir logros. Estos valores permiten a los usuarios entrenar de forma más eficiente, segura y personalizada, fomentando hábitos saludables y una experiencia accesible sin necesidad de un entrenador presencial.</p>

**Identificación de Funcionalidades Clave:**  
<p>A partir de estos valores, identificamos funcionalidades esenciales para el sistema:</p>

- Generación de planes de entrenamiento y alimentación personalizados mediante IA.
- Seguimiento de métricas de salud (IMC, calorías, evolución física).
- Notificaciones de recordatorio de entrenamientos e hidratación.
- Detección de inactividad y alertas para mantener la adherencia al plan.
- Análisis de imágenes con IA para estimar mejoras físicas (ej. reducción de IMC).
- Exportación de reportes de progreso en PDF/Excel.
- Visualización de gráficos y dashboards semanales.
- Gestión de cuentas y perfiles de usuarios.
- Compartir logros y resultados en redes sociales.

**Priorización de Contextos:**  
<p>La priorización de bounded contexts nos ayudó a enfocar el diseño del sistema en torno a lo que realmente sostiene el valor de FitSense. Al distinguir los núcleos del dominio, pudimos aislar lógicas críticas (como generación de planes personalizados, seguimiento de métricas y notificaciones) que deben evolucionar de forma independiente y con alta cohesión.</p>

**Contextos Identificados:**
1. Security: gestiona la autenticación, creación de cuentas y administración de perfiles de usuario. 
2. Plan: genera, personaliza y ajusta planes de ejercicio y alimentación mediante IA, incorporando el feedback del usuario.
3. Monitoring: realiza el seguimiento de métricas de salud, evolución física y análisis comparativo mediante dashboards y procesamiento de imágenes.
4. Notification: gestiona recordatorios automáticos de entrenamiento, hidratación y alertas de inactividad.
5. Social: permite al usuario compartir logros, exportar reportes y mantener interacción en redes sociales.

**Bounded Context Security**

<img src="../img/chapter-4/es_boundedContext1.png" alt="Bounded Context" width="80%">

**Bounded Context Plan**

<img src="../img/chapter-4/es_boundedContext5.png" alt="Bounded Context" width="80%">


**Bounded Context Monitoring**

<img src="../img/chapter-4/es_boundedContext4.png" alt="Bounded Context" width="80%">


**Bounded Context Notification**

<img src="../img/chapter-4/es_boundedContext3.png" alt="Bounded Context" width="80%">


**Bounded Context Social**

<img src="../img/chapter-4/es_boundedContext2.png" alt="Bounded Context" width="80%">
<br>
<br>
<br>

### **4.2.3. Domain Message Flows Modeling.** 

Estos gráfico muestra cómo el usuario interactúa con el sistema para monitorear su progreso físico. A través de la aplicación móvil, se registran datos personales y métricas de salud, que son procesados por la inteligencia artificial de FitSense. Si se detecta una desviación en el plan o un valor fuera de los rangos esperados, el sistema activa una alerta y notifica al usuario en tiempo real.

<img src="../img/chapter-4/dmf_security.png" alt="Domain Message Flow Security" width="80%">

<img src="../img/chapter-4//dmf_monitoring.png" alt="Domain Message Flow Monitoring" width="80%">

<img src="../img/chapter-4/dmf_plan.png" alt="Domain Message Flow Plan" width="80%">

<img src="../img/chapter-4/dmf_social.png" alt="Domain Message Flow Social" width="80%">

<img src="../img/chapter-4/dmf_notification.png" alt="Domain Message Flow Notification" width="80%">


### **4.2.4. Bounded Context Canvases.**
Los Bounded Context Canvases de FitSense permiten visualizar el propósito de cada contexto, sus interacciones con usuarios y sistemas externos, el lenguaje ubicuo que los define y las decisiones clave de negocio que los guían. Con ellos se asegura que cada módulo del sistema sea coherente, independiente y alineado con los objetivos de la aplicación.

<img src="../img/chapter-4/bcc_security.png" alt="Bounded Context Canvases Security" width="80%">

<img src="../img/chapter-4/bcc_monitoreo.png" alt="Bounded Context Canvases Monitoring" width="80%">

<img src="../img/chapter-4/bcc_plan.png" alt="Bounded Context Canvases Plan" width="80%">

<img src="../img/chapter-4/bcc_social.png" alt="Bounded Context Canvases Social" width="80%">

<img src="../img/chapter-4/bcc_notification.png" alt="Bounded Context Canvases Notification" width="80%">


### **4.2.5. Context Mapping**
Una vez definidos nuestros Bounded Contexts, realizamos el mapeo de sus relaciones para comprender cómo se comunican dentro del sistema de FitSense y asignar los patrones adecuados según su interacción.

– Security provee autenticación y manejo de perfiles de usuario. Es utilizado por los demás contextos, pero no depende de ninguno. Esta relación fue clasificada como Shared Kernel, ya que su lógica y entidades clave (usuarios, credenciales, perfiles) deben ser consistentes y compartidas de forma controlada.

– Plan genera y personaliza los planes de entrenamiento y alimentación. Consume datos básicos del perfil del usuario desde Security, por lo que su relación sigue el patrón Customer–Supplier.

– Monitoring realiza el seguimiento de métricas, progreso y análisis de imágenes. Este contexto depende de los planes generados en el contexto Plan (para medir adherencia y progreso), por lo que su relación aplica como Conformist, ya que adopta el lenguaje de eventos de Plan.

– Notification se encarga de la gestión de recordatorios y alertas (ej. entrenamiento pendiente, hidratación). Consume datos tanto de Monitoring (ej. detectar inactividad) como de Security (ej. configuración de usuario). Sus relaciones se clasifican como Customer–Supplier, ya que Notification depende de información expuesta por esos contextos.

– Social facilita la publicación y el compartir logros del usuario. Su interacción con Security (para validar identidad del usuario) también sigue el patrón Customer–Supplier. Además, consume métricas de Monitoring para generar contenido atractivo (ej. logros de progreso), lo que refuerza un Conformist con respecto al lenguaje de progreso definido en Monitoring.

– En algunos escenarios, la comunicación entre Plan y Monitoring también puede considerarse como Published Language, ya que ambos deben interpretar métricas y eventos de forma coherente (ej. cuando se regenera un plan porque el sistema detectó falta de adherencia).

Este mapeo nos ayuda a establecer relaciones claras entre los contextos, identificar dependencias y definir una arquitectura que mantenga separadas las responsabilidades de cada módulo en FitSense.

**Bounded Context All - Vista Completa**
    <img src="../img/chapter-4/es_allBoundedContext.png" alt="Bounded Contexts" width="800">

## 4.3. Software Architecture
### 4.3.1. Software Architecture System Landscape Diagram

El Diagrama de Paisaje del Sistema ofrece una visión panorámica de la cartera de software de la organización. Para el proyecto FitSense, este diagrama ubica nuestra plataforma en relación con los sistemas externos esenciales para su operación, como los servicios de inteligencia artificial y las APIs de redes sociales, definiendo el contexto más amplio en el que operará nuestro software.

<img src="../img/chapter-4/c4_landscapeDiagram.jpg" alt="C4 Landscape Diagram" width="800">

### 4.3.2. Software Architecture Context Level Diagrams 

El Diagrama de Contexto proporciona una vista de alto nivel del sistema FitSense. El propósito es mostrar cómo la plataforma interactúa con los usuarios y con los principales sistemas externos de los que depende, como los servicios de IA de Gpt 4o mini, las APIs de redes sociales, y los sistemas de autenticación y notificaciones.

<img src="../img/chapter-4/c4_contextDiagram.jpg" alt="C4 Context Diagram" width="800">

### 4.3.3. Software Architecture Container Level Diagrams

El Diagrama de Contenedores detalla la arquitectura interna del sistema FitSense. Representa las principales aplicaciones, servicios, bases de datos y sistemas externos que trabajan juntos para operar la plataforma. Este diagrama muestra las conexiones y el flujo de información entre cada uno de los componentes, ilustrando cómo se implementan decisiones arquitectónicas clave, como el uso de un API Gateway y la integración de la arquitectura RAG para la generación de planes de entrenamiento.

<img src="../img/chapter-4/c4_containersDiagram.jpg" alt="C4 Containers Diagram" width="800">

### 4.3.4. Software Architecture Deployment Diagrams 

El Diagrama de Despliegue muestra cómo la arquitectura del sistema FitSense se ejecuta en el entorno de producción. Este diagrama detalla la infraestructura física y lógica, incluyendo la plataforma de contenedores Railway que aloja la aplicación monolítica y las bases de datos, así como los servicios de terceros como Firebase y GPT-4o mini. Su propósito es visualizar las dependencias de red y los entornos de ejecución para entender cómo los componentes de software se distribuyen y se comunican entre sí.

<img src="../img/chapter-4/c4_deploymentDiagram.png" alt="C4 Deployment Diagram" width="800">
