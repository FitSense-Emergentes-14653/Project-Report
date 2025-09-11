## Capítulo IV: Solution Software Design
## 4.1. Strategic-Level Domain-Driven Design. 
### 4.1.1. EventStorming. 

<p>Realizamos nuestro proceso de event storming a través de la herramienta Figma, donde trazamos todo el recorrido del sistema. Iniciamos con la fase inicial de Unstructured Exploration, en la cual discutimos y contrastamos nuestras ideas respecto a los eventos clave del dominio, guiándonos por las sugerencias recomendadas y centrandonos en el objetivo numero uno de nuestro proyecto. Asimismo, tomamos en cuenta diversos aspectos al elegir los eventos, tales como su importancia, recurrencia y momento de ocurrencia.<p>

🔗 [Ver Figma](https://www.figma.com/design/d79XNdidl0cHYUaA9o8zsj/Figma---Emergentes?t=GWl8L6Gfl27XnxeW-1)
<br>

**Step 1: Unstructured Exploration**

<p>Iniciamos con una exploración libre del dominio, donde cada integrante propuso eventos clave desde su perspectiva. Esta etapa nos permitió intercambiar ideas, descubrir puntos relevantes y construir una comprensión compartida del proceso. Para seleccionar los eventos, consideramos criterios como relevancia, frecuencia y temporalidad.<p>

<img src="img/es_unstructuredExploration.png" alt="Unstructured Exploration" width="80%">


**Step 2: Timelines**
<p>En esta fase organizamos los eventos del dominio de forma cronológica. Esto nos permitió visualizar el flujo completo del sistema, identificar el orden natural de los eventos y comprender mejor cómo interactúan los usuarios con FitSense en el proceso de registro, generación de planes, seguimiento y mejora física.</p>

<img src="img/es_timelines1.png" alt="Timelines 1" width="80%">

<img src="img/es_timelines2.png" alt="Timelines 2" width="80%">

**Step 3: Pain Points**
<p>Detectamos los puntos críticos o problemáticos que enfrentan tanto los usuarios como el sistema actual. Estos incluían desde notificaciones poco visibles que podrían ser ignoradas, hasta la dificultad de generar planes realistas cuando los datos ingresados son incompletos o inconsistentes.</p>

<img src="img/es_painPoints1.png" alt="Pain Points 1" width="80%">
<img src="img/es_painPoints2.png" alt="Pain Points 2" width="80%">
<br>
<br>
<br>

**Step 4: Pivotal Points**
<p>Identificamos los momentos clave que marcan cambios importantes dentro del proceso, como cuando se genera un nuevo plan personalizado, cuando el usuario recibe una alerta de inactividad o cuando se detecta una mejora en las métricas físicas mediante IA. Estos puntos nos ayudaron a definir posibles mejoras de alto impacto en la experiencia de uso.</p>

<img src="img/es_pivotalPoints1.png" alt="Pivotal Points 1" width="80%">
<img src="img/es_pivotalPoints2.png" alt="Pivotal Points 2" width="80%">
<br>
<br>
<br>

**Step 5: Commands**
<p>Aquí definimos las acciones que los usuarios o el sistema pueden ejecutar, como "Registrar Usuario", "Generar Plan de Entrenamiento", "Enviar Notificación de Hidratación" o "Subir Foto de Progreso". Cada comando representa una intención concreta que da lugar a eventos dentro de FitSense.</p>

<img src="img/es_commands.png" alt="Commands 1" width="80%">
<img src="img/es_commands2.png" alt="Commands 2" width="80%">
<br>
<br>
<br>

**Step 6: Policies**
<p>Establecimos las reglas de negocio que deben ejecutarse de forma automática ante ciertos eventos. Por ejemplo, si el sistema detecta inactividad por más de tres días, se activa una política que genera y envía una notificación push al usuario. O si se sube una foto de progreso, se activa una política de privacidad y de procesamiento de la imagen con IA.</p>

<img src="img/es_policies1.png" alt="Policies 1" width="80%">
<img src="img/es_policies2.png" alt="Policies 1" width="80%">
<br>
<br>
<br>

**Step 7: Read Models**
<p>Diseñamos los modelos de lectura que permitirán consultar el estado del usuario, como el dashboard con métricas de IMC, calorías recomendadas, gráficos de progreso semanal, historial de planes y logros sociales. Estos modelos están optimizados para ofrecer al usuario información clara, motivadora y accesible.</p>

<img src="img/es_readModels.png" alt="Read Models" width="80%">
<br>
<br>
<br>

**Step 8: External Systems**
<p>Identificamos los sistemas externos que interactúan con FitSense, como servicios de autenticación (Firebase Auth), APIs de notificaciones push, motores de IA de recomendación, librerías de visualización de gráficos y APIs de visión por computadora para el análisis de imágenes. También se contemplaron integraciones con redes sociales para compartir logros.</p>

<img src="img/es_externalSystems.png" alt="External Systems" width="80%">
<br>
<br>
<br>

**Step 9: Aggregates**
<p>Por último, definimos los aggregates, que representan los límites consistentes del dominio. Un ejemplo claro fue el aggregate de <b>Plan Personalizado</b>, que encapsula la lógica de generación y adaptación de planes de entrenamiento y alimentación. Otro aggregate clave fue <b>Monitoring</b>, que centraliza el seguimiento de métricas y la detección de mejoras físicas. Estos aggregates permiten mantener la coherencia del dominio y garantizar que cada área funcional de FitSense evolucione de manera independiente pero alineada.</p>

<img src="img/es_aggregates.png" alt="Aggregates" width="80%">

#### 4.1.1.1 Candidate Context Discovery. 

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

<img src="img/es_boundedContext1.png" alt="Bounded Context" width="80%">

**Bounded Context Plan**

<img src="img/es_boundedContext4.png" alt="Bounded Context" width="80%">


**Bounded Context Monitoring**

<img src="img/es_boundedContext3.png" alt="Bounded Context" width="80%">


**Bounded Context Notification**

<img src="img/es_boundedContext2.png" alt="Bounded Context" width="80%">


**Bounded Context Social**

<img src="img/es_boundedContext1.png" alt="Bounded Context" width="80%">
<br>
<br>
<br>


