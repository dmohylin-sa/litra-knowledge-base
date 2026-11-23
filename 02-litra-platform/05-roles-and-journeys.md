# Roles and journeys - who uses the platform and how

> **In short:** six user types. The Fleet Planner and the Driver use it all day; the Back-Office handles exceptions and invoices; the Manager watches the numbers; the Administrator configures; the Customer gets updates now and a portal later.

## The six roles

| Role | Device | Main job | Biggest change vs today |
|---|---|---|---|
| **Fleet Planner** | Web, big screen | Turn orders into trips, watch them run | From typing and phoning to checking and deciding |
| **Driver** | Tablet in the truck (Android) | Load, drive, deliver, report | From paper waybills to taps and signatures |
| **Back-Office Specialist** | Web | Review exceptions, approve invoices, manage contracts | From Excel arithmetic to exception handling |
| **Manager** | Web | Operations overview, KPIs, CO₂, ROI | From late reports to live numbers |
| **Administrator** | Web | Users, roles, companies, tolerances, integrations | New role, owns the configuration |
| **Customer** | Email, SMS, API; portal in Phase 2 | Send orders, follow deliveries, get invoices | From calling to being told |

> **Assumption to confirm:** one Fleet Planner role covers both planning and dispatch. Some hauliers split these into two jobs.

## A day in the life: Fleet Planner

```mermaid
flowchart TB
    subgraph AM["Morning: today's trips"]
        direction LR
        A(["07:00"]):::term --> B["Open inbox:<br/>fix flagged orders"]:::role
        B --> C["Check live map:<br/>today's trips"]:::role
        C --> D{"Delay<br/>alert?"}:::decision
        D -->|"yes"| E["Re-plan stop order,<br/>customers get new ETA"]:::platform
    end
    subgraph PM["Afternoon: tomorrow's plan"]
        direction LR
        F["Generate plan<br/>for tomorrow"]:::platform --> G["Review proposals,<br/>override with comment"]:::role
        G --> H(["Send trips<br/>to drivers"]):::term
    end
    AM --> PM

    classDef role fill:#F0F0FA,stroke:#695EFE,stroke-width:1.5px,color:#27273D
    classDef platform fill:#695EFE,stroke:#4C3EFE,stroke-width:1.5px,color:#FFFFFF
    classDef decision fill:#FFF0AA,stroke:#FCB80A,stroke-width:1.5px,color:#27273D
    classDef term fill:#161626,stroke:#161626,color:#FFFFFF
```

**In plain words:** the planner spends the morning on today's surprises and the afternoon on tomorrow's plan, which the machine drafts.

**For the tech team:** the planning board is the most demanding screen: many orders, resources, a timeline and a map, updated live.

## A day in the life: Driver

```mermaid
flowchart TB
    subgraph S1["Start of shift"]
        direction LR
        A(["Log in<br/>with PIN"]):::term --> B["Pre-trip<br/>safety check"]:::role
        B --> C["Load at terminal:<br/>quantities, photo"]:::role
        C --> D["e-CMR created<br/>automatically"]:::platform
    end
    subgraph S2["On the road"]
        direction LR
        E["Drive: status,<br/>waiting, incidents"]:::role --> F["Deliver: quantity,<br/>pump, signature"]:::role
        F --> G{"More<br/>stops?"}:::decision
        G -->|"yes"| E
        G -->|"no"| H(["Finish trip:<br/>auto-reconciled"]):::good
    end
    S1 --> S2

    classDef role fill:#F0F0FA,stroke:#695EFE,stroke-width:1.5px,color:#27273D
    classDef platform fill:#695EFE,stroke:#4C3EFE,stroke-width:1.5px,color:#FFFFFF
    classDef decision fill:#FFF0AA,stroke:#FCB80A,stroke-width:1.5px,color:#27273D
    classDef term fill:#161626,stroke:#161626,color:#FFFFFF
    classDef good fill:#A7F3D0,stroke:#065F46,stroke-width:1.5px,color:#065F46
```

**In plain words:** big buttons, few steps, works with gloves on. The driver never types an address or a price.

**For the tech team:** offline-first. Every action is stored on the tablet and synced when there is signal. Language per driver (Norwegian, Swedish, English at least).

## A day in the life: Back-Office

```mermaid
flowchart TB
    subgraph EXC["Exceptions"]
        direction LR
        A["Open exceptions<br/>queue"]:::role --> B["See plan, telematics,<br/>driver report side by side"]:::platform
        B --> C{"Which<br/>value to bill?"}:::decision
        C --> D["Accept or correct,<br/>add comment"]:::role
    end
    subgraph INV["Invoices"]
        direction LR
        E["Approve invoices that<br/>need manual approval"]:::role --> F{"UBW<br/>accepted?"}:::decision
        F -->|"yes"| G(["Posted"]):::good
        F -->|"no, credit block"| H["Finance releases,<br/>retry"]:::risk
        H --> F
    end
    EXC --> INV

    classDef role fill:#F0F0FA,stroke:#695EFE,stroke-width:1.5px,color:#27273D
    classDef platform fill:#695EFE,stroke:#4C3EFE,stroke-width:1.5px,color:#FFFFFF
    classDef decision fill:#FFF0AA,stroke:#FCB80A,stroke-width:1.5px,color:#27273D
    classDef risk fill:#FECACA,stroke:#B91C1C,stroke-width:1.5px,color:#27273D
    classDef good fill:#A7F3D0,stroke:#065F46,stroke-width:1.5px,color:#065F46
```

**In plain words:** the back-office only touches trips that look wrong, and has all the evidence on one screen.

**For the tech team:** evidence means stored raw data per trip (telematics dwell, odometer, tablet events, photos), not just the final numbers.

## Manager and Administrator, briefly

- **Manager:** a control tower showing the pipeline from inbox to UBW, on-time rate, auto-reconciled share, delivery-to-invoice time, CO₂ per customer and an ROI view.
- **Administrator:** sets up companies (currency, VAT, language), roles and permissions, tolerances, notification templates, API clients; watches the integration log and the audit log.

## Access: role *and* company

A user sees only the data of their own operating company, and only the actions their role allows. A planner at Litra Gass Norway does not see Martinsen's customers. A group-level manager can see all companies.
