# Open-Core Model

## What Is Open, What Is Proprietary

The ClawMaven Open Governance Kit follows an **open-core model**. The foundational schemas, examples, checklists, and documentation in this kit are free and open under the Apache 2.0 license. The ClawMaven platform — which builds on top of these foundations — is a paid commercial product.

This document explains clearly what is included in the open kit, what remains proprietary, and why.

---

## What Is Free and Open

The following are fully open under Apache 2.0:

| Asset | Description |
|-------|-------------|
| `schemas/policy.schema.json` | JSON Schema for agent policy files |
| `schemas/trust-manifest.schema.json` | JSON Schema for agent trust manifests |
| `schemas/run-report.schema.json` | JSON Schema for per-run audit records |
| `examples/*/policy.json` | Example policy files for three agent types |
| `examples/*/trust-manifest.json` | Example trust manifests for three agent types |
| `examples/*/run-report.json` | Example run reports for three agent types |
| `checklists/pre-deployment-readiness.md` | Pre-deployment governance checklist |
| `checklists/spend-control.md` | Spend control checklist |
| `checklists/human-approval-gates.md` | Human approval gates checklist |
| `docs/what-is-agent-governance.md` | Primer on AI agent governance |
| `docs/open-core-model.md` | This document |

You can use, modify, redistribute, and build commercial products on top of these files without restriction. Attribution to ClawMaven is appreciated but not required.

---

## What Remains Proprietary

The following are exclusive to the [ClawMaven platform](https://clawmaven.com) and are **not** included in this kit:

### Guided Governance Wizard

The ClawMaven platform includes a 23-step interactive wizard that guides teams through the complete governance design process for an AI agent. It handles every field in every governance file, provides contextual guidance at each step, and produces a ready-to-deploy governance pack automatically.

The wizard's step logic, conditional branching, prompt engineering, and UI are proprietary.

### Posture Scoring Engine

ClawMaven's platform scores every generated governance pack on a 0–100 risk scale with letter grades (A–F). The scoring model weighs autonomy level, tool capabilities, spend limits, approval gate coverage, escalation completeness, and more than 40 other factors.

The scoring algorithm, weighting model, and grade thresholds are proprietary.

### Runtime-Specific Recommendations

The platform provides recommendations tailored to the specific agent runtime: LangChain, AutoGPT, CrewAI, OpenAI Assistants, custom, and others. These recommendations cover runtime-specific misconfigurations, known vulnerabilities, and deployment best practices.

The runtime recommendation database and logic are proprietary.

### Premium Templates

The platform includes pre-built governance templates for specialized agent types: Trading, DevOps, Healthcare, Legal, Customer Support, Content Generation, and more. Each template pre-populates policy and trust manifest fields with sensible defaults for that domain.

The premium template library is proprietary.

### Pack Validation and Diff Tools

The platform validates uploaded governance packs against current schemas, flags missing fields, and highlights risks. It also provides diff views to compare governance packs across versions or environments.

The validation engine and diff tooling are proprietary.

### Agent Monitor

ClawMaven's Agent Monitor provides live runtime telemetry for deployed agents: cost per run, risk score trends, escalation events, policy violation rates, and more. It surfaces anomalies and produces compliance-ready reports.

The monitoring infrastructure, telemetry schema, and analytics engine are proprietary.

### Signed Trust Manifests and Tamper-Evident Exports

The platform signs trust manifests with SHA-256 hashes and produces tamper-evident ZIP exports containing signed copies of every governance file. This provides cryptographic proof that governance files have not been altered after generation.

The signing infrastructure and export pipeline are proprietary.

### Compliance Reporting

The platform produces formatted compliance reports mapped to SOC 2, ISO 27001, GDPR, HIPAA, and EU AI Act requirements. These reports are designed to be submitted directly to auditors or used as evidence in compliance programs.

The report templates, control mappings, and export formats are proprietary.

### Team Accounts, RBAC, and Enterprise SSO

The platform supports multi-user team accounts, role-based access control for governance file review and approval workflows, and enterprise SSO integration (SAML, OIDC).

The account system, RBAC engine, and SSO integration are proprietary.

---

## Why Open Core?

Agent governance is most valuable when it is widely adopted. A fragmented landscape — where every team invents its own schema, every organization uses a different format, and no two governance packs look alike — makes it harder to share tooling, compare postures, and build a coherent ecosystem.

The open kit establishes a common baseline. It gives teams a structured starting point that is immediately useful, freely adoptable, and community-improvable. It lowers the barrier to getting governance in place.

The ClawMaven platform accelerates and deepens that governance for teams who need more: guided generation instead of manual authoring, automated scoring instead of manual review, runtime-specific expertise instead of generic checklists, and monitoring instead of post-hoc auditing.

---

## Using the Open Kit in Your Own Product

You are free to build products and services on top of the open kit. You may:

- Bundle the schemas in your own tooling
- Reference or extend the schemas in your own governance frameworks
- Build validators, linters, or generators that consume these schemas
- Include the examples and checklists in your own documentation

You may not represent your product as being affiliated with or endorsed by ClawMaven unless you have a written agreement to that effect.

If you build something useful on top of the open kit, we'd love to hear about it.

---

## Links

- **Platform:** https://clawmaven.com
- **Open kit repository:** https://github.com/clawmaven/agent-governance-kit
- **License:** Apache 2.0 (see `../LICENSE`)

---

*ClawMaven Open Governance Kit v0.1.0 · Apache 2.0 · https://clawmaven.com*
