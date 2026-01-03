# Module 2: Data Integration & Movement Architectures

## Module Intent

Explain how data moves across systems and why architectural choices create long-term consequences.

---

## Unit 2.1: ETL vs ELT vs Streaming

### Core Concepts

Understanding the fundamental approaches to data movement:

| Approach | Description | Best For |
|----------|-------------|----------|
| **ETL** | Extract, Transform, Load - transformation before loading | Legacy systems, structured data |
| **ELT** | Extract, Load, Transform - transformation after loading | Cloud data warehouses, big data |
| **Streaming** | Continuous real-time data flow | Event-driven architectures |

- **Transformation placement**: Where and when data is transformed affects cost and flexibility
- **Cost and latency trade-offs**: Batch processing is cheaper but slower; streaming is faster but more expensive
- **Governance implications**: Different approaches require different governance strategies

```mermaid
flowchart LR
    subgraph ETL["ETL Approach"]
        A1[Extract] --> A2[Transform]
        A2 --> A3[Load]
    end
    
    subgraph ELT["ELT Approach"]
        B1[Extract] --> B2[Load]
        B2 --> B3[Transform]
    end
    
    subgraph Streaming["Streaming"]
        C1[Source] --> C2[Stream]
        C2 --> C3[Process]
        C3 --> C4[Sink]
    end
    
    style A2 fill:#FF9800,color:#fff
    style B3 fill:#4CAF50,color:#fff
    style C2 fill:#2196F3,color:#fff
```

### AI / GenAI Sub-thread

!!! info "AI Integration"
    AI systems learn optimal pipeline designs by observing execution cost, query behavior, and downstream usage patterns.

```mermaid
flowchart TB
    A[Execution Metrics] --> D[AI Optimizer]
    B[Query Patterns] --> D
    C[Usage Data] --> D
    D --> E{Recommendation}
    E --> F[ETL Pipeline]
    E --> G[ELT Pipeline]
    E --> H[Streaming Pipeline]
    
    style D fill:#667eea,color:#fff
```

---

## Unit 2.2: Batch, Near-Real-Time, and Event-Driven Integration

### Core Concepts

Different integration patterns serve different business needs:

- **CDC (Change Data Capture)**: Captures and tracks data changes in source systems
- **Message queues**: Asynchronous communication between systems (Kafka, RabbitMQ)
- **Event schemas**: Structured definitions for event data formats

```mermaid
flowchart TB
    subgraph Batch["Batch Processing"]
        A1[Scheduled Job] --> A2[Full Extract]
        A2 --> A3[Bulk Load]
    end
    
    subgraph NRT["Near-Real-Time"]
        B1[CDC] --> B2[Micro-batches]
        B2 --> B3[Incremental Load]
    end
    
    subgraph Event["Event-Driven"]
        C1[Event Producer] --> C2[Message Queue]
        C2 --> C3[Event Consumer]
    end
    
    style A1 fill:#9C27B0,color:#fff
    style B1 fill:#FF9800,color:#fff
    style C2 fill:#4CAF50,color:#fff
```

### AI / GenAI Sub-thread

!!! info "AI Integration"
    ML detects event anomalies and predicts schema drift in streaming systems before failures occur.

```mermaid
flowchart LR
    A[Event Stream] --> B[ML Anomaly Detector]
    B --> C{Anomaly?}
    C -->|Yes| D[Alert]
    C -->|No| E[Continue]
    B --> F[Schema Drift Predictor]
    F --> G[Early Warning]
    
    style B fill:#667eea,color:#fff
    style D fill:#F44336,color:#fff
    style G fill:#FF9800,color:#fff
```

---

## Unit 2.3: Data Transformation & Standardization

### Core Concepts

Transforming raw data into usable formats:

- **Parsing**: Breaking down complex data structures into components
- **Normalization**: Standardizing data formats and values
- **Business rules**: Applying domain-specific logic to data

```mermaid
flowchart LR
    A[Raw Data] --> B[Parser]
    B --> C[Normalizer]
    C --> D[Business Rules Engine]
    D --> E[Standardized Data]
    
    style B fill:#2196F3,color:#fff
    style C fill:#4CAF50,color:#fff
    style D fill:#FF9800,color:#fff
    style E fill:#9C27B0,color:#fff
```

### AI / GenAI Sub-thread

!!! info "AI Integration"
    LLMs propose transformation logic directly from business language and historical correction patterns.

```mermaid
flowchart TB
    A[Business Requirements] --> C[LLM]
    B[Historical Patterns] --> C
    C --> D[Proposed Transformation Logic]
    D --> E[Human Review]
    E --> F[Deployed Rules]
    
    style C fill:#667eea,color:#fff
```

---

## Unit 2.4: Integration Error Handling & Observability

### Core Concepts

Managing failures in data pipelines:

| Component | Purpose |
|-----------|---------|
| **Rejections** | Records that fail validation rules |
| **Retries** | Automatic re-attempts for transient failures |
| **Dead-letter queues** | Storage for messages that cannot be processed |

```mermaid
flowchart TB
    A[Incoming Data] --> B{Validation}
    B -->|Pass| C[Process]
    B -->|Fail| D[Rejection Handler]
    C --> E{Success?}
    E -->|Yes| F[Target System]
    E -->|No| G{Retry?}
    G -->|Yes| C
    G -->|No| H[Dead Letter Queue]
    D --> I[Error Log]
    
    style B fill:#2196F3,color:#fff
    style H fill:#F44336,color:#fff
    style F fill:#4CAF50,color:#fff
```

### AI / GenAI Sub-thread

!!! info "AI Integration"
    AI-driven root cause analysis clusters failures using log embeddings instead of brittle keyword matching.

```mermaid
flowchart LR
    A[Error Logs] --> B[Log Embeddings]
    B --> C[Clustering Algorithm]
    C --> D[Failure Patterns]
    D --> E[Root Cause Analysis]
    E --> F[Recommended Fix]
    
    style B fill:#667eea,color:#fff
    style C fill:#9C27B0,color:#fff
    style E fill:#4CAF50,color:#fff
```

---

## Module Summary

This module covered the essential concepts of data integration and movement:

1. **Pipeline Architectures**: Understanding ETL, ELT, and streaming approaches
2. **Integration Patterns**: Batch, near-real-time, and event-driven strategies
3. **Transformation**: Parsing, normalization, and business rules
4. **Error Handling**: Building resilient pipelines with proper observability

!!! success "Key Takeaway"
    Architectural choices in data integration have long-term consequences. Understanding the trade-offs between different approaches is essential for building scalable, maintainable data systems.

---

**Next Module**: [Module 3 - Data Quality Engineering](module3.md)
