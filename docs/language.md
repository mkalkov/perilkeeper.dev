---
title: PerilSpec DSL
hide:
  - navigation
---

Perilscribe is a compact, SQL‑inspired language to describe components, risks, mitigations, and relationships.

## Core concepts
- **component**: a unit you build or operate
- **risk**: an unwanted outcome (threat, hazard, quality defect)
- **control**: a mitigation / requirement
- **link**: typed relation between entities

## Minimal example

```perilscribe
COMPONENT AuthService(kind=backend, criticality=high)
  INPUT user_credentials
  OUTPUT access_token

RISK CredentialTheft(category=cyber, stride=I)
  TARGET AuthService
  IMPACT confidentiality=high, integrity=medium, availability=low
  FEASIBILITY attacker=remote, complexity=low

CONTROL MFA(type=preventive)
  MITIGATES CredentialTheft
  REQUIRES AuthService
```

### SQL‑like form (alternative)
```sql
INSERT INTO component(name, kind, criticality)
VALUES ('AuthService', 'backend', 'high');

INSERT INTO risk(name, category, stride, target)
VALUES ('CredentialTheft', 'cyber', 'I', 'AuthService');

INSERT INTO control(name, type)
VALUES ('MFA', 'preventive');

INSERT INTO mitigates(control, risk) VALUES ('MFA','CredentialTheft');
INSERT INTO requires(control, component) VALUES ('MFA','AuthService');
```

## Validation rules (snapshot)
- every `RISK` must have at least one `TARGET`
- `CONTROL` → `RISK` must be typed as preventive/detective/corrective
- scoring = f(impact × feasibility), overridable per policy file

## Generated artifacts
- risk register (HTML/PDF/CSV)
- change diff between commits
- graphs (attack/impact trees)


