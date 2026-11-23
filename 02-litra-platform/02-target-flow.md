# Target flow - one order, zero re-keying

> **In short:** six actors, three phases, one decision gate. The order is captured once and every later step reuses that data. Machine learning proposes the plan, the planner confirms. Trips that match the plan are priced and invoiced with no human touch; only exceptions reach a person.

## The whole flow on one page

```mermaid
flowchart LR
    subgraph P1["1 · Planning"]
        direction TB
        START(["Customer<br/>order"]):::term
        A["Validate against<br/>master data"]:::platform
        B["ML proposes plan<br/>within the rules"]:::platform
        C["Planner reviews<br/>and confirms"]:::role
        START --> A --> B --> C
    end

    subgraph P2["2 · Execution"]
        direction TB
        D["Driver: pre-trip check<br/>and loading"]:::role
        E["Digital waybill<br/>(e-CMR)"]:::platform
        F["Live tracking,<br/>ETA, alerts"]:::platform
        G["Driver: unload<br/>and POD"]:::role
        D --> E --> F --> G
    end

    subgraph P3["3 · Back-Office"]
        direction TB
        H["Reconcile planned<br/>vs actual"]:::platform
        I{"Within<br/>tolerance?"}:::decision
        J["Back-office<br/>reviews exception"]:::role
        K["Price by contract,<br/>create invoice"]:::platform
        UBW["UBW posts invoice<br/>and ledger entry"]:::ext
        DONE(["Customer gets<br/>invoice"]):::term
        H --> I
        I -->|"yes"| K
        I -->|"no"| J --> K
        K --> UBW --> DONE
    end

    P1 --> P2 --> P3

    classDef role fill:#F0F0FA,stroke:#695EFE,stroke-width:1.5px,color:#27273D
    classDef platform fill:#695EFE,stroke:#4C3EFE,stroke-width:1.5px,color:#FFFFFF
    classDef ext fill:#FFFFFF,stroke:#7E7EA6,stroke-width:1.5px,stroke-dasharray:5 4,color:#3A3A5A
    classDef decision fill:#FFF0AA,stroke:#FCB80A,stroke-width:1.5px,color:#27273D
    classDef term fill:#161626,stroke:#161626,color:#FFFFFF
```

**In plain words:** purple boxes happen automatically. Light boxes are where a person acts. People are left only where their judgement adds value: confirming the plan, driving and delivering, and handling odd cases.

**For the tech team:** the purple steps are the automation scope. Each one consumes the output of the previous step without manual input, so data contracts between modules matter more than screens.

## Who does what, phase by phase

The diagrams below read like swimlanes: each column is an actor, time runs downward.

### Phase 1 - Planning

```mermaid
sequenceDiagram
    participant CU as Customer
    participant FP as Fleet Planner
    participant PF as Platform
    participant DR as Driver

    CU->>PF: Order by EDI or API
    CU->>FP: Order by email or phone
    FP->>PF: Enters email and phone orders
    PF->>PF: Validates against master data, adds to inbox
    PF->>FP: Flags orders that need fixing
    PF->>PF: ML proposes an optimised plan within the rules
    FP->>PF: Reviews, adjusts or plans manually, confirms
    PF->>DR: Sends confirmed trip to the tablet
```

**In plain words:** most orders arrive by machine. The planner's job shifts from typing to checking.

**For the tech team:** validation runs at intake for every channel, so a broken site code is caught in the inbox, not at the customer's gate.

### Phase 2 - Execution

```mermaid
sequenceDiagram
    participant DR as Driver tablet
    participant PF as Platform
    participant TE as Telematics
    participant FP as Fleet Planner
    participant CU as Customer

    DR->>PF: Pre-trip check done
    DR->>PF: Loaded quantity, manifest OK
    PF->>DR: e-CMR created
    TE->>PF: GPS, km, idle, events
    PF->>CU: Status and ETA
    PF->>FP: Delay alert
    FP->>PF: Re-plan if needed
    DR->>PF: Status, waiting, incidents
    DR->>PF: Delivered quantity, POD
```

**In plain words:** the driver taps buttons instead of filling in paper. The truck reports itself. The customer knows the ETA without calling.

**For the tech team:** the tablet must work offline (tunnels, rural areas) and sync later. Telematics and tablet events are merged into one trip timeline.

### Phase 3 - Back-Office

```mermaid
sequenceDiagram
    participant PF as Platform
    participant BO as Back-Office
    participant UBW as UBW
    participant CU as Customer

    PF->>PF: Reconcile plan vs actual
    alt Within tolerance
        PF->>PF: Auto-approve, price
    else Outside tolerance
        PF->>BO: Exception with evidence
        BO->>PF: Accept or correct
    end
    PF->>PF: Create invoice
    opt Contract needs approval
        BO->>PF: Approve invoice
    end
    PF->>UBW: Post invoice and ledger
    UBW->>CU: Invoice sent
```

**In plain words:** the back-office stops doing arithmetic and starts reviewing only what looks wrong.

**For the tech team:** tolerances and approval rules are per contract and editable by an administrator, not hard-coded.

## The decision gate: "Within tolerance?"

This single question decides whether a trip is billed automatically.

| Check | Default tolerance |
|---|---|
| Distance | ±5% vs plan |
| Trip time | ±10%, after removing confirmed waiting |
| Quantity | ±0.5% loaded vs delivered |
| Waiting time | ±10 minutes between driver and telematics |
| Proof of delivery | Present at every stop |

> **Why it matters:** the share of trips that pass this gate *is* the ROI. If 80% pass, the back-office looks at 20% of trips instead of 100%.
