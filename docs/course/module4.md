# Module 4: Master Data Management (MDM)

## Module Intent

Establish enterprise-grade identity, consistency, and trust across core business entities.

---

## Unit 4.1: MDM Concepts & Styles

### Core Concepts

Different approaches to implementing Master Data Management:

| Style | Description | Data Location |
|-------|-------------|---------------|
| **Registry** | Pointers to source systems, no data copy | Distributed |
| **Consolidation** | Read-only master copy for analytics | Centralized copy |
| **Coexistence** | Bi-directional sync with sources | Hybrid |
| **Centralized** | Single authoritative source | Central hub |

```mermaid
flowchart TB
    subgraph Registry["Registry Style"]
        A1[Source A] --> A2[Registry Index]
        A3[Source B] --> A2
        A4[Source C] --> A2
    end
    
    subgraph Consolidation["Consolidation Style"]
        B1[Source A] --> B2[Master Hub]
        B3[Source B] --> B2
        B2 --> B4[Analytics]
    end
    
    subgraph Centralized["Centralized Style"]
        C1[Master Hub] --> C2[Source A]
        C1 --> C3[Source B]
        C1 --> C4[Source C]
    end
    
    style A2 fill:#2196F3,color:#fff
    style B2 fill:#4CAF50,color:#fff
    style C1 fill:#9C27B0,color:#fff
```

### AI / GenAI Sub-thread

!!! info "AI Integration"
    AI evaluates domain readiness and recommends MDM styles based on organizational maturity signals.

```mermaid
flowchart LR
    A[Maturity Assessment] --> B[AI Evaluator]
    B --> C{Readiness Level}
    C -->|Low| D[Registry]
    C -->|Medium| E[Consolidation]
    C -->|High| F[Centralized]
    
    style B fill:#667eea,color:#fff
```

---

## Unit 4.2: Identity Resolution & Matching

### Core Concepts

Techniques for identifying and linking related records:

- **Deterministic matching**: Exact matches on key fields
- **Probabilistic matching**: Fuzzy matching with confidence scores
- **Survivorship**: Rules for selecting the best value from multiple sources

```mermaid
flowchart TB
    A[Record A] --> C[Matching Engine]
    B[Record B] --> C
    C --> D{Match Type}
    D -->|Exact| E[Deterministic Match]
    D -->|Fuzzy| F[Probabilistic Match]
    E --> G[Confidence: 100%]
    F --> H[Confidence: 85%]
    G --> I[Link Decision]
    H --> I
    
    style C fill:#2196F3,color:#fff
    style E fill:#4CAF50,color:#fff
    style F fill:#FF9800,color:#fff
```

### AI / GenAI Sub-thread

!!! info "AI Integration"
    ML-based entity resolution leverages embeddings, phonetics, and contextual similarity.

```mermaid
flowchart LR
    A[Entity Data] --> B[Embedding Generator]
    B --> C[Vector Space]
    C --> D[Similarity Calculation]
    D --> E[Match Candidates]
    E --> F[Resolution Decision]
    
    style B fill:#667eea,color:#fff
    style C fill:#9C27B0,color:#fff
```

---

## Unit 4.3: Golden Records & XREF

### Core Concepts

Creating and maintaining the single version of truth:

| Concept | Description |
|---------|-------------|
| **Survivorship rules** | Logic for selecting best values |
| **Lineage** | Tracking data origin and transformations |
| **Traceability** | Ability to trace back to source records |

```mermaid
flowchart TB
    subgraph Sources["Source Records"]
        A1[CRM Record]
        A2[ERP Record]
        A3[Web Record]
    end
    
    A1 --> B[Survivorship Engine]
    A2 --> B
    A3 --> B
    B --> C[Golden Record]
    
    subgraph XREF["Cross-Reference Table"]
        D1[Source ID → Golden ID]
        D2[Lineage Metadata]
    end
    
    C --> XREF
    
    style B fill:#FF9800,color:#fff
    style C fill:#4CAF50,color:#fff
```

### AI / GenAI Sub-thread

!!! info "AI Integration"
    LLMs generate human-readable explanations for why a golden value was selected.

```mermaid
flowchart LR
    A[Golden Record] --> B[LLM Explainer]
    B --> C[Selection Rationale]
    C --> D[Audit Trail]
    C --> E[User Documentation]
    
    style B fill:#667eea,color:#fff
    style C fill:#4CAF50,color:#fff
```

---

## Unit 4.4: Hierarchies & Relationships

### Core Concepts

Managing complex entity relationships:

- **Parent-child**: Organizational structures, product categories
- **Network relationships**: Many-to-many connections
- **Temporal links**: Time-based relationship validity

```mermaid
flowchart TB
    subgraph Hierarchy["Parent-Child Hierarchy"]
        A1[Corporate HQ] --> A2[Region]
        A2 --> A3[Division]
        A3 --> A4[Department]
    end
    
    subgraph Network["Network Relationships"]
        B1[Customer] <--> B2[Supplier]
        B2 <--> B3[Partner]
        B3 <--> B1
    end
    
    subgraph Temporal["Temporal Links"]
        C1[Entity] --> C2[Relationship v1]
        C2 -->|Superseded| C3[Relationship v2]
    end
    
    style A1 fill:#9C27B0,color:#fff
    style B1 fill:#2196F3,color:#fff
    style C3 fill:#4CAF50,color:#fff
```

### AI / GenAI Sub-thread

!!! info "AI Integration"
    Graph ML detects hierarchy anomalies and infers missing relationships.

```mermaid
flowchart LR
    A[Entity Graph] --> B[Graph ML]
    B --> C{Analysis}
    C --> D[Anomaly Detection]
    C --> E[Missing Links]
    C --> F[Relationship Inference]
    
    style B fill:#667eea,color:#fff
    style D fill:#F44336,color:#fff
    style E fill:#FF9800,color:#fff
    style F fill:#4CAF50,color:#fff
```

---

## Module Summary

This module covered Master Data Management fundamentals:

1. **MDM Styles**: Registry, consolidation, coexistence, and centralized approaches
2. **Identity Resolution**: Deterministic and probabilistic matching techniques
3. **Golden Records**: Creating and maintaining the single source of truth
4. **Relationships**: Managing hierarchies and complex entity networks

!!! success "Key Takeaway"
    MDM provides the foundation for accurate and trustworthy reporting across the enterprise. The choice of MDM style should align with organizational maturity and business requirements.

---

**Next Module**: [Module 5 - Data Governance & Trust Frameworks](module5.md)
