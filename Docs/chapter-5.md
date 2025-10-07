# Capítulo V: Tactical-Level Software Design

## 5.1. Bounded Context: Plan Context

### 5.1.1. Domain Layer

A continuación, se presenta la organización del Domain Layer del Bounded Context: Plan Context, siguiendo la estructura de Aggregate, Value Objects, Domain Services y Repositories, con todos los elementos organizados en tablas independientes.

Aggregate
<table> <thead> <tr><th>Entidad</th><th>Atributos Clave</th><th>Value Objects Asociados</th><th>Métodos / Reglas</th></tr> </thead> <tbody> <tr> <td>Usuario</td> <td>id, nombre, edad, peso, altura, nivel, objetivo, frecuencia</td> <td>Objetivo, PerfilEntrenamiento</td> <td> crearPlan()<br> actualizarProgreso()<br> consultarRutina()<br> obtenerInsight()<br> definirObjetivo()<br> validarDatosFisicos() </td> </tr> <tr> <td>Plan</td> <td>id, usuarioId, fechaInicio, fechaFin, estado</td> <td>Rutina, Objetivo</td> <td> agregarRutina()<br> finalizarPlan()<br> actualizarPlan()<br> validarFechas()<br> sincronizarConIA() </td> </tr> <tr> <td>Progreso</td> <td>id, planId, fecha, pesoActual, caloriasQuemadas</td> <td>Métricas</td> <td> registrarProgreso()<br> calcularIMC()<br> analizarTendencia()<br> notificarIA() </td> </tr> </tbody> </table>

Value Objects
<table> <thead> <tr><th>VO</th><th>Atributos</th><th>Descripción</th></tr> </thead> <tbody> <tr><td>Objetivo</td><td>tipo, valorMeta</td><td>Define la meta física del usuario (bajar peso, ganar masa, mantener).</td></tr> <tr><td>Rutina</td><td>nombre, duracion, ejercicios</td><td>Describe un conjunto de ejercicios estructurados dentro de un plan.</td></tr> <tr><td>Métricas</td><td>peso, imc, calorías, consistencia</td><td>Valores medidos y calculados a partir del progreso del usuario.</td></tr> <tr><td>Insight</td><td>descripcion, recomendaciones</td><td>Resultado analítico de la IA con sugerencias personalizadas.</td></tr> </tbody> </table>

Domain Services
<table> <thead> <tr><th>Servicio</th><th>Métodos</th><th>Responsabilidad</th></tr> </thead> <tbody> <tr> <td>PlanManagementService</td> <td>crearPlan(), actualizarPlan(), finalizarPlan()</td> <td>Orquesta la creación, modificación y cierre de los planes de entrenamiento del usuario.</td> </tr> <tr> <td>ProgressAnalysisService</td> <td>registrarProgreso(), generarInsight(), sincronizarIA()</td> <td>Evalúa métricas de progreso y coordina la comunicación con el modelo de IA para generar recomendaciones.</td> </tr> <tr> <td>RoutineService</td> <td>crearRutina(), actualizarEjercicio(), validarRutina()</td> <td>Administra la estructura de rutinas dentro de cada plan.</td> </tr> </tbody> </table>

Repositories
<table> <thead> <tr><th>Repositorio</th><th>Métodos</th><th>Entidad</th></tr> </thead> <tbody> <tr><td>PlanRepository</td><td>findById(), findByUsuarioId(), save(), deleteById()</td><td>Plan</td></tr> <tr><td>ProgresoRepository</td><td>findByPlanId(), save(), deleteById()</td><td>Progreso</td></tr> <tr><td>RutinaRepository</td><td>findByPlanId(), save(), deleteById()</td><td>Rutina</td></tr> <tr><td>InsightRepository</td><td>findByProgresoId(), save(), deleteById()</td><td>Insight</td></tr> </tbody> </table>


### 5.1.2. Interface Layer

En esta sección, se presenta la Capa de Interfaz (Interface Layer) de FitSense – Plan Context, que actúa como punto de entrada para las interacciones entre los usuarios (atletas o entrenadores) y el sistema.
Esta capa está compuesta por una serie de controladores REST que manejan las solicitudes entrantes del cliente (web o móvil), procesan los datos mediante los servicios de aplicación y devuelven las respuestas correspondientes.

Los controladores expuestos en este contexto permiten gestionar planes, rutinas, progreso e insights generados por IA.

El contexto de esta capa incluye cuatro controladores principales: PlanController, RutinaController, ProgresoController e InsightController.
Estos controladores son responsables de administrar la creación, consulta y actualización de los planes de entrenamiento y los registros asociados al progreso del usuario.

Controladores
<table> <thead> <tr><th>PlanController</th><th>RutinaController</th></tr> </thead> <tbody> <tr> <td> + createPlan(planDto): ResponseEntity<br> + updatePlan(id, planDto): PlanDto<br> + getPlanByUsuario(usuarioId): List&lt;PlanDto&gt;<br> + deletePlan(id): ResponseEntity </td> <td> + getRutinasByPlan(planId): List&lt;RutinaDto&gt;<br> + addRutina(rutinaDto): ResponseEntity<br> + updateRutina(id, rutinaDto): RutinaDto<br> + deleteRutina(id): ResponseEntity </td> </tr> </tbody> </table> <table> <thead> <tr><th>ProgresoController</th><th>InsightController</th></tr> </thead> <tbody> <tr> <td> + getProgresoByPlan(planId): List&lt;ProgresoDto&gt;<br> + addProgreso(progresoDto): ResponseEntity<br> + updateProgreso(id, progresoDto): ProgresoDto<br> + deleteProgreso(id): ResponseEntity </td> <td> + getInsightsByProgreso(progresoId): List&lt;InsightDto&gt;<br> + generateInsight(progresoId): InsightDto<br> + deleteInsight(id): ResponseEntity </td> </tr> </tbody> </table>
Descripción de la capa

Responsabilidad:
La Interface Layer traduce las peticiones HTTP del usuario en comandos o consultas internas, garantizando una comunicación desacoplada entre el cliente y la lógica de negocio.
Todos los controladores exponen endpoints REST documentados en OpenAPI (Swagger) para facilitar su integración.

Integraciones:

Se conecta con la Application Layer mediante Handlers y Services.

Se comunica con el módulo de IA para la generación de recomendaciones (GPT-4o mini Connector).

Devuelve respuestas estructuradas en formato JSON.

### 5.1.3. Application Layer

En esta sección, se presenta la Capa de Aplicación (Application Layer) del Plan Context de FitSense. Esta capa actúa como intermediaria entre la lógica de dominio y la infraestructura, orquestando operaciones como creación/actualización de planes, registro de progreso y generación de recomendaciones por IA.
Se definen Command Handlers y Event Handlers que coordinan los servicios relevantes para ejecutar acciones como crear planes, registrar avances o actualizar rutinas cuando se generan insights.

Handlers
<table> <thead> <tr> <th>CreatePlanCommandHandler</th> <th>RegisterProgressCommandHandler</th> </tr> </thead> <tbody> <tr> <td> + planService: PlanManagementService<br/> + handle(CreatePlanCommand command): <i>Plan</i> </td> <td> + progressService: ProgressAnalysisService<br/> + handle(RegisterProgressCommand command): <i>Progreso</i> </td> </tr> </tbody> </table> <br/> <table> <thead> <tr> <th>GenerateInsightEventHandler</th> <th>PlanUpdatedEventHandler</th> </tr> </thead> <tbody> <tr> <td> + insightService: InsightService<br/> + handle(InsightGeneratedEvent event): <i>Insight</i> </td> <td> + planService: PlanManagementService<br/> + handle(PlanUpdatedEvent event): <i>void</i> </td> </tr> </tbody> </table> <br/> <table> <thead> <tr> <th>AdaptPlanCommandHandler</th> <th>DeletePlanCommandHandler</th> </tr> </thead> <tbody> <tr> <td> + planService: PlanManagementService<br/> + handle(AdaptPlanCommand command): <i>Plan</i> </td> <td> + planService: PlanManagementService<br/> + handle(DeletePlanCommand command): <i>void</i> </td> </tr> </tbody> </table> <br/> <table> <thead> <tr> <th>ProgressRegisteredEventHandler</th> <th>InsightPersistedEventHandler</th> </tr> </thead> <tbody> <tr> <td> + progressService: ProgressAnalysisService<br/> + handle(ProgressRegisteredEvent event): <i>Insight</i> </td> <td> + insightService: InsightService<br/> + handle(InsightPersistedEvent event): <i>void</i> </td> </tr> </tbody> </table>

### 5.1.4. Infrastructure Layer

En esta sección se presenta la Capa de Infraestructura (Infrastructure Layer) dentro del contexto de Planificación de FitSense. Esta capa proporciona los componentes técnicos y de soporte que permiten la interacción con la base de datos, los servicios de almacenamiento y el módulo de IA, responsable de generar y adaptar los planes personalizados.

Su función principal es implementar los contratos definidos en el dominio y garantizar la persistencia de los datos relacionados con planes, rutinas, progreso e insights.
Además, esta capa maneja la comunicación con el motor GPT-4o mini, responsable de las recomendaciones automáticas y del análisis de rendimiento.

Los repositorios definidos en esta capa usan frameworks como Spring Data JPA o Hibernate, representando el puente entre la lógica de negocio y el almacenamiento físico de los datos.

Repositorios
<table> <thead> <tr> <th>PlanRepository</th> <th>RutinaRepository</th> </tr> </thead> <tbody> <tr> <td> + findById(planId: UUID): <i>Plan</i><br/> + findByUsuarioId(usuarioId: UUID): List&lt;Plan&gt;<br/> + save(plan: Plan): void<br/> + deleteById(planId: UUID): void </td> <td> + findByPlanId(planId: UUID): List&lt;Rutina&gt;<br/> + findByNombre(nombre: String): <i>Rutina</i><br/> + save(rutina: Rutina): void<br/> + deleteById(rutinaId: UUID): void </td> </tr> </tbody> </table> <br/> <table> <thead> <tr> <th>ProgresoRepository</th> <th>InsightRepository</th> </tr> </thead> <tbody> <tr> <td> + findByPlanId(planId: UUID): List&lt;Progreso&gt;<br/> + findByFecha(fecha: Date): <i>Progreso</i><br/> + save(progreso: Progreso): void<br/> + deleteById(progresoId: UUID): void </td> <td> + findByProgresoId(progresoId: UUID): List&lt;Insight&gt;<br/> + findByDescripcionContaining(texto: String): List&lt;Insight&gt;<br/> + save(insight: Insight): void<br/> + deleteById(insightId: UUID): void </td> </tr> </tbody> </table>
Componentes de soporte

AIConnectorService
Servicio responsable de la comunicación con el modelo GPT-4o mini para la generación de insights y recomendaciones.
Expone endpoints REST y controla los tiempos de respuesta y manejo de errores.

DTO Mappers / Converters
Transforman las entidades del dominio a DTOs usados en la capa de aplicación e interfaz, asegurando un transporte de datos limpio y desacoplado.

PersistenceAdapter
Implementa el patrón Repository Adapter, traduciendo las entidades del dominio a entidades de persistencia (JPA Entities) y viceversa.

Integraciones tecnológicas

Base de datos: PostgreSQL / MySQL

Framework ORM: Spring Data JPA / Hibernate

Conector de IA: RESTful API → GPT-4o mini

Seguridad y despliegue: GitHub Actions + CI/CD

Formato de almacenamiento: JSON para planes y recomendaciones generadas por IA

### 5.1.6. Bounded Context Software Architecture Component Level Diagrams

![Plan Context Software Architecture Component Level Diagram](../img/chapter-5/PlanContextSoftwareArchitectureComponentLevelDiagram.png)

### 5.1.7. Bounded Context Software Architecture Code Level Diagrams

#### 5.1.7.1. Bounded Context Domain Layer Class Diagrams

En esta sección se presenta el diagrama de clases del dominio para el Plan Context de FitSense.
El modelo refleja la estructura de agregados, entidades y objetos de valor y sus relaciones (cardinalidades) usadas por la lógica de negocio para crear, adaptar y evaluar planes de entrenamiento.
Este diseño asegura consistencia dentro del agregado (Usuario → Plan) y trazabilidad del progreso y de los insights generados por la IA.

![Plan Context Domain Layer Class Diagram](../img/chapter-5/PlanContextDomainLayerClassDiagram.png)

#### 5.1.7.2. Bounded Context Database Design Diagram

En esta sección se presenta el diseño de base de datos correspondiente al Plan Context de FitSense.
El modelo de datos refleja la estructura de las entidades y sus relaciones mediante claves primarias y foráneas, garantizando la integridad referencial entre los usuarios, sus planes de entrenamiento, rutinas, progreso e insights generados por IA.

![Plan Context Database Design Diagram](../img/chapter-5/PlanContextDatabaseDesignDiagram.png)

## 5.2. Bounded Context: Social Context

### 5.2.1. Domain Layer

<p align="justify">
El Domain Layer del contexto de <b>Social</b> representa el núcleo de las funcionalidades sociales y de gamificación de FitSense. Su objetivo es modelar las entidades, objetos de valor, agregados y servicios que permiten a los usuarios compartir logros, participar en desafíos, generar reportes de progreso y mantener una comunidad motivadora, cumpliendo con las políticas de privacidad y visibilidad definidas por el sistema.
</p>

---

**Agregados**

<table>
<thead>
<tr>
<th>Entidad</th>
<th>Atributos Clave</th>
<th>Value Objects Asociados</th>
<th>Métodos / Reglas</th>
</tr>
</thead>
<tbody>
<tr>
<td>SocialProfile</td>
<td>userId, achievements, posts, followersCount, followingCount, totalReactionsReceived</td>
<td>UserId, Achievement, Post</td>
<td>
earnAchievement()<br>
createPost()<br>
exportProgressReport()<br>
incrementFollowers()<br>
calculateEngagementScore()<br>
validatePostContent()
</td>
</tr>
<tr>
<td>Challenge</td>
<td>challengeId, name, description, type, goal, startDate, endDate, participants, status</td>
<td>ChallengeId, ChallengeGoal, ChallengeType, Participant</td>
<td>
addParticipant()<br>
updateProgress()<br>
getLeaderboard()<br>
complete()<br>
validateDateRange()<br>
checkEligibility()
</td>
</tr>
<tr>
<td>Post</td>
<td>postId, userId, content, metrics, imageUrl, visibility, createdAt, reactions</td>
<td>PostId, PostContent, ProgressMetrics, Visibility, Reaction</td>
<td>
addReaction()<br>
updateVisibility()<br>
canBeEditedBy()<br>
validateContent()<br>
isPublic()
</td>
</tr>
<tr>
<td>Achievement</td>
<td>achievementId, userId, type, title, description, earnedDate, iconUrl, isShared</td>
<td>AchievementId, AchievementType</td>
<td>
share()<br>
getShareableContent()<br>
canBeShared()<br>
validateUnlockConditions()
</td>
</tr>
</tbody>
</table>

**Value Objects**

<table>
<thead>
<tr><th>VO</th><th>Atributos</th><th>Descripción</th></tr>
</thead>
<tbody>
<tr>
<td>PostContent</td>
<td>text, hashtags</td>
<td>Contenido de una publicación con validación de longitud (máx. 500 caracteres) y hashtags válidos.</td>
</tr>
<tr>
<td>ProgressMetrics</td>
<td>currentWeight, bmi, caloriesBurned, workoutsCompleted</td>
<td>Métricas de progreso que se incluyen en publicaciones y reportes.</td>
</tr>
<tr>
<td>ShareContent</td>
<td>title, description, imageUrl, deepLink</td>
<td>Contenido formateado para compartir en redes sociales externas.</td>
</tr>
<tr>
<td>ChallengeGoal</td>
<td>targetType, targetValue, unit</td>
<td>Define el objetivo cuantificable de un desafío (ej: 50 km corridos, 1000 calorías quemadas).</td>
</tr>
<tr>
<td>Participant</td>
<td>userId, joinedAt, currentProgress</td>
<td>Representa la participación de un usuario en un desafío específico.</td>
</tr>
<tr>
<td>Reaction</td>
<td>userId, type, createdAt</td>
<td>Reacción a una publicación (like, celebrate, inspire).</td>
</tr>
<tr>
<td>Visibility</td>
<td>level (PUBLIC, FRIENDS, PRIVATE)</td>
<td>Controla quién puede ver una publicación.</td>
</tr>
<tr>
<td>Leaderboard</td>
<td>rankings, updatedAt</td>
<td>Tabla de posiciones ordenada para un desafío específico.</td>
</tr>
<tr>
<td>ReportFormat</td>
<td>type (PDF, EXCEL)</td>
<td>Formato de exportación de reportes de progreso.</td>
</tr>
</tbody>
</table>

**Domain Services**

<table>
<thead>
<tr><th>Servicio</th><th>Métodos</th><th>Responsabilidad</th></tr>
</thead>
<tbody>
<tr>
<td>AchievementEvaluationService</td>
<td>evaluateAchievements(), checkMilestone(), detectNewAchievements()</td>
<td>Evalúa el progreso del usuario y determina si ha desbloqueado nuevos logros basándose en reglas de negocio complejas (ej: primera semana completada, 10 entrenamientos, meta de peso alcanzada).</td>
</tr>
<tr>
<td>ChallengeManagementService</td>
<td>createChallenge(), calculateLeaderboard(), updateParticipantProgress(), completeChallenge()</td>
<td>Orquesta la creación y gestión de desafíos grupales, calcula rankings y administra el ciclo de vida de las competencias.</td>
</tr>
<tr>
<td>SocialSharingService</td>
<td>shareToFacebook(), shareToInstagram(), shareToTwitter(), generateShareableContent()</td>
<td>Coordina el proceso de compartir contenido en plataformas externas, generando contenido optimizado para cada red social.</td>
</tr>
<tr>
<td>ReportGenerationService</td>
<td>generatePdfReport(), generateExcelReport(), compileReportData()</td>
<td>Genera reportes de progreso en diferentes formatos consolidando datos de métricas, entrenamientos y logros.</td>
</tr>
</tbody>
</table>

**Repositories**

<table>
<thead>
<tr><th>Repositorio</th><th>Métodos</th><th>Entidad</th></tr>
</thead>
<tbody>
<tr>
<td>SocialProfileRepository</td>
<td>findByUserId(), save(), update(), incrementFollowersCount()</td>
<td>SocialProfile</td>
</tr>
<tr>
<td>PostRepository</td>
<td>findById(), findByUserId(), findPublicPosts(), save(), delete(), updateReactions()</td>
<td>Post</td>
</tr>
<tr>
<td>AchievementRepository</td>
<td>findByUserId(), findByType(), save(), markAsShared()</td>
<td>Achievement</td>
</tr>
<tr>
<td>ChallengeRepository</td>
<td>findById(), findActiveChallenges(), findByParticipant(), save(), updateParticipants()</td>
<td>Challenge</td>
</tr>
</tbody>
</table>

---

### 5.2.2. Interface Layer

En esta capa se definen los puntos de entrada del contexto Social. Los **Controllers** permiten que los usuarios interactúen con las funcionalidades sociales a través de APIs REST.

**Controladores**

<table>
<thead>
<tr><th>SocialController</th><th>AchievementController</th></tr>
</thead>
<tbody>
<tr>
<td>
+ createPost(postDto): ResponseEntity<br>
+ getPosts(userId, pagination): List&lt;PostDto&gt;<br>
+ updatePost(postId, postDto): PostDto<br>
+ deletePost(postId): ResponseEntity<br>
+ addReaction(postId, reactionDto): ResponseEntity<br>
+ getSocialProfile(userId): SocialProfileDto
</td>
<td>
+ getAchievements(userId): List&lt;AchievementDto&gt;<br>
+ shareAchievement(achievementId, platforms): ResponseEntity<br>
+ getPendingAchievements(userId): List&lt;AchievementProgressDto&gt;<br>
+ getAchievementDetails(achievementId): AchievementDto
</td>
</tr>
</tbody>
</table>

<table>
<thead>
<tr><th>ChallengeController</th><th>ReportController</th></tr>
</thead>
<tbody>
<tr>
<td>
+ getActiveChallenges(): List&lt;ChallengeDto&gt;<br>
+ joinChallenge(challengeId, userId): ResponseEntity<br>
+ getLeaderboard(challengeId): LeaderboardDto<br>
+ createCustomChallenge(challengeDto): ResponseEntity<br>
+ updateProgress(challengeId, progressDto): ResponseEntity
</td>
<td>
+ exportProgressReport(userId, format, dateRange): ResponseEntity<br>
+ shareReport(userId, reportId, platforms): ResponseEntity<br>
+ getReportHistory(userId): List&lt;ReportDto&gt;
</td>
</tr>
</tbody>
</table>

**Descripción de la capa**

**Responsabilidad:**  
La Interface Layer traduce las peticiones HTTP del usuario en comandos o consultas internas, garantizando una comunicación desacoplada entre el cliente y la lógica de negocio. Todos los controladores exponen endpoints REST documentados en OpenAPI (Swagger) para facilitar su integración.

**Integraciones:**
- Se conecta con la Application Layer mediante Command Handlers y Event Handlers.
- Se comunica con APIs externas de redes sociales (Facebook, Instagram, Twitter).
- Recibe notificaciones internas de otros bounded contexts mediante eventos del dominio.
- Devuelve respuestas estructuradas en formato JSON.

---

### 5.2.3. Application Layer

En esta sección, se presenta la Capa de Aplicación (Application Layer) del Social Context de FitSense. Esta capa actúa como intermediaria entre la lógica de dominio y la infraestructura, orquestando operaciones como creación de publicaciones, compartir logros, gestión de desafíos y generación de reportes. Se definen Command Handlers y Event Handlers que coordinan los servicios relevantes para ejecutar acciones sociales y de gamificación.

**Command Handlers**

<table>
<thead>
<tr>
<th>CreatePostCommandHandler</th>
<th>ShareAchievementCommandHandler</th>
</tr>
</thead>
<tbody>
<tr>
<td>
+ socialProfileRepository: SocialProfileRepository<br>
+ postRepository: PostRepository<br>
+ handle(CreatePostCommand command): <i>Post</i>
</td>
<td>
+ achievementRepository: AchievementRepository<br>
+ socialSharingService: SocialSharingService<br>
+ handle(ShareAchievementCommand command): <i>void</i>
</td>
</tr>
</tbody>
</table>

<table>
<thead>
<tr>
<th>JoinChallengeCommandHandler</th>
<th>ExportProgressReportCommandHandler</th>
</tr>
</thead>
<tbody>
<tr>
<td>
+ challengeRepository: ChallengeRepository<br>
+ challengeManagementService: ChallengeManagementService<br>
+ handle(JoinChallengeCommand command): <i>void</i>
</td>
<td>
+ reportGenerationService: ReportGenerationService<br>
+ socialProfileRepository: SocialProfileRepository<br>
+ handle(ExportReportCommand command): <i>Report</i>
</td>
</tr>
</tbody>
</table>

<table>
<thead>
<tr>
<th>UpdatePostCommandHandler</th>
<th>AddReactionCommandHandler</th>
</tr>
</thead>
<tbody>
<tr>
<td>
+ postRepository: PostRepository<br>
+ handle(UpdatePostCommand command): <i>Post</i>
</td>
<td>
+ postRepository: PostRepository<br>
+ handle(AddReactionCommand command): <i>void</i>
</td>
</tr>
</tbody>
</table>

**Event Handlers**

<table>
<thead>
<tr>
<th>OnProgressMilestoneReachedEventHandler</th>
<th>OnWorkoutCompletedEventHandler</th>
</tr>
</thead>
<tbody>
<tr>
<td>
+ achievementEvaluationService: AchievementEvaluationService<br>
+ achievementRepository: AchievementRepository<br>
+ handle(ProgressMilestoneReachedEvent event): <i>void</i>
</td>
<td>
+ challengeManagementService: ChallengeManagementService<br>
+ challengeRepository: ChallengeRepository<br>
+ handle(WorkoutCompletedEvent event): <i>void</i>
</td>
</tr>
</tbody>
</table>

<table>
<thead>
<tr>
<th>OnWeeklyProgressComputedEventHandler</th>
<th>PostCreatedEventHandler</th>
</tr>
</thead>
<tbody>
<tr>
<td>
+ socialProfileRepository: SocialProfileRepository<br>
+ handle(WeeklyProgressComputedEvent event): <i>void</i>
</td>
<td>
+ notificationService: NotificationService<br>
+ handle(PostCreatedEvent event): <i>void</i>
</td>
</tr>
</tbody>
</table>

<table>
<thead>
<tr>
<th>AchievementEarnedEventHandler</th>
<th>ChallengeCompletedEventHandler</th>
</tr>
</thead>
<tbody>
<tr>
<td>
+ socialProfileRepository: SocialProfileRepository<br>
+ handle(AchievementEarnedEvent event): <i>void</i>
</td>
<td>
+ challengeRepository: ChallengeRepository<br>
+ notificationService: NotificationService<br>
+ handle(ChallengeCompletedEvent event): <i>void</i>
</td>
</tr>
</tbody>
</table>

---

### 5.2.4. Infrastructure Layer

En esta sección se presenta la Capa de Infraestructura (Infrastructure Layer) dentro del Social Context de FitSense. Esta capa proporciona los componentes técnicos y de soporte que permiten la interacción con la base de datos, servicios de almacenamiento de archivos, APIs de redes sociales y generadores de reportes.

Su función principal es implementar los contratos definidos en el dominio y garantizar la persistencia de los datos relacionados con perfiles sociales, publicaciones, logros, desafíos y reportes. Además, esta capa maneja la comunicación con servicios externos como Facebook, Instagram, Twitter y generadores de documentos PDF/Excel.

**Repositorios**

<table>
<thead>
<tr>
<th>SocialProfileRepository</th>
<th>PostRepository</th>
</tr>
</thead>
<tbody>
<tr>
<td>
+ findByUserId(userId: UUID): <i>SocialProfile</i><br>
+ save(profile: SocialProfile): void<br>
+ update(profile: SocialProfile): void<br>
+ incrementFollowersCount(userId: UUID): void
</td>
<td>
+ findById(postId: UUID): <i>Post</i><br>
+ findByUserId(userId: UUID, pagination: Pagination): List&lt;Post&gt;<br>
+ findPublicPosts(pagination: Pagination): List&lt;Post&gt;<br>
+ save(post: Post): void<br>
+ delete(postId: UUID): void<br>
+ updateReactions(postId: UUID, reactions: List&lt;Reaction&gt;): void
</td>
</tr>
</tbody>
</table>

<table>
<thead>
<tr>
<th>AchievementRepository</th>
<th>ChallengeRepository</th>
</tr>
</thead>
<tbody>
<tr>
<td>
+ findByUserId(userId: UUID): List&lt;Achievement&gt;<br>
+ findByType(type: AchievementType): List&lt;Achievement&gt;<br>
+ save(achievement: Achievement): void<br>
+ markAsShared(achievementId: UUID): void
</td>
<td>
+ findById(challengeId: UUID): <i>Challenge</i><br>
+ findActiveChallenges(): List&lt;Challenge&gt;<br>
+ findByParticipant(userId: UUID): List&lt;Challenge&gt;<br>
+ save(challenge: Challenge): void<br>
+ updateParticipants(challengeId: UUID, participants: List&lt;Participant&gt;): void
</td>
</tr>
</tbody>
</table>

**Componentes de soporte**

**SocialMediaIntegrationService**  
Servicio responsable de la integración con APIs de redes sociales (Facebook, Instagram, Twitter). Maneja la autenticación OAuth, formato de contenido y envío de publicaciones.

**ReportGenerationService**  
Genera reportes de progreso en formatos PDF y Excel utilizando librerías como PDFKit o ExcelJS. Consolida datos de métricas, entrenamientos y logros.

**FileStorageService**  
Gestiona el almacenamiento temporal de archivos generados (reportes, imágenes de posts) en servicios cloud como Firebase Storage.

**DTO Mappers / Converters**  
Transforman las entidades del dominio a DTOs usados en la capa de aplicación e interfaz, asegurando un transporte de datos limpio y desacoplado.

**EventPublisher**  
Implementa el patrón Observer para publicar eventos de dominio (PostCreated, AchievementEarned) que pueden ser consumidos por otros bounded contexts dentro del monolito.

**Integraciones tecnológicas**

- **Base de datos:** PostgreSQL / MySQL
- **Framework ORM:** Spring Data JPA / Prisma / TypeORM
- **APIs de Redes Sociales:** Facebook Graph API, Instagram Graph API, Twitter API v2
- **Generación de Reportes:** PDFKit, ExcelJS, Apache POI
- **Almacenamiento de archivos:** Firebase Storage
- **Event Bus interno:** Spring Events / Domain Events Pattern
- **Formato de datos:** JSON para intercambio de información

---

### 5.2.5. Bounded Context Software Architecture Component Level Diagrams

![Social Context Software Architecture Component Level Diagram](../img/chapter-5/SocialContextSoftwareArchitectureComponentLevelDiagram.png)

---

### 5.2.6. Bounded Context Software Architecture Code Level Diagrams

#### 5.2.6.1. Bounded Context Domain Layer Class Diagrams

En esta sección se presenta el diagrama de clases del dominio para el Social Context de FitSense. El modelo refleja la estructura de agregados, entidades y objetos de valor y sus relaciones (cardinalidades) usadas por la lógica de negocio para gestionar perfiles sociales, publicaciones, logros, desafíos y reportes. Este diseño asegura consistencia dentro de los agregados y trazabilidad de las interacciones sociales.

![Social Context Domain Layer Class Diagram](../img/chapter-5/SocialContextDomainLayerClassDiagram.png)

#### 5.2.6.2. Bounded Context Database Design Diagram

En esta sección se presenta el diseño de base de datos correspondiente al Social Context de FitSense. El modelo de datos refleja la estructura de las entidades y sus relaciones mediante claves primarias y foráneas, garantizando la integridad referencial entre los perfiles sociales, publicaciones, logros, desafíos y participantes.

![Social Context Database Design Diagram](../img/chapter-5/SocialContextDatabaseDesignDiagram.png)

---

## 5.3. Bounded Context: Notification Context

### 5.3.1. Domain Layer

<p align="justify">
El Domain Layer del contexto de <b>Notificaciones</b> representa el núcleo de la gestión de recordatorios, alertas y comunicaciones proactivas de FitSense. Su objetivo es modelar las entidades, objetos de valor, agregados y servicios que permiten enviar notificaciones personalizadas, inteligentes y respetuosas del tiempo del usuario, cumpliendo con las políticas de "No molestar" y preferencias individuales definidas por el sistema.
</p>

---

**Agregados**

<table>
<thead>
<tr>
<th>Entidad</th>
<th>Atributos Clave</th>
<th>Value Objects Asociados</th>
<th>Métodos / Reglas</th>
</tr>
</thead>
<tbody>
<tr>
<td>NotificationPreferences</td>
<td>userId, schedules, deviceTokens, globalDoNotDisturb, enabledTypes</td>
<td>UserId, NotificationSchedule, DeviceToken, TimeRange, NotificationType</td>
<td>
addSchedule()<br>
updateSchedule()<br>
registerDevice()<br>
setGlobalDoNotDisturb()<br>
enableNotificationType()<br>
disableNotificationType()<br>
isTypeEnabled()<br>
isInDoNotDisturbPeriod()
</td>
</tr>
<tr>
<td>NotificationSchedule</td>
<td>scheduleId, userId, type, recurrence, preferredTime, isActive, doNotDisturbPeriods</td>
<td>ScheduleId, NotificationType, Recurrence, TimeOfDay, TimeRange</td>
<td>
activate()<br>
deactivate()<br>
updatePreferredTime()<br>
addDoNotDisturbPeriod()<br>
shouldSendAt()<br>
calculateNextSendTime()<br>
validateRecurrence()
</td>
</tr>
<tr>
<td>Notification</td>
<td>notificationId, userId, type, title, message, payload, scheduledAt, sentAt, deliveredAt, readAt, status</td>
<td>NotificationId, NotificationType, NotificationPayload, NotificationStatus</td>
<td>
markAsSent()<br>
markAsDelivered()<br>
markAsRead()<br>
markAsFailed()<br>
canBeSent()<br>
isExpired()<br>
retry()
</td>
</tr>
<tr>
<td>DeviceToken</td>
<td>tokenId, userId, token, platform, registeredAt, lastUsedAt, isActive</td>
<td>TokenId, Platform</td>
<td>
updateLastUsed()<br>
deactivate()<br>
isValid()<br>
needsRefresh()
</td>
</tr>
</tbody>
</table>

**Value Objects**

<table>
<thead>
<tr><th>VO</th><th>Atributos</th><th>Descripción</th></tr>
</thead>
<tbody>
<tr>
<td>Recurrence</td>
<td>frequency, daysOfWeek, customInterval</td>
<td>Define la frecuencia de envío (ONCE, DAILY, WEEKLY, CUSTOM) y parámetros específicos.</td>
</tr>
<tr>
<td>TimeOfDay</td>
<td>hour, minute</td>
<td>Representa un momento específico del día (formato 24h) con validación de rangos.</td>
</tr>
<tr>
<td>TimeRange</td>
<td>startTime, endTime</td>
<td>Define un período de tiempo (ej: horario de "No molestar" de 22:00 a 07:00).</td>
</tr>
<tr>
<td>NotificationPayload</td>
<td>data, deepLink, actionButtons</td>
<td>Contenido adicional de la notificación (datos, enlaces profundos, botones de acción).</td>
</tr>
<tr>
<td>NotificationType</td>
<td>type (WORKOUT_REMINDER, HYDRATION, ACHIEVEMENT, INACTIVITY, MILESTONE)</td>
<td>Categoriza el tipo de notificación para control granular de preferencias.</td>
</tr>
<tr>
<td>NotificationStatus</td>
<td>status (SCHEDULED, SENT, DELIVERED, READ, FAILED)</td>
<td>Estado del ciclo de vida de una notificación.</td>
</tr>
<tr>
<td>Platform</td>
<td>type (IOS, ANDROID)</td>
<td>Plataforma del dispositivo para notificaciones push específicas.</td>
</tr>
<tr>
<td>UsagePattern</td>
<td>mostActiveHours, avgResponseTime, preferredDays</td>
<td>Patrón de uso del usuario para optimización adaptativa de horarios.</td>
</tr>
</tbody>
</table>

**Domain Services**

<table>
<thead>
<tr><th>Servicio</th><th>Métodos</th><th>Responsabilidad</th></tr>
</thead>
<tbody>
<tr>
<td>NotificationSchedulingService</td>
<td>calculateNextSendTime(), shouldSendNotification(), getActiveSchedulesForTime()</td>
<td>Determina cuándo enviar notificaciones según las preferencias del usuario, horarios "No molestar" y recurrencias configuradas.</td>
</tr>
<tr>
<td>AdaptiveNotificationService</td>
<td>analyzeUsagePatterns(), suggestOptimalTimes(), adaptScheduleBasedOnEngagement()</td>
<td>Analiza patrones de uso del usuario y ajusta horarios de notificaciones para maximizar engagement y minimizar molestias.</td>
</tr>
<tr>
<td>NotificationContentService</td>
<td>generateMotivationalMessage(), personalizeContent(), createDeepLink()</td>
<td>Genera contenido personalizado y motivacional para notificaciones basado en el contexto y progreso del usuario.</td>
</tr>
<tr>
<td>PushNotificationService</td>
<td>sendToDevice(), sendToMultipleDevices(), validateToken()</td>
<td>Abstracción del servicio de envío de notificaciones push (implementado en Infrastructure Layer).</td>
</tr>
</tbody>
</table>

**Repositories**

<table>
<thead>
<tr><th>Repositorio</th><th>Métodos</th><th>Entidad</th></tr>
</thead>
<tbody>
<tr>
<td>NotificationPreferencesRepository</td>
<td>findByUserId(), save(), update(), findSchedulesByType()</td>
<td>NotificationPreferences</td>
</tr>
<tr>
<td>NotificationRepository</td>
<td>findById(), findByUserId(), findScheduledForTimeRange(), save(), update(), bulkUpdate()</td>
<td>Notification</td>
</tr>
<tr>
<td>DeviceTokenRepository</td>
<td>findByUserId(), findByToken(), save(), deactivateOldTokens()</td>
<td>DeviceToken</td>
</tr>
<tr>
<td>UsagePatternRepository</td>
<td>findByUserId(), save(), update(), computePatterns()</td>
<td>UsagePattern</td>
</tr>
</tbody>
</table>

---

### 5.3.2. Interface Layer

En esta capa se definen los puntos de entrada del contexto de Notificaciones. Los **Controllers** permiten que los usuarios gestionen sus preferencias y consulten notificaciones.

**Controladores**

<table>
<thead>
<tr><th>NotificationController</th><th>NotificationPreferencesController</th></tr>
</thead>
<tbody>
<tr>
<td>
+ getNotifications(userId, pagination): List&lt;NotificationDto&gt;<br>
+ markAsRead(notificationId): ResponseEntity<br>
+ getUnreadCount(userId): CountDto<br>
+ deleteNotification(notificationId): ResponseEntity
</td>
<td>
+ getPreferences(userId): NotificationPreferencesDto<br>
+ updatePreferences(userId, preferencesDto): ResponseEntity<br>
+ addSchedule(userId, scheduleDto): ResponseEntity<br>
+ updateSchedule(userId, scheduleId, scheduleDto): ResponseEntity<br>
+ deleteSchedule(userId, scheduleId): ResponseEntity<br>
+ setDoNotDisturb(userId, dndDto): ResponseEntity
</td>
</tr>
</tbody>
</table>

<table>
<thead>
<tr><th>DeviceTokenController</th></tr>
</thead>
<tbody>
<tr>
<td>
+ registerToken(tokenDto): ResponseEntity<br>
+ unregisterToken(token): ResponseEntity<br>
+ getDevices(userId): List&lt;DeviceDto&gt;<br>
+ refreshToken(oldToken, newToken): ResponseEntity
</td>
</tr>
</tbody>
</table>

**Descripción de la capa**

**Responsabilidad:**  
La Interface Layer traduce las peticiones HTTP del usuario en comandos o consultas internas para gestión de notificaciones y preferencias. También recibe eventos internos de otros bounded contexts que desencadenan notificaciones automáticas.

**Integraciones:**
- Se conecta con la Application Layer mediante Command Handlers y Event Handlers.
- Recibe eventos de dominio de otros bounded contexts (Plan, Monitoring, Social, Security).
- Expone APIs REST documentadas en OpenAPI (Swagger).
- Devuelve respuestas estructuradas en formato JSON.

---

### 5.3.3. Application Layer

En esta sección, se presenta la Capa de Aplicación (Application Layer) del Notification Context de FitSense. Esta capa actúa como intermediaria entre la lógica de dominio y la infraestructura, orquestando operaciones como envío de notificaciones, programación de recordatorios, gestión de preferencias y análisis adaptativo. Se definen Command Handlers, Event Handlers y Scheduled Jobs que coordinan los servicios relevantes.

**Command Handlers**

### 5.3.4. Infrastructure Layer

### 5.3.6. Bounded Context Software Architecture Component Level Diagrams

### 5.3.7. Bounded Context Software Architecture Code Level Diagrams

#### 5.3.7.1. Bounded Context Domain Layer Class Diagrams

#### 5.3.7.2. Bounded Context Database Design Diagram

## 5.4. Bounded Context: Monitoring Context

### 5.4.1. Domain Layer

<p align="justify">
El Domain Layer del contexto de <b>Monitoreo</b> representa el núcleo de la aplicación FitSense. Su objetivo es modelar las entidades, objetos de valor, agregados y servicios que permiten registrar, procesar y analizar la información de progreso físico del usuario (IMC, peso, adherencia, calorías, fotos de progreso, etc.) cumpliendo con las políticas de privacidad y precisión definidas por el sistema.
</p>

---

<p><b>Entidades de dominio</b></p>

<li>
    <b>MetricSnapshot:</b> Representa un registro individual de una métrica del usuario (peso, IMC, calorías, pasos, frecuencia cardíaca).
</li>

<li>
    <b>WorkoutSummary:</b> Registra el resumen de un entrenamiento completado, incluyendo duración, tipo y calorías quemadas.
</li>

<li>
    <b>PhotoProgress:</b> Representa una foto de progreso subida por el usuario con su respectivo consentimiento de privacidad. Permite posteriormente ejecutar análisis de imagen con IA.
</li>

<li>
    <b>ImprovementFinding:</b> Registra las mejoras detectadas por el sistema en base a la comparación de métricas o resultados visuales, como la reducción del IMC o cambios en la silueta corporal.
</li> <br>

<p><b>Objetos de valor (Value Objects)</b></p>

<li>
    <b>UserId:</b> Identificador único e inmutable de un usuario.
</li>

<li>
    <b>MetricName:</b> Define el tipo de métrica registrada (IMC, peso, calorías, pasos, HR, etc.).
</li>

<li>
    <b>MetricUnit:</b> Representa la unidad de medida asociada a una métrica.
</li>

<li>
    <b>AdherenceScore:</b> Representa el nivel de cumplimiento semanal de rutinas del usuario (escala 0–1).
</li>

<li>
    <b>CalorieBalance:</b> Modela el balance energético (calorías ingeridas – calorías quemadas).
</li>

<li>
    <b>PrivacyConsent:</b> Registra el consentimiento del usuario para el uso, análisis o almacenamiento de imágenes personales.
</li>

<li>
    <b>DataRetentionPolicy:</b> Define la duración y condiciones de almacenamiento de datos sensibles.
</li>

<li>
    <b>TimeWindow:</b> Intervalo de tiempo usado para agregaciones y cálculos.
</li>

<li>
    <b>Week:</b> Representa una semana ISO (año + número de semana).
</li> <br>

<p><b>Agregados</b></p>

<li>
    <b>WeeklyProgress:</b> Agregado raíz que consolida el progreso semanal del usuario (IMC, peso, adherencia, balance calórico, mejoras detectadas). Se actualiza automáticamente al final de cada semana.
</li> <br>

<p><b>Servicios de dominio</b></p>

<li>
    <b>ProgressComputationService:</b> Calcula indicadores clave del progreso semanal (IMC promedio, peso variado, adherencia, balance calórico) a partir de métricas y entrenamientos registrados.
</li>

<li>
    <b>ImprovementDetectionService:</b> Detecta mejoras físicas en base a comparaciones de métricas o resultados de visión computacional. Utiliza TensorFlow como analizador de imágenes.
</li>

<li>
    <b>ReportFactory:</b> Fábrica encargada de generar reportes semanales en formatos PDF o Excel utilizando los datos consolidados en WeeklyProgress.
</li> <br>

<p><b>Repositorios</b></p>

<li>
    <b>MetricsRepository:</b> Maneja la persistencia y consulta de las métricas del usuario en la base de datos de series temporales.
</li>

<li>
    <b>WorkoutsRepository:</b> Gestiona la persistencia de los entrenamientos registrados.
</li>

<li>
    <b>WeeklyProgressRepository:</b> Persiste los datos consolidados del progreso semanal.
</li>

<li>
    <b>PhotoProgressRepository:</b> Maneja las referencias a las fotos de progreso en el almacenamiento en la nube.
</li> <br>

<p><b>Interfaces (Ports)</b></p>

<li>
    <b>ImageAnalyzer:</b> Define la interfaz para servicios de análisis de imagen (visión por computadora). La implementación concreta se realiza en la capa de infraestructura mediante TensorFlow.
</li>

---

### 5.4.2. Interface Layer

<p align="justify">
En esta capa se definen los puntos de entrada del contexto de Monitoreo. Los <b>Controllers</b> y <b>Consumers</b> permiten que los usuarios y servicios externos interactúen con las funcionalidades de monitoreo a través de APIs REST o mensajería.
</p>

<li>
    <b>MetricsController:</b> Gestiona las operaciones de consulta de métricas del usuario, permitiendo visualizar series y promedios de IMC, peso y calorías. 
</li>

<li>
    <b>WorkoutsController:</b> Maneja el registro y consulta de entrenamientos. Interactúa con el <i>Application Layer</i> para emitir eventos al contexto de Planificación.
</li>

<li>
    <b>ProgressController:</b> Permite subir fotos de progreso, consultar el resumen semanal y solicitar análisis de imagen.
</li>

<li>
    <b>ReportsController:</b> Genera y exporta reportes de progreso en PDF o Excel.
</li>

<li>
    <b>WearableIngestConsumer:</b> Consume datos enviados por dispositivos wearables (pasos, ritmo cardíaco, calorías) para incorporarlos al sistema.
</li>

<li>
    <b>PlanEventsConsumer:</b> Escucha eventos provenientes del contexto de Planificación (por ejemplo, “AdherenceCalculated”) para actualizar el progreso semanal.
</li> <br>

---

### 5.4.3. Application Layer

<p align="justify">
El Application Layer del contexto de Monitoreo se encarga de orquestar los procesos de negocio y coordinar las transacciones entre el dominio y la infraestructura. Aplica el patrón CQRS y maneja tanto comandos como eventos relacionados con el progreso del usuario.
</p>

<p><b>Command Handlers:</b></p>

<li>
    <b>RecordWorkoutCommandHandler:</b> Procesa la creación de un nuevo entrenamiento. Valida los datos, guarda el resumen y emite el evento <i>WorkoutRecorded</i>.
</li>

<li>
    <b>IngestMetricCommandHandler:</b> Procesa el registro de una nueva métrica (IMC, peso, calorías). Emite el evento <i>MetricRecorded</i>.
</li>

<li>
    <b>SubmitProgressPhotoCommandHandler:</b> Valida el consentimiento de privacidad, guarda la referencia de imagen y emite el evento <i>PhotoSubmitted</i>.
</li>

<li>
    <b>AnalyzePhotoCommandHandler:</b> Invoca el servicio de análisis de imagen (TensorFlow) si el usuario otorgó permiso.
</li>

<li>
    <b>ComputeWeeklyProgressCommandHandler:</b> Calcula y consolida el progreso semanal usando los servicios de dominio, emitiendo <i>WeeklyProgressComputed</i>.
</li>

<li>
    <b>ExportWeeklyReportCommandHandler:</b> Genera un reporte PDF/Excel utilizando la <i>ReportFactory</i>.
</li> <br>

<p><b>Event Handlers:</b></p>

<li>
    <b>OnMetricRecordedProjector:</b> Actualiza los dashboards con las métricas más recientes.
</li>

<li>
    <b>OnWorkoutRecordedProjector:</b> Actualiza los totales de calorías y adherencia de la semana.
</li>

<li>
    <b>OnImageAnalyzedDetector:</b> Ejecuta el servicio de detección de mejoras físicas y emite <i>ImprovementDetected</i>.
</li>

<li>
    <b>OnAdherenceCalculatedUpdater:</b> Escucha el evento <i>AdherenceCalculated</i> desde el contexto de Plan y actualiza la adherencia semanal.
</li> <br>

---

### 5.4.4. Infrastructure Layer

<p align="justify">
La capa de infraestructura implementa los repositorios, adaptadores y servicios externos que apoyan al dominio del contexto de Monitoreo. Se encarga de la persistencia de datos, análisis de imágenes y comunicación asincrónica entre contextos.
</p>

<p><b>Bases de datos:</b></p>

<li>
    <b>Relacional (PostgreSQL):</b> Almacena entidades principales como <i>workouts</i>, <i>weekly_progress</i> y <i>photo_progress</i>.
</li>

<li>
    <b>Time-Series (TimescaleDB):</b> Registra las métricas históricas (IMC, calorías, pasos) para análisis longitudinales.
</li>

<li>
    <b>Blob Storage (Firebase Storage / AWS S3):</b> Contiene las imágenes de progreso. Solo se almacenan referencias opacas (ImageRef).
</li> <br>

<p><b>Repositorios implementados:</b></p>

<li>
    <b>MetricsRepositorySql:</b> Implementa <i>MetricsRepository</i> usando SQL sobre una base de datos de series temporales.
</li>

<li>
    <b>WorkoutsRepositorySql:</b> Implementa <i>WorkoutsRepository</i> con ORM (TypeORM o Prisma).
</li>

<li>
    <b>WeeklyProgressRepositorySql:</b> Persiste los agregados semanales.
</li>

<li>
    <b>PhotoProgressRepositorySql:</b> Guarda los metadatos de fotos de progreso, delegando el archivo binario al Blob Storage.
</li> <br>

<p><b>Servicios externos:</b></p>

<li>
    <b>ImageAnalyzerTensorFlow:</b> Implementación concreta del puerto <i>ImageAnalyzer</i>. Utiliza modelos de visión computacional (TensorFlow) para detectar cambios físicos y calcular el nivel de confianza.
</li>

<li>
    <b>MessageBrokerAdapter:</b> Gestiona la comunicación asincrónica mediante colas (Kafka o RabbitMQ) para eventos de progreso.
</li>

<li>
    <b>NotificationAdapter:</b> Envía notificaciones push al usuario cuando se detectan mejoras físicas o recordatorios de rutina.
</li>

<li>
    <b>Scheduler:</b> Automatiza la ejecución semanal de procesos de consolidación y generación de reportes.
</li> <br>

### 5.4.6. Bounded Context Software Architecture Component Level Diagrams

```mermaid
C4Component
title FitSense - Monitoring Context (Component Diagram)

Person(user, "Usuario", "Registra y consulta su progreso.")
Container(spa, "Web Dashboard", "React/Next.js", "UI de progreso y reportes.")
Container(ml, "AI Image Analyzer", "TensorFlow", "Analiza fotos de progreso.")
ContainerDb(dbSql, "Monitoring DB", "PostgreSQL", "Workouts y progreso semanal.")
ContainerDb(dbTs, "Metrics TS DB", "Timescale/Influx", "Series de métricas.")
Container(blob, "Blob Storage", "Firebase/S3", "Fotos de progreso.")
Container(queue, "Message Broker", "Kafka/RabbitMQ", "Eventos de dominio.")

%% ====== API Boundary ======
Container_Boundary(api, "Monitoring API (NestJS/REST)") {

  Component(metricsCtrl, "MetricsController", "Controller",
            "Consultas de series y KPIs.")
  Component(workoutsCtrl, "WorkoutsController", "Controller",
            "Registro/consulta de entrenos.")
  Component(progressCtrl, "ProgressController", "Controller",
            "Subir foto, progreso semanal.")
  Component(reportsCtrl, "ReportsController", "Controller",
            "Exportar PDF/Excel.")
  Component(webhookCtrl, "ProviderWebhookController", "Controller",
            "Webhook wearables.")

  Component(cmdRecordWorkout, "RecordWorkoutHandler", "Command Handler", "")
  Component(cmdIngestMetric, "IngestMetricHandler", "Command Handler", "")
  Component(cmdSubmitPhoto, "SubmitPhotoHandler", "Command Handler", "")
  Component(cmdAnalyzePhoto, "AnalyzePhotoHandler", "Command Handler", "")
  Component(cmdComputeWeek, "ComputeWeeklyHandler", "Command Handler", "")
  Component(cmdExportReport, "ExportReportHandler", "Command Handler", "")

  Component(evMetricProj, "OnMetricRecorded", "Event Handler", "Proyección dashboard.")
  Component(evWorkoutProj, "OnWorkoutRecorded", "Event Handler", "Proyección dashboard.")
  Component(evImgDetected, "OnImageAnalyzed", "Event Handler", "Detecta mejoras.")
  Component(evAdhUpdate, "OnAdherenceCalculated", "Event Handler", "Actualiza adherencia.")

  Component(progressSvc, "ProgressComputationService", "Domain Service",
            "IMC, balance, adherencia.")
  Component(improveSvc, "ImprovementDetectionService", "Domain Service",
            "Detecta mejoras (reglas/IA).")
  Component(reportFactory, "ReportFactory", "Factory",
            "Construye reportes (DTO).")
  ComponentPort(imgAnalyzer, "ImageAnalyzer", "Port", "Análisis de imagen.")

  Component(metricsRepo, "MetricsRepository", "Repository Port", "")
  Component(workoutsRepo, "WorkoutsRepository", "Repository Port", "")
  Component(weeklyRepo, "WeeklyProgressRepository", "Repository Port", "")
  Component(photoRepo, "PhotoProgressRepository", "Repository Port", "")
}

%% ====== Relaciones externas ======
Rel_R(user, spa, "Usa", "HTTPS/JSON")
Rel_R(spa, metricsCtrl, "Consume", "HTTPS/JSON")
Rel_R(spa, workoutsCtrl, "Consume", "HTTPS/JSON")
Rel_R(spa, progressCtrl, "Consume", "HTTPS/JSON")
Rel_R(spa, reportsCtrl, "Consume", "HTTPS/JSON")
Rel_R(webhookCtrl, cmdIngestMetric, "Dispara", "Webhook")

%% ====== Flujos principales ======
Rel_R(metricsCtrl, cmdIngestMetric, "", "")
Rel_R(workoutsCtrl, cmdRecordWorkout, "", "")
Rel_R(progressCtrl, cmdSubmitPhoto, "", "")
Rel_R(progressCtrl, cmdAnalyzePhoto, "", "")
Rel_R(reportsCtrl, cmdExportReport, "", "")
Rel_R(cmdComputeWeek, progressSvc, "", "")
Rel_R(evImgDetected, improveSvc, "", "")

Rel_R(cmdIngestMetric, metricsRepo, "", "")
Rel_R(cmdRecordWorkout, workoutsRepo, "", "")
Rel_R(cmdSubmitPhoto, photoRepo, "", "")
Rel_R(cmdAnalyzePhoto, imgAnalyzer, "", "")
Rel_R(cmdComputeWeek, weeklyRepo, "", "")
Rel_R(cmdExportReport, reportFactory, "", "")

Rel_R(metricsRepo, dbTs, "Lee/Escribe", "SQL")
Rel_R(workoutsRepo, dbSql, "Lee/Escribe", "SQL")
Rel_R(weeklyRepo, dbSql, "Lee/Escribe", "SQL")
Rel_R(photoRepo, dbSql, "Lee/Escribe", "SQL")
Rel_R(imgAnalyzer, ml, "Analiza", "gRPC/REST")
Rel_R(photoRepo, blob, "Referencia", "URL/ID")

Rel_R(cmdIngestMetric, queue, "Publica eventos", "")
Rel_R(cmdRecordWorkout, queue, "Publica eventos", "")
Rel_R(cmdAnalyzePhoto, queue, "Publica eventos", "")
Rel_R(progressSvc, queue, "Publica progreso", "")

Rel_R(queue, evMetricProj, "Entrega", "")
Rel_R(queue, evWorkoutProj, "Entrega", "")
Rel_R(queue, evImgDetected, "Entrega", "")
Rel_R(queue, evAdhUpdate, "Entrega", "")
```

### 5.4.7. Bounded Context Software Architecture Code Level Diagrams

#### 5.4.7.1. Bounded Context Domain Layer Class Diagrams

```mermaid
classDiagram
direction LR

%% ==== Value Objects ====
class UserId {
  +value: UUID
}
class MetricName {
  +value: enum
}
class MetricUnit {
  +value: enum
}
class TimeWindow {
  +from: Date
  +to: Date
  +contains(d: Date): bool
}
class Week {
  +year: int
  +week: int
}
class AdherenceScore {
  +value: float
}
class CalorieBalance {
  +in: number
  +out: number
  +balance(): number
}
class PrivacyConsent {
  +granted: bool
  +grantedAt: Date
  +scope: enum[]
}
class DataRetentionPolicy {
  +ttlDays: int
  +minPrecision: float
}
class ImageRef {
  +storageId: string
  +mime: string
}

%% ==== Entities / Aggregates ====
class MetricSnapshot {
  +id: UUID
  +userId: UserId
  +name: MetricName
  +unit: MetricUnit
  +value: number
  +capturedAt: Date
}

class WorkoutSummary {
  +id: UUID
  +userId: UserId
  +type: string
  +startAt: Date
  +endAt: Date
  +caloriesOut: number
  +avgHr: number
}

class PhotoProgress {
  +id: UUID
  +userId: UserId
  +image: ImageRef
  +takenAt: Date
  +consent: PrivacyConsent
  +canAnalyze(): bool
}

class ImprovementFinding {
  +id: UUID
  +userId: UserId
  +week: Week
  +kind: enum
  +delta: number
  +confidence: float
}

class WeeklyProgress {
  +id: UUID
  +userId: UserId
  +week: Week
  +bmiAvg: number
  +weightDelta: number
  +calorieBalance: CalorieBalance
  +adherence: AdherenceScore
  +improvements: ImprovementFinding[*]
  +addMetric(ms: MetricSnapshot)
  +applyWorkout(ws: WorkoutSummary)
  +registerImprovement(f: ImprovementFinding)
  +computeKpis()
}

WeeklyProgress --> "0..*" ImprovementFinding
WeeklyProgress --> CalorieBalance
WeeklyProgress --> AdherenceScore
WeeklyProgress --> Week
PhotoProgress --> ImageRef
PhotoProgress --> PrivacyConsent
MetricSnapshot --> MetricName
MetricSnapshot --> MetricUnit
```

#### 5.4.7.2. Bounded Context Database Design Diagram

```mermaid
erDiagram
  USERS ||--o{ WORKOUTS : has
  USERS ||--o{ METRIC_SNAPSHOTS : has
  USERS ||--o{ PHOTO_PROGRESS : has
  USERS ||--o{ WEEKLY_PROGRESS : owns
  WEEKLY_PROGRESS ||--o{ IMPROVEMENT_FINDINGS : includes

  USERS {
    uuid id PK
    text email
    text name
  }

  WORKOUTS {
    uuid id PK
    uuid user_id FK
    text type
    timestamp start_at
    timestamp end_at
    numeric calories_out
    numeric avg_hr
  }

  METRIC_SNAPSHOTS {
    uuid id PK
    uuid user_id FK
    text metric_name
    text metric_unit
    numeric value
    timestamp captured_at
  }

  PHOTO_PROGRESS {
    uuid id PK
    uuid user_id FK
    text storage_id
    text mime
    boolean consent_granted
    text consent_scope
    timestamp consent_at
    timestamp taken_at
  }

  WEEKLY_PROGRESS {
    uuid id PK
    uuid user_id FK
    int year
    int week
    numeric bmi_avg
    numeric weight_delta
    numeric cal_in
    numeric cal_out
    numeric adherence
  }

  IMPROVEMENT_FINDINGS {
    uuid id PK
    uuid weekly_progress_id FK
    text kind
    numeric delta
    numeric confidence
  }
```

## 5.5. Bounded Context: Security Context

### 5.5.1. Domain Layer

<p align="justify">
El Domain Layer del contexto de <b>Seguridad</b> define las clases que representan las reglas de negocio relacionadas con la autenticación, autorización y gestión de roles de los usuarios dentro del sistema FitSense. Este dominio garantiza el control de acceso, la integridad de las credenciales y la trazabilidad de acciones mediante auditorías.
</p>

<p><b>Entidades de dominio</b></p>

<li>
    <b>Account:</b> Representa una cuenta de usuario. Contiene credenciales, estado de verificación y configuración de autenticación multifactor (MFA).
</li>

<li>
    <b>Role:</b> Define un rol dentro del sistema (por ejemplo, “User”, “Coach”, “Admin”) y sus permisos asociados.
</li>

<li>
    <b>Permission:</b> Representa una acción o recurso al cual puede acceder un rol (por ejemplo, <i>metrics:read</i> o <i>progress:write</i>).
</li>

<li>
    <b>Token:</b> Representa los tokens emitidos durante el proceso de autenticación (access y refresh tokens).
</li>

<li>
    <b>AuditLog:</b> Entidad encargada de registrar los eventos de seguridad relevantes como inicio de sesión, cambio de contraseña o asignación de roles.
</li> <br>

<p><b>Objetos de valor (Value Objects)</b></p>

<li>
    <b>AccountId:</b> Identificador único de una cuenta de usuario.
</li>

<li>
    <b>RoleName:</b> Valor inmutable que representa el nombre de un rol.
</li>

<li>
    <b>TokenType:</b> Define el tipo de token (ACCESS o REFRESH).
</li>

<li>
    <b>HashedPassword:</b> Valor protegido que representa la contraseña encriptada del usuario.
</li> <br>

<p><b>Agregados</b></p>

<li>
    <b>Authenticator:</b> Agregado raíz responsable de verificar credenciales, emitir tokens y gestionar la validez de las sesiones.
</li>

<li>
    <b>Authorizer:</b> Valida que un usuario tenga los permisos necesarios para acceder a un recurso, según su rol y estado.
</li> <br>

<p><b>Servicios de dominio</b></p>

<li>
    <b>AuthService:</b> Encargado de emitir y validar tokens JWT. Implementa las políticas de expiración y rotación definidas en <i>AuthPolicy</i>.
</li>

<li>
    <b>PasswordHasher:</b> Servicio responsable del cifrado y verificación de contraseñas usando algoritmos seguros (bcrypt o Argon2).
</li>

<li>
    <b>AuditService:</b> Encargado de registrar acciones críticas de seguridad (inicio de sesión, cambio de roles, fallos de autenticación).
</li>

<li>
    <b>AuthPolicy:</b> Define la configuración de tiempo de vida (TTL), reglas de rotación y alcance de los tokens.
</li> <br>

<p><b>Repositorios</b></p>

<li>
    <b>AccountRepository:</b> Gestiona la persistencia de las cuentas de usuario.
</li>

<li>
    <b>RoleRepository:</b> Administra la persistencia y consulta de roles y permisos.
</li>

<li>
    <b>TokenRepository:</b> Maneja los tokens activos y sus estados (revocado, expirado, vigente).
</li>

<li>
    <b>AuditLogRepository:</b> Persiste los registros de auditoría.
</li> <br>

---

### 5.5.2. Interface Layer

<p align="justify">
En esta capa se definen los puntos de entrada al contexto IAM. Los controladores manejan las solicitudes REST relacionadas con autenticación, registro y administración de roles. También se incluyen consumidores de eventos externos y callbacks de OAuth.
</p>

<li>
    <b>AuthController:</b> Administra las rutas de autenticación de usuarios:
    <ul>
        <li><i>POST /auth/register</i>: registro de nueva cuenta.</li>
        <li><i>POST /auth/login</i>: inicio de sesión con credenciales.</li>
        <li><i>POST /auth/refresh</i>: renovación del token de acceso.</li>
        <li><i>POST /auth/logout</i>: cierre de sesión y revocación de tokens.</li>
    </ul>
</li>

<li>
    <b>MfaController:</b> Gestiona la activación y verificación de autenticación multifactor.
</li>

<li>
    <b>RoleController:</b> Controla las operaciones CRUD de roles y asignaciones de permisos.
</li>

<li>
    <b>OAuthCallbackController:</b> Recibe las respuestas de los proveedores externos (Google, Apple, Facebook) y crea cuentas federadas.
</li>

---

### 5.5.3. Application Layer

<p align="justify">
El <b>Application Layer</b> orquesta los flujos de autenticación y autorización, manejando comandos y eventos que coordinan las operaciones entre las capas de dominio e infraestructura. Implementa los patrones <i>CQRS</i> y <i>Event-Driven</i> para separar responsabilidades y garantizar trazabilidad.
</p>

<p><b>Command Handlers:</b></p>

<li>
    <b>RegisterUserCommandHandler:</b> Procesa la creación de una nueva cuenta, encripta la contraseña y emite <i>AccountCreated</i>.
</li>

<li>
    <b>AuthenticateUserCommandHandler:</b> Valida credenciales, genera tokens y emite <i>UserAuthenticated</i>.
</li>

<li>
    <b>RefreshTokenCommandHandler:</b> Valida un token de refresco y emite nuevos tokens según la política.
</li>

<li>
    <b>ChangePasswordCommandHandler:</b> Actualiza la contraseña del usuario tras verificar las credenciales.
</li>

<li>
    <b>AssignRoleCommandHandler:</b> Asocia roles a una cuenta y emite <i>RoleAssigned</i>.
</li> <br>

<p><b>Event Handlers:</b></p>

<li>
    <b>OnAccountCreatedHandler:</b> Registra la creación de cuentas en <i>AuditLog</i>.
</li>

<li>
    <b>OnUserAuthenticatedHandler:</b> Emite eventos de sesión iniciada y registra auditoría.
</li>

<li>
    <b>OnRoleAssignedHandler:</b> Actualiza permisos y genera logs de seguridad.
</li> <br>

---

### 5.5.4. Infrastructure Layer

<p align="justify">
La capa de infraestructura implementa las interfaces de repositorios y adaptadores que permiten la comunicación con bases de datos, servicios externos de identidad y notificaciones de seguridad.
</p>

<p><b>Bases de datos:</b></p>

<li>
    <b>PostgreSQL:</b> Base de datos relacional para almacenar cuentas, roles, permisos y logs de auditoría.
</li>

<li>
    <b>Redis:</b> Almacenamiento temporal para tokens de acceso (blacklist y TTL).
</li> <br>

<p><b>Implementaciones de repositorios:</b></p>

<li>
    <b>AccountRepositorySql:</b> Implementa la persistencia de cuentas en PostgreSQL.
</li>

<li>
    <b>RoleRepositorySql:</b> Gestiona roles y permisos con relaciones N:M.
</li>

<li>
    <b>TokenRepositoryRedis:</b> Controla tokens activos en memoria (Redis).
</li>

<li>
    <b>AuditLogRepositorySql:</b> Guarda los eventos de auditoría en tabla append-only.
</li> <br>

<p><b>Adaptadores y servicios externos:</b></p>

<li>
    <b>PasswordHasherAdapter:</b> Implementación de <i>PasswordHasher</i> usando bcrypt o Argon2.
</li>

<li>
    <b>TokenProvider:</b> Generación y validación de JWTs (firma HMAC o RSA).
</li>

<li>
    <b>OAuthProviderAdapter:</b> Integración con Google o Apple mediante OAuth 2.0.
</li>

<li>
    <b>EmailNotificationAdapter:</b> Envía correos de recuperación de contraseña y alertas de inicio de sesión.
</li>

### 5.5.6. Bounded Context Software Architecture Component Level Diagrams
```mermaid
C4Component
title FitSense - Security Context (IAM) - Component Diagram

Person(user, "Usuario", "Se autentica en FitSense.")
Container(spa, "Web/Mobile Client", "React/Flutter", "Pantallas de login/registro.")
ContainerDb(authDb, "Auth DB", "PostgreSQL", "Cuentas, roles, auditoría.")
Container(cache, "Token Cache", "Redis", "Tokens activos / refresh.")
Container(email, "Email Service", "External", "Verificación y recuperación.")

%% ====== Auth API Boundary ======
Container_Boundary(authApi, "Auth API (NestJS/REST)") {

  Component(authCtrl, "AuthController", "Controller",
            "Login, refresh, logout, register.")
  Component(mfaCtrl, "MfaController", "Controller",
            "Activar/verificar MFA.")
  Component(roleCtrl, "RoleController", "Controller",
            "CRUD roles/permisos.")
  Component(oauthCtrl, "OAuthCallbackController", "Controller",
            "Login federado.")

  Component(cmdRegister, "RegisterUserHandler", "Command Handler", "")
  Component(cmdLogin, "AuthenticateUserHandler", "Command Handler", "")
  Component(cmdRefresh, "RefreshTokenHandler", "Command Handler", "")
  Component(cmdChangePwd, "ChangePasswordHandler", "Command Handler", "")
  Component(cmdAssignRole, "AssignRoleHandler", "Command Handler", "")

  Component(evAccountCreated, "OnAccountCreated", "Event Handler", "")
  Component(evUserAuth, "OnUserAuthenticated", "Event Handler", "")
  Component(evRoleAssigned, "OnRoleAssigned", "Event Handler", "")

  Component(authSvc, "AuthService", "Domain Service",
            "Emite/valida tokens y sesiones.")
  Component(policy, "AuthPolicy", "Strategy",
            "Expiración y rotación de tokens.")
  Component(hasher, "PasswordHasher", "Domain Service",
            "Hash/verificación (bcrypt/Argon2).")

  Component(accRepo, "AccountRepository", "Repository Port", "")
  Component(roleRepo, "RoleRepository", "Repository Port", "")
  Component(tokenRepo, "TokenRepository", "Repository Port", "")
  Component(auditRepo, "AuditLogRepository", "Repository Port", "")

  Component(jwtProv, "TokenProvider(JWT)", "Adapter", "Firmado/verificación.")
  Component(oauthProv, "OAuthProvider", "Adapter", "Google/Apple.")
  Component(emailAdapter, "EmailAdapter", "Adapter", "SMTP/API externa.")
  Component(tokenCache, "TokenCacheAdapter", "Adapter", "Redis.")
}

%% ====== Relaciones externas ======
Rel_R(user, spa, "Usa", "HTTPS/JSON")
Rel_R(spa, authCtrl, "Autentica", "HTTPS/JSON")
Rel_R(spa, oauthCtrl, "OAuth", "HTTPS/JSON")

Rel_R(accRepo, authDb, "Lee/Escribe", "SQL")
Rel_R(roleRepo, authDb, "Lee/Escribe", "SQL")
Rel_R(auditRepo, authDb, "Append", "SQL")
Rel_R(tokenCache, cache, "Guarda/Borra", "Redis")
Rel_R(emailAdapter, email, "Envía", "SMTP/API")

%% ====== Flujos internos ======
Rel_R(authCtrl, cmdLogin, "", "")
Rel_R(authCtrl, cmdRefresh, "", "")
Rel_R(authCtrl, cmdChangePwd, "", "")
Rel_R(authCtrl, cmdRegister, "", "")
Rel_R(roleCtrl, cmdAssignRole, "", "")
Rel_R(oauthCtrl, cmdLogin, "Callback", "")

Rel_R(cmdLogin, authSvc, "", "")
Rel_R(cmdRefresh, authSvc, "", "")
Rel_R(cmdChangePwd, hasher, "", "")
Rel_R(cmdRegister, hasher, "", "")

Rel_R(authSvc, jwtProv, "Firmar/validar", "")
Rel_R(authSvc, tokenRepo, "Persistir tokens", "")
Rel_R(authSvc, accRepo, "Buscar cuenta", "")
Rel_R(cmdAssignRole, roleRepo, "Asignar", "")
Rel_R(evAccountCreated, auditRepo, "Registrar", "")
Rel_R(evUserAuth, auditRepo, "Registrar", "")
Rel_R(evRoleAssigned, auditRepo, "Registrar", "")
Rel_R(authSvc, tokenCache, "Gestionar sesión", "")
```

### 5.5.7. Bounded Context Software Architecture Code Level Diagrams

#### 5.5.7.1. Bounded Context Domain Layer Class Diagrams

```mermaid
classDiagram
direction LR

%% ===== Value Objects =====
class AccountId { +value: UUID }
class RoleName { +value: string }
class TokenType { +value: string }
class HashedPassword { +value: string }

%% ===== Entities / Aggregates =====
class Account {
  +id: AccountId
  +email: string
  +password: HashedPassword
  +mfaEnabled: bool
  +status: string
  +enableMFA()
  +disableMFA()
  +changePassword(newHash: HashedPassword)
}

class Role {
  +id: UUID
  +name: RoleName
}

class Permission {
  +id: UUID
  +code: string
  +scope: string
}

class Token {
  +id: UUID
  +accountId: AccountId
  +type: TokenType
  +valueHash: string
  +expiresAt: Date
  +revoked: bool
}

class AuditLog {
  +id: UUID
  +accountId: AccountId
  +action: string
  +details: string
  +ip: string
  +occurredAt: Date
}

%% ===== Domain Services / Policy =====
class AuthPolicy {
  +accessTtl(): number
  +refreshTtl(): number
  +shouldRotate(now: Date, lastUsed: Date): bool
}

class AuthService {
  +issueTokens(account: Account): Token
  +validateCredentials(email: string, password: string): Account
  +refreshTokens(refreshToken: string): Token
}

class PasswordHasher {
  +hash(plain: string): HashedPassword
  +verify(plain: string, hashed: HashedPassword): bool
}

%% ===== Repository Interfaces (Ports) =====
class AccountRepository {
  +findByEmail(email: string): Account
  +save(account: Account): void
}

class RoleRepository {
  +findRolesByAccount(id: AccountId): Role
  +assignRole(accountId: AccountId, roleId: UUID): void
}

class TokenRepository {
  +store(token: Token): void
  +revoke(tokenId: UUID): void
  +findValidRefresh(accountId: AccountId): Token
}

class AuditLogRepository {
  +append(entry: AuditLog): void
}

%% ===== Associations =====
Account --> Role
Role --> Permission

Token --> AccountId
AuditLog --> AccountId
Account --> AccountId
Account --> HashedPassword

AuthService ..> AccountRepository
AuthService ..> RoleRepository
AuthService ..> TokenRepository
AuthService ..> PasswordHasher
AccountRepository <.. Account
Role *-- RoleName
Token *-- TokenType
```

#### 5.5.7.2. Bounded Context Database Design Diagram

```mermaid
erDiagram
  ACCOUNTS ||--o{ ACCOUNT_ROLES : has
  ROLES ||--o{ ACCOUNT_ROLES : has
  ROLES ||--o{ ROLE_PERMISSIONS : grants
  PERMISSIONS ||--o{ ROLE_PERMISSIONS : maps
  ACCOUNTS ||--o{ TOKENS : issues
  ACCOUNTS ||--o{ AUDIT_LOGS : generates

  ACCOUNTS {
    uuid id PK
    text email
    text password_hash
    boolean mfa_enabled
    text status
    timestamp created_at
    timestamp updated_at
  }

  ROLES {
    uuid id PK
    text name
  }

  PERMISSIONS {
    uuid id PK
    text code
    text scope
  }

  ACCOUNT_ROLES {
    uuid account_id FK
    uuid role_id FK
  }

  ROLE_PERMISSIONS {
    uuid role_id FK
    uuid permission_id FK
  }

  TOKENS {
    uuid id PK
    uuid account_id FK
    text type
    text value_hash
    timestamp expires_at
    boolean revoked
  }

  AUDIT_LOGS {
    uuid id PK
    uuid account_id FK
    text action
    text details
    text ip
    timestamp occurred_at
  }
```
