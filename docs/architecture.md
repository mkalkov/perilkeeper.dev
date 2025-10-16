---
title: Architecture
---


- **Parser** for Perilscribe DSL → AST
- **Rules engine** (policy.toml) → scoring & checks
- **Aggregators** for AND/OR logic across attack paths
- **Renderers** → HTML/PDF/CSV/SVG


```mermaid
flowchart LR
A[DSL files] --> B(Parser)
B --> C(Rules Engine)
C --> D(Renderers)
C --> E(CI status)
```


**Integrations (planned):** Stripe/Lemon‑Squeezy for premium, Neo4j export, AI‑assisted scaffolding.




# -------------------------
# docs/pricing.md
# -------------------------
---
title: Pricing
---


- **Community** — free, MIT‑licensed
- **Premium** — advanced templates, compliance packs, priority support


> Want early access? Write at **founder@perilkeeper.dev**
