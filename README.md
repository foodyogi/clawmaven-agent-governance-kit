# ClawMaven Open Governance Kit

**Version:** 0.1.0  
**License:** Apache 2.0  
**Maintained by:** [ClawMaven](https://clawmaven.com)

---

## What Is This?

The **ClawMaven Open Governance Kit** is a public starter standard for governing AI agents before and during deployment. It provides a minimal, practical set of schemas, examples, and checklists that any team can adopt — regardless of which framework, model, or infrastructure they use.

This kit defines a common vocabulary for AI agent governance: what a policy file should contain, what a trust manifest should declare, and what a run report should record. It is designed to be simple enough to use today and extensible enough to grow with your needs.

This is the open-core foundation. The full ClawMaven platform builds on top of it — see [Open-Core Model](./docs/open-core-model.md) for details.

---

## What Is Included

```
clawmaven-agent-governance-kit/
├── README.md                          ← This file
├── LICENSE                            ← Apache 2.0
│
├── schemas/
│   ├── policy.schema.json             ← JSON Schema: agent policy file
│   ├── trust-manifest.schema.json     ← JSON Schema: trust manifest
│   └── run-report.schema.json         ← JSON Schema: per-run audit report
│
├── examples/
│   ├── openclaw-basic/                ← Example: generic open-weight agent
│   │   ├── policy.json
│   │   ├── trust-manifest.json
│   │   └── run-report.json
│   ├── claude-code-basic/             ← Example: Claude Code agent
│   │   ├── policy.json
│   │   ├── trust-manifest.json
│   │   └── run-report.json
│   └── hermes-basic/                  ← Example: Hermes instruction-following agent
│       ├── policy.json
│       ├── trust-manifest.json
│       └── run-report.json
│
├── checklists/
│   ├── pre-deployment-readiness.md    ← Checklist before shipping an agent
│   ├── spend-control.md               ← Checklist for cost governance
│   └── human-approval-gates.md        ← Checklist for approval workflows
│
└── docs/
    ├── what-is-agent-governance.md    ← Primer on agent governance
    └── open-core-model.md             ← What is free vs. what is proprietary
```

---

## Who Is This For?

- **Developers** building AI agents who want a structured governance baseline
- **Platform teams** who need to enforce standards across multiple agents
- **Security and compliance teams** evaluating AI agent risk before deployment
- **Enterprises** that require documented policies, audit trails, and approval workflows
- **Anyone** shipping an autonomous or semi-autonomous AI system into production

You do not need to use the ClawMaven platform to use this kit. The schemas and checklists are standalone and framework-agnostic.

---

## How to Use It

### 1. Validate an agent against the policy schema

Use any JSON Schema validator with `schemas/policy.schema.json` to check whether your agent's policy file meets the baseline standard.

```bash
npx ajv-cli validate -s schemas/policy.schema.json -d your-agent/policy.json
```

### 2. Start from an example

Copy the closest example in `/examples` and adapt it to your agent:

```bash
cp -r examples/openclaw-basic my-agent-governance
```

Edit `policy.json`, `trust-manifest.json`, and `run-report.json` to match your agent's actual configuration, tools, and runtime.

### 3. Run the pre-deployment checklist

Before shipping any agent, work through `checklists/pre-deployment-readiness.md`. It takes less than 10 minutes and surfaces the most common governance gaps.

### 4. Commit your governance files alongside your agent code

Treat these files the same as infrastructure-as-code. They belong in your repository, reviewed in pull requests, and versioned with your deployments.

---

## What Remains Proprietary in the ClawMaven Platform

This kit is the open-core foundation. The following remain exclusive to the [ClawMaven platform](https://clawmaven.com) and are **not** included here:

- The guided 23-step Governance Wizard that generates all files automatically
- Automated posture scoring (0–100 risk grade A–F)
- Runtime-specific policy recommendations (LangChain, AutoGPT, CrewAI, etc.)
- Premium templates for specialized agent types (Trading, DevOps, Healthcare, etc.)
- Pack validation and diff tools
- Agent Monitor (live runtime telemetry, cost tracking, escalation events)
- Signed trust manifests (SHA-256) and tamper-evident audit exports
- Compliance reporting for SOC 2, ISO 27001, EU AI Act
- Team accounts, RBAC, and enterprise SSO

See [docs/open-core-model.md](./docs/open-core-model.md) for the full breakdown.

---

## Versioning

This kit uses [Semantic Versioning](https://semver.org). The current version is **0.1.0**.

Schema versions are tracked in each file under the `schema_version` field. When breaking changes are made to a schema, the major version increments.

---

## Contributing

This kit is open to contributions. If you have improvements to the schemas, useful example configurations, or checklist additions:

1. Fork the repository
2. Create a branch: `git checkout -b improve/policy-schema`
3. Make your changes and open a pull request
4. Include a clear description of what changed and why

Schema changes that break backward compatibility must include a migration note.

---

## License

Apache License 2.0. See [LICENSE](./LICENSE).

You are free to use, modify, and distribute this kit in commercial and non-commercial projects. Attribution appreciated but not required.

---

## Links

- **Platform:** https://clawmaven.com
- **Documentation:** https://clawmaven.com/docs
- **GitHub:** https://github.com/clawmaven/agent-governance-kit
