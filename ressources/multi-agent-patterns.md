# 🤖 Patterns Multi-Agents

Notes sur les architectures multi-agents et leur application.

---

## Vocabulaire

| Terme | Définition |
|-------|------------|
| **Agent** | LLM + outils + instructions spécialisées |
| **Orchestrateur** | Agent qui coordonne les autres |
| **State** | Données partagées entre agents |
| **Checkpoint** | Sauvegarde d'état pour reprise |

---

## Patterns courants

### 1. Sequential (Pipeline)

```mermaid
flowchart LR
    A[Agent 1] --> B[Agent 2] --> C[Agent 3] --> OUT[Output]
```

**Use case** : Tâches linéaires où chaque étape dépend de la précédente.

### 2. Parallel (Fan-out / Fan-in)

```mermaid
flowchart TB
    IN[Input] --> A1[Agent 1]
    IN --> A2[Agent 2]
    IN --> A3[Agent 3]
    
    A1 --> AGG[Aggregateur]
    A2 --> AGG
    A3 --> AGG
    
    AGG --> OUT[Output]
```

**Use case** : Tâches indépendantes qui peuvent être parallélisées.

### 3. Router (Conditional)

```mermaid
flowchart TB
    IN[Input] --> ROUTER{Router}
    
    ROUTER -->|Type A| A1[Agent Spécialisé A]
    ROUTER -->|Type B| A2[Agent Spécialisé B]
    ROUTER -->|Type C| A3[Agent Spécialisé C]
    
    A1 --> OUT[Output]
    A2 --> OUT
    A3 --> OUT
```

**Use case** : Requêtes de nature différente nécessitant des expertises différentes.

### 4. Hierarchical (Supervisor)

```mermaid
flowchart TB
    SUP[Supervisor] --> A1[Worker 1]
    SUP --> A2[Worker 2]
    SUP --> A3[Worker 3]
    
    A1 --> SUP
    A2 --> SUP
    A3 --> SUP
    
    SUP --> OUT[Output final]
```

**Use case** : Tâches complexes nécessitant coordination et validation.

### 5. Debate (Adversarial)

```mermaid
flowchart TB
    IN[Input] --> A1[Agent Pro]
    IN --> A2[Agent Contra]
    
    A1 <--> A2
    
    A1 --> JUDGE[Agent Juge]
    A2 --> JUDGE
    
    JUDGE --> OUT[Synthèse]
```

**Use case** : Décisions nécessitant des perspectives opposées.

---

## LangGraph vs LangChain

| Aspect | LangChain | LangGraph |
|--------|-----------|-----------|
| Paradigme | Chains linéaires | Graphs avec cycles |
| State | Limité | First-class citizen |
| Checkpoints | Non natif | Natif |
| Conditional logic | Callbacks | Edges conditionnels |
| Use case | Simple workflows | Complex multi-agent |

---

## Quand utiliser quoi ?

```mermaid
flowchart TB
    START[Besoin] --> Q1{Linéaire?}
    
    Q1 -->|Oui| CHAIN[LangChain suffit]
    Q1 -->|Non| Q2{Cycles/Loops?}
    
    Q2 -->|Non| SIMPLE[Simple agent + tools]
    Q2 -->|Oui| Q3{State partagé?}
    
    Q3 -->|Non| PARALLEL[Parallel processing]
    Q3 -->|Oui| LANGGRAPH[LangGraph]
```

---

## Notes perso

- Commencer simple (single agent) puis complexifier si besoin
- Le multi-agent ajoute de la latence et du coût
- Le state management est le vrai challenge
- Les checkpoints sont essentiels pour debug et reprise

---

*En cours d'enrichissement*
