# Spend Control Checklist

AI agents can generate significant and unexpected costs. LLM inference charges, external API calls, and runaway loops can produce bills that are orders of magnitude higher than expected. This checklist ensures your spend controls are in place before and during deployment.

**Agent name:** ___________________  
**Reviewed by:** ___________________  
**Date:** ___________________

---

## 1. Budget Is Defined

- [ ] A `per_run_usd` limit is set in the agent's `policy.json`.
- [ ] A `daily_usd` limit is set and reviewed against expected daily usage.
- [ ] A `monthly_usd` limit is set and agreed with the team or budget owner.
- [ ] The `alert_threshold_pct` is set to 75–80% so the team is warned before the limit is hit.
- [ ] Spend limits have been approved by whoever holds the budget for this agent.

---

## 2. Alerts Are Configured

- [ ] An alert fires when spend reaches the `alert_threshold_pct` of any limit (per-run, daily, or monthly).
- [ ] The alert goes to a person who can act on it — not just a shared inbox that no one monitors.
- [ ] The alert channel (email, Slack, PagerDuty, etc.) has been tested and confirmed working.
- [ ] A hard stop is enforced (not just an alert) when the per-run or daily limit is reached.

---

## 3. Token Usage Is Tracked

- [ ] Token counts (prompt + completion) are logged for every LLM call.
- [ ] The team knows the approximate token cost per run under normal conditions.
- [ ] Context window stuffing is prevented — the agent does not pass unbounded amounts of data to the LLM in a single call.
- [ ] Retry logic has a maximum retry count. The agent does not retry indefinitely on LLM errors.

---

## 4. External API Costs Are Accounted For

- [ ] All external APIs the agent calls that incur a cost have been identified.
- [ ] Per-call costs for each paid API are documented.
- [ ] Tool calls to paid external APIs are limited or rate-limited within the agent's logic.
- [ ] The agent cannot be triggered by user input in a way that causes it to call a paid API an unlimited number of times.

---

## 5. Loop and Runaway Prevention

- [ ] The agent has a maximum number of steps or iterations per run.
- [ ] The agent does not enter an infinite retry loop when a tool call fails.
- [ ] There is a wall-clock timeout on runs (e.g., 5 minutes max runtime).
- [ ] If the agent can spawn sub-agents or parallel tasks, the total spend across all children is governed and capped.

---

## 6. Monitoring and Reporting

- [ ] Spend is visible in a dashboard or report at least daily.
- [ ] Run-level spend data is included in every run report (`spend_used` block).
- [ ] There is a process for reviewing unexpected spend spikes within 24 hours.
- [ ] Monthly spend is reviewed against the approved budget at least once per month.

---

## 7. Incident Readiness

- [ ] The team knows how to immediately halt the agent if it is accumulating unexpected spend.
- [ ] The LLM provider account has billing alerts configured independently of the agent (provider-level safety net).
- [ ] There is a documented process for disputing or investigating unexpected charges.
- [ ] A post-incident review process is in place for spend incidents above a defined threshold.

---

*ClawMaven Open Governance Kit v0.1.0 · Apache 2.0 · https://clawmaven.com*
