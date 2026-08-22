# Nicholas Leko

**Healthcare operations → healthcare AI product.**

I build healthcare AI systems around workflows I’ve worked inside: payer operations, emergency-department intake, clinical administration, and medical-device program readiness.

My focus is the part after the model demo: workflow fit, deterministic guardrails, evaluation, auditability, human review, refusal states, policy provenance, and failure modes.

[LinkedIn](https://www.linkedin.com/in/nicholas-leko/) · [Portfolio](https://github.com/NickLeko/PUBLIC_PORTFOLIO_HUB) · [GitHub Repositories](https://github.com/NickLeko?tab=repositories) · [nicholas.leko99@gmail.com](mailto:nicholas.leko99@gmail.com)

---

## Start here

### [Prior Authorization Readiness Copilot](https://github.com/NickLeko/PriorAuthorizationCopilot)

Prior authorization often breaks before medical necessity is even evaluated: missing documentation, payer-rule variation, policy drift, unclear handoffs, and requirements discovered too late.

I built a deterministic readiness engine that extracts structured facts from synthetic clinical documentation and evaluates them against versioned payer/procedure rules.

The decision path is inspectable:

**note evidence → extracted fact → rule/operator → requirement result → overall decision**

Outputs are explicitly bounded:

`READY` · `NOT_READY` · `CANNOT_DETERMINE` · `NEEDS_REVIEW`

One `Aetna:MRI_LUMBAR` pathway is mapped end-to-end to an official Aetna policy source, CPB 0236, with requirement-to-clause provenance and policy-drift monitoring. The cervical MRI, knee MRI, and CPAP pathways remain clearly labeled synthetic demos.

**What it demonstrates**

* Deterministic evaluation instead of free-form LLM adjudication
* Explicit rule operators and fail-closed behavior
* Requirement-level evidence traceability
* Versioned immutable payer-rule releases
* Official-policy provenance for one narrow Aetna pathway
* Policy source hashing and drift-aware trust
* Payer-qualified rule identity and procedure-scoped verification
* Adversarial extraction and regression testing
* Shared Streamlit, FastAPI, CLI, and artifact surfaces
* Explicit separation between readiness review and payer authorization

**Tech:** Python, FastAPI, Streamlit, YAML rules engine, pytest, GitHub Actions

![Prior Authorization Readiness Copilot showing a CANNOT\_DETERMINE result with explicit missing-documentation blockers](assets/readme/prior-auth-readiness-demo.png)

---

### [Clinical AI Eval Sandbox](https://github.com/NickLeko/clinical-AI-eval_sandbox)

Before a healthcare organization deploys an LLM into a clinical-adjacent workflow, someone has to answer a harder question than “does the demo look good?”:

**Where does it fail, when does it overstate, and how do we know?**

This project is a safety-oriented evaluation harness for structured clinical-style LLM outputs. It evaluates groundedness, citation fidelity, uncertainty calibration, refusal behavior, and failure modes, with reproducible run artifacts and reviewer-facing reports.

**What it demonstrates**

* Structured LLM evaluation design
* Groundedness and citation-fidelity checks
* Uncertainty and refusal-behavior evaluation
* Negation-sensitive safety testing
* Explicit PASS / WARN / FAIL review states
* Published run manifests and artifact provenance
* Reproducible benchmark outputs
* Qualitative review of evaluator failure modes
* Clear separation between benchmark results and clinical-safety claims

The checked-in canonical evaluation contains 25 scored cases with explicit provider, model, run ID, prompt version, raw generations, case-level scores, and flagged outputs.

**Tech:** Python, OpenAI / Anthropic / Gemini APIs, evaluation pipelines, CI/CD

---

### [ICU Code Blue Early Warning](https://github.com/NickLeko/icu-code-blue-early-warning)

Clinical prediction systems do not fail only because the model is weak. They fail when temporal validity, alert burden, workflow fit, and deployment constraints are treated as afterthoughts.

This project is a retrospective ICU risk-ranking case study using eICU-CRD with hospital-level holdout validation and fixed alert-budget evaluation.

The reference test set includes more than 2 million scored patient-hours across 31 held-out hospitals. At a fixed 0.5% alert budget, the selected rows showed **13.55× enrichment over test prevalence**.

The point is not the headline metric. The project explicitly analyzes what happens when model scores become alerts, including repeated-alert suppression and cooldown tradeoffs.

**What it demonstrates**

* Hospital-level held-out evaluation
* Temporal prediction framing
* Fixed alert-budget analysis
* Risk enrichment rather than accuracy theater
* First-crossing and cooldown alert-policy analysis
* BigQuery ML / SQL workflow
* Model-card and reproducibility documentation
* Explicit leakage, proxy-label, and deployment limitations

**Tech:** BigQuery ML, SQL, Python, eICU-CRD

---

## Supporting healthcare AI work

### [FHIR Referral Intake Review](https://github.com/NickLeko/FHIR-Referral-Intake-Review)

Deterministic review of synthetic FHIR referral bundles with source traceability, missing/ambiguous data detection, explicit human review, and audited final handoff artifacts.

### [Prior Auth Readiness Handoff Agent](https://github.com/NickLeko/prior-auth-readiness-handoff-agent)

A bounded LangGraph workflow that keeps readiness validation rules-first while using agent orchestration for routing, shared state, human review, and final handoff generation.

### [Daily AI Digest](https://github.com/NickLeko/daily-ai-digest)

Automated healthcare-AI signal triage and source review for tracking meaningful developments without treating every headline as equally important.

---

## How I build

I generally prefer:

**deterministic systems before probabilistic ones**
when the workflow can be expressed clearly as rules.

**refusal states over confident guesses**
when required evidence is missing or ambiguous.

**evaluation before deployment claims**
especially in healthcare.

**human review at real decision boundaries**
instead of adding HITL language after the architecture is finished.

**traceability over black-box confidence**
so a reviewer can understand what evidence produced an output.

**narrow claims over impressive-sounding claims**
because regulated products eventually have to survive contact with reality.

Across these projects, I focus on:

* Workflow boundaries
* Human-review assumptions
* Auditability
* Failure-mode analysis
* Policy and model provenance
* Reproducible artifacts
* Evaluation design
* Implementation risk
* Explicit non-claims

These are self-directed prototypes and research artifacts, not deployed clinical products.

---

## Background

I came into AI from healthcare operations rather than software engineering.

* **Stryker:** AED program administration, operational readiness, compliance workflows, customer onboarding, field-issue synthesis, and platform feedback across 300+ enterprise AED programs.
* **Blue Cross Blue Shield of Texas:** Small-group payer account management within a team supporting 60,000+ employer accounts, with exposure to retention strategy, claims/CRM analysis, HIPAA-aware operations, and payer-provider friction.
* **HCA Los Robles Hospital:** Emergency-department registration, patient intake, documentation workflows, and high-acuity operational environments.
* **Ventura Orthopedics:** Physical-therapy operations, scheduling, documentation support, and care coordination.

That background shapes what I build.

I’m less interested in making AI demos that look intelligent than in designing systems that could plausibly survive the operational, evaluation, governance, and human factors between a prototype and real healthcare implementation.
