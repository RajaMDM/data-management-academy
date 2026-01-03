# Module 1: Foundations of Data & Modern Data Sources

## Module Intent

Establish a rigorous mental model of what data is, where it comes from, and why context matters before any tooling discussion begins.

---

## Unit 1.1: What Is Data (Really)?

### Core Concepts

- **Structured data**: Highly organized data that fits neatly into tables (e.g., relational databases)
- **Semi-structured data**: Data with some organizational properties but not rigid schema (e.g., JSON, XML)
- **Unstructured data**: Data without predefined format (e.g., text documents, images, videos)
- **Operational vs analytical data**: Transactional data for day-to-day operations vs aggregated data for insights
- **Metadata vs data**: Data about data (schema, lineage, quality metrics) vs the actual content

```mermaid
flowchart TB
    subgraph DataTypes["Data Types"]
        A[Structured Data] --> D[Tables & Schemas]
        B[Semi-Structured Data] --> E[JSON, XML, YAML]
        C[Unstructured Data] --> F[Text, Images, Audio]
    end
    
    subgraph Purpose["Data Purpose"]
        G[Operational Data] --> I[Transactions]
        H[Analytical Data] --> J[Insights & Reports]
    end
    
    style A fill:#4CAF50,color:#fff
    style B fill:#FF9800,color:#fff
    style C fill:#F44336,color:#fff
    style G fill:#2196F3,color:#fff
    style H fill:#9C27B0,color:#fff
```

### AI / GenAI Sub-thread

!!! info "AI Integration"
    LLMs transform unstructured data (text, images, audio) into vector representations, enabling semantic search, similarity matching, and downstream analytics previously impossible with classical schemas.

```mermaid
flowchart LR
    A[Unstructured Data] --> B[LLM Processing]
    B --> C[Vector Embeddings]
    C --> D[Semantic Search]
    C --> E[Similarity Matching]
    C --> F[Analytics]
    
    style B fill:#667eea,color:#fff
    style C fill:#764ba2,color:#fff
```

---

## Unit 1.2: Systems of Entry, Record, and Reference

### Core Concepts

| System Type | Description | Example |
|-------------|-------------|---------|
| **System of Entry (SoE)** | Where data first enters the organization | Web forms, mobile apps, IoT sensors |
| **System of Record (SoR)** | Authoritative source of truth for specific data | ERP, CRM, HR systems |
| **System of Reference (SoRef)** | Provides context and lookup data | Master data repositories |

- **Trust boundaries**: Define where data ownership and responsibility change
- **Ownership**: Clear accountability for data quality and governance

```mermaid
flowchart LR
    subgraph Entry["System of Entry"]
        A1[Web Forms]
        A2[Mobile Apps]
        A3[IoT Devices]
    end
    
    subgraph Record["System of Record"]
        B1[ERP]
        B2[CRM]
        B3[HR System]
    end
    
    subgraph Reference["System of Reference"]
        C1[Master Data]
        C2[Reference Tables]
    end
    
    A1 --> B1
    A2 --> B2
    A3 --> B1
    B1 --> C1
    B2 --> C1
    B3 --> C2
    
    style A1 fill:#4CAF50,color:#fff
    style A2 fill:#4CAF50,color:#fff
    style A3 fill:#4CAF50,color:#fff
    style B1 fill:#2196F3,color:#fff
    style B2 fill:#2196F3,color:#fff
    style B3 fill:#2196F3,color:#fff
    style C1 fill:#9C27B0,color:#fff
    style C2 fill:#9C27B0,color:#fff
```

### AI / GenAI Sub-thread

!!! info "AI Integration"
    AI models infer system roles by analyzing data freshness, mutation frequency, access patterns, and lineage graphs instead of relying solely on documentation.

---

## Unit 1.3: Modern Data Sources Landscape

### Core Concepts

The modern data landscape encompasses diverse sources:

- **SaaS platforms**: Salesforce, Workday, ServiceNow, etc.
- **APIs and event streams**: REST APIs, GraphQL, Kafka, Pub/Sub
- **IoT and machine-generated data**: Sensors, logs, telemetry
- **External data providers**: Market data, weather, demographics

```mermaid
flowchart TB
    subgraph Internal["Internal Sources"]
        A[SaaS Platforms]
        B[APIs & Events]
        C[IoT Devices]
    end
    
    subgraph External["External Sources"]
        D[Data Providers]
        E[Public APIs]
        F[Partner Data]
    end
    
    A --> G[Data Platform]
    B --> G
    C --> G
    D --> G
    E --> G
    F --> G
    
    G --> H[Analytics]
    G --> I[ML/AI]
    G --> J[Reporting]
    
    style G fill:#667eea,color:#fff
    style H fill:#4CAF50,color:#fff
    style I fill:#FF9800,color:#fff
    style J fill:#2196F3,color:#fff
```

### AI / GenAI Sub-thread

!!! info "AI Integration"
    ML models classify data sources by volatility, reliability, and business impact using historical ingestion and consumption signals.

```mermaid
flowchart LR
    A[Data Source] --> B[ML Classifier]
    B --> C{Classification}
    C --> D[High Volatility]
    C --> E[Medium Volatility]
    C --> F[Low Volatility]
    
    style B fill:#667eea,color:#fff
    style D fill:#F44336,color:#fff
    style E fill:#FF9800,color:#fff
    style F fill:#4CAF50,color:#fff
```

---

## Unit 1.4: Data Contracts & Producer Responsibility

### Core Concepts

Data contracts establish formal agreements between data producers and consumers:

| Component | Description |
|-----------|-------------|
| **Schema contracts** | Define structure, types, and constraints |
| **Change management** | Processes for evolving schemas safely |
| **Data SLAs** | Service level agreements for quality, freshness, availability |

```mermaid
flowchart TB
    subgraph Producer["Data Producer"]
        A[Schema Definition]
        B[Quality Checks]
        C[Documentation]
    end
    
    subgraph Contract["Data Contract"]
        D[Schema Contract]
        E[SLA Terms]
        F[Change Policy]
    end
    
    subgraph Consumer["Data Consumer"]
        G[Validation]
        H[Integration]
        I[Monitoring]
    end
    
    A --> D
    B --> E
    C --> F
    D --> G
    E --> H
    F --> I
    
    style D fill:#667eea,color:#fff
    style E fill:#667eea,color:#fff
    style F fill:#667eea,color:#fff
```

### AI / GenAI Sub-thread

!!! info "AI Integration"
    GenAI auto-generates data contracts and flags breaking changes by comparing evolving schemas against historical consumer expectations.

```mermaid
flowchart LR
    A[Schema Changes] --> B[GenAI Analysis]
    B --> C{Breaking Change?}
    C -->|Yes| D[Alert & Review]
    C -->|No| E[Auto-Approve]
    D --> F[Manual Review]
    E --> G[Deploy]
    F --> G
    
    style B fill:#667eea,color:#fff
    style D fill:#F44336,color:#fff
    style E fill:#4CAF50,color:#fff
```

---

## Module Summary

This module established the foundational concepts for understanding data in modern organizations:

1. **Data Types**: Understanding structured, semi-structured, and unstructured data
2. **System Roles**: Distinguishing between Systems of Entry, Record, and Reference
3. **Data Sources**: Navigating the modern landscape of internal and external data sources
4. **Data Contracts**: Implementing formal agreements for data governance

!!! success "Key Takeaway"
    Before diving into tools and technologies, it's essential to build a strong mental model of what data is, where it originates, and how it flows through organizational systems.

---

**Next Module**: *Coming Soon* — Data Quality & Governance
