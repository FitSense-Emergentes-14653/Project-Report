# Capítulo V: Tactical-Level Software Design

## 5.1. Bounded Context: Plan Context

### 5.1.1. Domain Layer

### 5.1.2. Interface Layer

### 5.1.3. Application Layer

### 5.1.4. Infrastructure Layer

### 5.1.6. Bounded Context Software Architecture Component Level Diagrams

### 5.1.7. Bounded Context Software Architecture Code Level Diagrams

#### 5.1.7.1. Bounded Context Domain Layer Class Diagrams

#### 5.1.7.2. Bounded Context Database Design Diagram

## 5.2. Bounded Context: Social Context

### 5.2.1. Domain Layer

### 5.2.2. Interface Layer

### 5.2.3. Application Layer

### 5.2.4. Infrastructure Layer

### 5.2.6. Bounded Context Software Architecture Component Level Diagrams

### 5.2.7. Bounded Context Software Architecture Code Level Diagrams

#### 5.2.7.1. Bounded Context Domain Layer Class Diagrams

#### 5.2.7.2. Bounded Context Database Design Diagram

## 5.3. Bounded Context: Notification Context

### 5.3.1. Domain Layer

### 5.3.2. Interface Layer

### 5.3.3. Application Layer

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
flowchart LR
  %% === Interface / Presentation ===
  subgraph API[Monitoring API (Interface Layer)]
    MCtrl[MetricsController]
    WCtrl[WorkoutsController]
    PCtrl[ProgressController]
    RCtrl[ReportsController]
    Webhook[ProviderWebhookController]
  end

  %% === Application Layer ===
  subgraph APP[Application Layer (CQRS + Events)]
    RWH[RecordWorkoutCommandHandler]
    IMH[IngestMetricCommandHandler]
    SPPH[SubmitProgressPhotoCommandHandler]
    APH[AnalyzePhotoCommandHandler]
    CWH[ComputeWeeklyProgressCommandHandler]
    EWRH[ExportWeeklyReportCommandHandler]

    OMRP[OnMetricRecordedProjector]
    OWRP[OnWorkoutRecordedProjector]
    OIAD[OnImageAnalyzedDetector]
    OACU[OnAdherenceCalculatedUpdater]
  end

  %% === Domain Layer ===
  subgraph DOMAIN[Domain Layer]
    WP[WeeklyProgress (Aggregate Root)]
    MS[MonitoringService <<DomainService>>]
    IDS[ImprovementDetectionService <<DomainService>>]
    RF[ReportFactory <<Factory>>]

    MR[MetricsRepository <<Interface>>]
    WR[WorkoutsRepository <<Interface>>]
    WPR[WeeklyProgressRepository <<Interface>>]
    PPR[PhotoProgressRepository <<Interface>>]
    IA[ImageAnalyzer <<Port>>]
  end

  %% === Infrastructure Layer ===
  subgraph INFRA[Infrastructure Layer]
    MRSQL[MetricsRepositorySql]
    WRSQL[WorkoutsRepositorySql]
    WPRSQL[WeeklyProgressRepositorySql]
    PPRSQL[PhotoProgressRepositorySql]

    TS[(Time-Series DB<br/>Timescale/Influx)]
    SQL[(Relational DB<br/>PostgreSQL)]
    BLOB[(Blob Storage<br/>Firebase/S3)]
    MB[(Message Broker<br/>Kafka/RabbitMQ)]
    TF[ImageAnalyzerTensorFlow]
    SCH[(Scheduler)]
    NOTI[(Notification Adapter)]
  end

  %% Flujos Interface -> App
  MCtrl --> IMH
  WCtrl --> RWH
  PCtrl --> SPPH
  PCtrl --> APH
  RCtrl --> EWRH
  Webhook --> IMH

  %% App -> Domain
  RWH --> WR
  IMH --> MR
  SPPH --> PPR
  APH --> IA
  CWH --> MS
  CWH --> WP
  EWRH --> RF

  %% Domain -> Infra (impl)
  MR --> MRSQL
  WR --> WRSQL
  WPR --> WPRSQL
  PPR --> PPRSQL
  IA --> TF

  %% Infra recursos
  MRSQL --> TS
  WRSQL --> SQL
  WPRSQL --> SQL
  PPRSQL --> SQL
  PPRSQL --> BLOB

  %% Eventing / Jobs / Notifs
  IMH --> MB
  RWH --> MB
  APH --> MB
  CWH --> MB

  MB --> OMRP
  MB --> OWRP
  MB --> OIAD
  MB --> OACU

  SCH --> CWH
  MB --> NOTI

### 5.4.7. Bounded Context Software Architecture Code Level Diagrams

#### 5.4.7.1. Bounded Context Domain Layer Class Diagrams

```mermaid
classDiagram
  direction LR

  %% ==== Value Objects ====
  class UserId { +value: UUID }
  class MetricName { +value: enum }
  class MetricUnit { +value: enum }
  class TimeWindow { +from: Date +to: Date +contains(d:Date) bool }
  class Week { +year: int +week: int }
  class AdherenceScore { +value: float <<0..1>> }
  class CalorieBalance { +in: number +out: number +balance(): number }
  class PrivacyConsent { +granted: bool +grantedAt: Date +scope: enum[] }
  class DataRetentionPolicy { +ttlDays: int +minPrecision: float }
  class ImageRef { +storageId: string +mime: string }

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

  %% ==== Domain Services & Factory ====
  class MonitoringService <<DomainService>> {
    +weeklyCalories(userId: UserId, tw: TimeWindow): number
    +adherence(userId: UserId, tw: TimeWindow): float
  }

  class ImprovementDetectionService <<DomainService>> {
    +detect(userId: UserId, week: Week): ImprovementFinding[*]
  }

  class ReportFactory <<Factory>> {
    +createReport(progress: WeeklyProgress): ProgressReport
  }

  %% ==== Repositories (Ports) ====
  class MetricsRepository <<Interface>> {
    +save(snapshot: MetricSnapshot)
    +findSeries(userId: UserId, name: MetricName, tw: TimeWindow): MetricSnapshot[*]
  }

  class WorkoutsRepository <<Interface>> {
    +save(summary: WorkoutSummary)
    +findByRange(userId: UserId, tw: TimeWindow): WorkoutSummary[*]
  }

  class WeeklyProgressRepository <<Interface>> {
    +get(userId: UserId, week: Week): WeeklyProgress
    +save(progress: WeeklyProgress)
  }

  class PhotoProgressRepository <<Interface>> {
    +save(photo: PhotoProgress)
    +findByWeek(userId: UserId, week: Week): PhotoProgress[*]
  }

  class ImageAnalyzer <<Interface>> {
    +analyze(img: ImageRef): AnalysisResult
  }

  %% ==== Associations ====
  MetricSnapshot --> UserId
  MetricSnapshot --> MetricName
  MetricSnapshot --> MetricUnit

  WorkoutSummary --> UserId
  PhotoProgress --> UserId
  PhotoProgress --> ImageRef
  PhotoProgress --> PrivacyConsent

  WeeklyProgress --> Week
  WeeklyProgress --> CalorieBalance
  WeeklyProgress --> AdherenceScore
  WeeklyProgress --> "0..*" ImprovementFinding

  MonitoringService ..> MetricsRepository : uses
  MonitoringService ..> WorkoutsRepository : uses
  ImprovementDetectionService ..> ImageAnalyzer : uses
  ReportFactory ..> WeeklyProgress : builds

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
    index (user_id, start_at)
  }

  METRIC_SNAPSHOTS {
    uuid id PK
    uuid user_id FK
    text metric_name
    text metric_unit
    numeric value
    timestamp captured_at
    index (user_id, metric_name, captured_at)
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
    index (user_id, taken_at)
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
    unique(user_id, year, week)
  }

  IMPROVEMENT_FINDINGS {
    uuid id PK
    uuid weekly_progress_id FK
    text kind
    numeric delta
    numeric confidence
  }

## 5.5. Bounded Context: Security Context

### 5.5.1. Domain Layer

### 5.5.2. Interface Layer

### 5.5.3. Application Layer

### 5.5.4. Infrastructure Layer

### 5.5.6. Bounded Context Software Architecture Component Level Diagrams

### 5.5.7. Bounded Context Software Architecture Code Level Diagrams

#### 5.5.7.1. Bounded Context Domain Layer Class Diagrams

#### 5.5.7.2. Bounded Context Database Design Diagram



