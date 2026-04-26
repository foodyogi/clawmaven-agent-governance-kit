# Pre-Deployment Readiness Checklist

Use this checklist before deploying any AI agent to a production or staging environment. Work through every item. Do not skip sections for "simple" agents — the simplest agents have caused the most unexpected incidents.

**Agent name:** ___________________  
**Reviewed by:** ___________________  
**Date:** ___________________

---

## 1. Objective and Scope

- [ ] The agent has a clearly written objective that describes what it does and what it does **not** do.
- [ ] The scope of the agent's actions is explicitly bounded (no open-ended "do whatever it takes" instructions).
- [ ] The agent cannot be prompted by end-users to expand its own scope or modify its instructions.

---

## 2. Policy File

- [ ] A `policy.json` conforming to the governance schema exists and is committed to the repository.
- [ ] `autonomy_level` is explicitly set to `manual`, `balanced`, or `operator` — and the choice is justified.
- [ ] `allowed_actions` is a specific, bounded list. It does not contain wildcards or catch-alls.
- [ ] `restricted_actions` explicitly lists the actions this agent must never perform.
- [ ] `spend_limits` are set with per-run, daily, and monthly caps that have been reviewed and approved.
- [ ] `escalation_rules` are defined for at least: spend threshold, ambiguous objective, and repeated tool errors.
- [ ] `human_contact` is populated with a real name and active email address.

---

## 3. Trust Manifest

- [ ] A `trust-manifest.json` conforming to the governance schema exists and is committed to the repository.
- [ ] Every tool registered in `tool_access` has a description and correct `write_capable` value.
- [ ] Tools with side effects (write, send, delete, pay) have `requires_approval: true` unless a deliberate decision was made to exempt them — and that decision is documented.
- [ ] `network_access.blocked_domains` includes at minimum: `localhost`, internal network ranges (e.g., `169.254.169.254` for cloud metadata endpoints), and any domains the agent should never reach.
- [ ] `secrets_logged` is `false`. Confirm no logging path could expose secret values.
- [ ] `known_risks` is populated with honest risk entries — not left blank.

---

## 4. Data and Privacy

- [ ] The agent does not store PII beyond the duration of a single run unless explicitly designed to do so — and that design is reviewed and compliant with applicable privacy requirements.
- [ ] If `pii_access` is `true`, a data handling review has been completed.
- [ ] The agent's outputs do not echo back raw user-supplied data in logs without sanitization.
- [ ] Data retention for logs and run reports is explicitly configured (not default/indefinite).

---

## 5. Secrets and Credentials

- [ ] The agent accesses secrets only through environment variables or a dedicated secrets manager — never hardcoded values.
- [ ] API keys used by the agent have the minimum required permissions (principle of least privilege).
- [ ] API keys have been rotated within the last 90 days (or since the last deployment).
- [ ] There are no secrets checked into the repository (run a secret-scanning check).

---

## 6. Spend and Budget

- [ ] Someone on the team has reviewed and approved the spend limits in the policy file.
- [ ] Alerts are configured so the team is notified before the spend limit is hit (not after).
- [ ] The team knows which cost centre or billing account will be charged.
- [ ] A runaway-spend scenario has been considered: what happens if this agent is invoked 100x its expected rate?

---

## 7. Human Oversight

- [ ] There is at least one human who is responsible for reviewing this agent's output regularly.
- [ ] The escalation notification paths (email, Slack, etc.) have been tested and confirmed working.
- [ ] The team knows how to immediately halt the agent if something goes wrong (kill switch documented).
- [ ] A rollback plan exists if the agent needs to be disabled after deployment.

---

## 8. Testing

- [ ] The agent has been run against at least 5 representative tasks in a non-production environment.
- [ ] At least one adversarial prompt has been tested (e.g., instruction injection, scope-expansion attempt).
- [ ] The agent's behavior at the spend limit has been tested: does it halt cleanly?
- [ ] The escalation path has been tested end-to-end at least once.

---

## 9. Documentation

- [ ] There is a README or internal doc page explaining what this agent does, who owns it, and how to change it.
- [ ] The governance files (`policy.json`, `trust-manifest.json`) are version-controlled and change-reviewed.
- [ ] A review date is set in the policy file and entered into the team's calendar.

---

## Sign-off

| Role | Name | Date | Signature |
|------|------|------|-----------|
| Agent Owner | | | |
| Security Review | | | |
| Engineering Lead | | | |

---

*ClawMaven Open Governance Kit v0.1.0 · Apache 2.0 · https://clawmaven.com*
