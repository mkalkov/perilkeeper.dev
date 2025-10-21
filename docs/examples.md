---
title: Examples
hide:
  - navigation
---

### 1) Microservice with auth and storage
```perilscribe
COMPONENT API(kind=frontend)
COMPONENT Auth(kind=backend)
COMPONENT DB(kind=stateful)
LINK API -> Auth (protocol=HTTPS)
LINK Auth -> DB (protocol=SQL)

RISK SQLInjection(category=cyber, stride=I)
  TARGET DB
CONTROL ORM_Escaping(type=preventive) MITIGATES SQLInjection
```

**Output:**
- STRIDE coverage: I threat mitigated by `ORM_Escaping`
- Residual risk: medium → low after control

---

### 2) Safety‑relevant controller
```perilscribe
COMPONENT MotorCtrl(kind=embedded, asil=C)
RISK Stall(category=safety, asil=C)
  TARGET MotorCtrl
CONTROL RedundantSensor(type=preventive) MITIGATES Stall
```

---

### 3) Quality risk in CI pipeline
```perilscribe
COMPONENT BuildPipeline(kind=ci)
RISK FlakyTests(category=quality)
CONTROL RetryLogic(type=corrective) MITIGATES FlakyTests
```


