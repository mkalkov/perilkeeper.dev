---
title: Perilkeeper — code‑first risk analysis
hide:
- toc
---


# Meet **Perilkeeper**


A code‑centric way to model and manage cyber, safety, and quality risks — right inside your build.


> Describe your components in a simple DSL, and Perilkeeper turns them into actionable risk reports during CI.


<div class="grid cards" markdown>
- :sparkles: **For engineers first** — DSL in text, versioned, code‑reviewable.
- :rocket: **Build‑integrated** — runs in CI, fails fast on policy.
- :shield: **Cybersecurity‑aware** — maps to ISO 21434, UNECE R155, STRIDE, etc.
- :bar_chart: **Clear outputs** — HTML/PDF risk register, diagrams, and diffs.
</div>


## Quick glance


```console
# Define components & threats in repo
$ perilscribe components.yaml threats.yaml
# Get a report in CI
$ perilkeeper build --report out/report.html
```


[Explore the DSL »](language.md){ .md-button }
[See examples »](examples.md){ .md-button .md-button--primary }


---


## Who is it for?
- Developers & software architects
- Cybersecurity engineers
- Product owners who need traceable risk decisions


---


## What problems does it solve?
- scattered spreadsheets and hand‑wavy risk logs
- slow, manual sign‑offs
- hard‑to‑replicate expert decisions


---


## Try it locally


```bash
pipx install perilkeeper # or: pip install perilkeeper
perilkeeper init # scaffold demo project
perilkeeper build # produce a local report
```


---


Still evaluating? Jump to a use‑case walkthrough: **[From DSL to report in CI](use-cases.md)**.


