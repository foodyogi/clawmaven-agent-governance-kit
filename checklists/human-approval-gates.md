# Human Approval Gates Checklist

Human approval gates are the checkpoints where an AI agent must pause and wait for a person to review and authorize before proceeding. They are one of the most important safety mechanisms for autonomous agents. This checklist helps teams define, implement, and validate their approval gates.

**Agent name:** ___________________  
**Reviewed by:** ___________________  
**Date:** ___________________

---

## 1. Gates Are Defined in Policy

- [ ] The `approval_required_for` list in `policy.json` is explicitly populated — it is not empty.
- [ ] Every action category with external side effects requires approval: sending communications, writing to databases, triggering payments, making API calls that modify state.
- [ ] High-cost LLM actions (e.g., very large prompts, long chains) require approval if they could generate unexpected spend.
- [ ] Any action involving PII or sensitive data requires approval before the data is transmitted externally.

---

## 2. Gates Are Implemented in Code

- [ ] For every item in `approval_required_for`, there is a corresponding code path that halts execution and requests approval.
- [ ] The approval request includes enough context for the approver to make an informed decision (what, why, what happens if approved, what happens if denied).
- [ ] The agent cannot proceed without a positive approval response — a timeout or non-response results in the action being blocked, not defaulting to approval.
- [ ] Denied approvals are logged and the agent's run is marked as `halted_by_operator` in the run report.

---

## 3. Approvers Are Identified and Reachable

- [ ] Every approval gate has a defined approver (person or role) who will receive the request.
- [ ] Approvers have been told they may receive approval requests and understand what they mean.
- [ ] There is a backup approver if the primary is unavailable.
- [ ] Approval requests are delivered through a channel the approver actively monitors (not a mailbox they check once a week).

---

## 4. Approval Timeout Behavior Is Defined

- [ ] A maximum approval wait time is configured (e.g., 30 minutes, 2 hours, 24 hours — whatever is appropriate for the use case).
- [ ] When the approval window expires without a response, the agent defaults to blocking the action, not proceeding.
- [ ] Timeout events are logged and the appropriate party is notified.
- [ ] Urgent agents with short timeout windows have an on-call contact who can respond promptly.

---

## 5. The Approval Interface Is Usable

- [ ] The approver can understand the approval request without reading source code or logs.
- [ ] The approval interface clearly shows: what the agent wants to do, what data is involved, and the consequence of approving vs. denying.
- [ ] Approvals can be granted or denied through a simple, accessible channel (email reply, Slack button, web UI — not requiring system access).
- [ ] Approvers cannot be social-engineered into approving via prompt injection in the approval message (approval content is sanitized before display).

---

## 6. Audit Trail for Approvals

- [ ] Every approval request is logged with: timestamp, reason, who was asked, and what the action was.
- [ ] Every approval resolution (approved, denied, timed out) is logged with: timestamp, approver identity, and final decision.
- [ ] Approval logs are included in or linked from the agent's run report.
- [ ] Approval logs are retained for the same duration as other audit logs.

---

## 7. Gates Are Tested

- [ ] At least one test run has been executed in which an approval gate is triggered — confirm the request arrives correctly.
- [ ] At least one test has been run in which an approval is **denied** — confirm the agent halts cleanly.
- [ ] At least one test has been run in which an approval **times out** — confirm the agent blocks the action and notifies.
- [ ] A malformed or spoofed approval response has been tested — confirm it is rejected.

---

## 8. Autonomy Level Matches Gate Coverage

- [ ] If `autonomy_level` is `manual`: approval gates exist for every consequential action (not just edge cases).
- [ ] If `autonomy_level` is `balanced`: approval gates exist for all high-risk and side-effect actions; routine actions can proceed without approval.
- [ ] If `autonomy_level` is `operator`: approval gates are reserved only for policy violations, budget thresholds, and explicitly flagged escalations.
- [ ] The business and technical owners have reviewed and explicitly agreed on the `autonomy_level` choice.

---

*ClawMaven Open Governance Kit v0.1.0 · Apache 2.0 · https://clawmaven.com*
