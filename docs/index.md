---
title: Perilkeeper — code‑centric risk analysis
hide:
  - navigation
  - toc
---

# Cybersecurity, safety and quality risks as code

<div class="grid cards" markdown>

-   :sparkles: **For developers**

    Version-controlled risk description in DSL

-   :bar_chart: **For business**

    Actionable HTML/PDF risk report, diagrams, and diffs

-   :link: **Cross-component dependencies**

    Python-like import of damages, threats and attack/failure paths from other components

-   :shield: **Best practicies**
    
    Based on ISO 27005, ISO 21434, ISO 26262, etc.
</div>

## Have you run into...

- risk spreadsheet growing out-of-date with actual implementation?
- risk updates not propagating across several components?
- specialized risk management tools with cumbersome UI that few people know how to use?

__Discover the five steps to identify and treat your app's cybersecurity, safety and quality risks without becoming a certified expert that you can implement within one day!__

---

## Step 1. Describe business assets and assess damages

```console
BUSINESS FUNCTION "Payment Processing"
    DATA "Customer Payment Details"
        REQUIRES confidentiality, integrity   # guide words for deriving threats
        DAMAGE THROUGH "Payment Data Breach"
            BY Cybercriminal                  # could also be hacktivists, researchers, state actors etc.
            COMPROMISES confidentiality
            WITH IMPACT                       # damage impact level is derived from impact factors
                financial: High,
                operational: 3
        ...
```

## Step 2. Describe implementation assets

```console
SYSTEM "Payment Gateway"
    DEPENDS_ON "AWS Cloud"                    # enables reuse of threats and steps from other components
    IMPLEMENTS "Payment Processing"           # connects 
    API "PaymentAPI"
        RECEIVES "Customer Payment Order" WITH "Customer Payment Details"
        SENDS "Payment Confirmation"
    STORAGE "TransactionStorage"
        FOR "Customer Payment Order" WITH "Customer Payment Details"
```

## Step 3. List threats and attack/failure steps

```console
THREAT "Payment Data Theft"
    FROM Cybercriminal
    TO PaymentAPI                               # reference to implementation asset
    ACHIEVES "Payment Data Breach"              # reference to business damage
    THROUGH "SQL Injection"

ATTACK STEP "SQL Injection"
    COMES AFTER "Discover SQL Injection Point"  # intermediate steps are assembled using AND/OR statements
            AND "Exploit SQL Injection"
            AND "Extract Data"

ATTACK STEP "Discover SQL Injection Point"
    LIKELIHOOD                                  # leaf step likelyhood is derived from likelyhood factors
        skills_required: 3,
        window_of_opportunity: 12,
        resources_required: 1,
        knowledge_required: 4

ATTACK_STEP "Exploit SQL Injection"
    LIKELIHOOD
        skills_required: 6,
        window_of_opportunity: 24,
        resources_required: 3,
        knowledge_required: 5

ATTACK_STEP "Extract Data"
    LIKELIHOOD
        skills_required: 5,
        window_of_opportunity: 8,
        resources_required: 2,
        knowledge_required: 6
```

## Step 4. Calculate risks and produce a report
```console
$ perilkeeper gather assets.pkspec threats.pkspec
$ perilkeeper report --format pdf
```

## Step 5. Take a risk treatment decision

Lorem ipsum dolor sit amet...

---

## Learn more

[Explore the DSL »](language.md){ .md-button }
[See examples »](examples.md){ .md-button }
[Installation »](installation.md){ .md-button .md-button--primary }

Still evaluating? Jump to a use‑case walkthrough: **[From DSL to report in CI](use-cases.md)**.

