---
title: How it fits your workflow
---


## Typical flow (15 minutes)
1. **Write DSL** next to the code
2. **Run in CI** (GitHub Actions, GitLab CI, Jenkins)
3. **Review report** in PR: diffs, scores, required controls
4. **Gate the build** on policy (fail on high residual risk)


### GitHub Actions example
```yaml
name: Risk report
on: [push, pull_request]
jobs:
report:
runs-on: ubuntu-latest
steps:
- uses: actions/checkout@v4
- uses: actions/setup-python@v5
with: { python-version: '3.12' }
- run: pip install perilkeeper
- run: perilkeeper build --report out/report.html --strict
- uses: actions/upload-artifact@v4
with: { name: risk-report, path: out/report.html }
```


### Outputs you’ll get
- `/out/report.html` — interactive
- `/out/risk-register.csv` — spreadsheet‑ready
- `/out/graph.svg` — architecture/attack tree
