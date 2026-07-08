---
name: is-this-a-good-idea
description: Domain-routed idea evaluation skill. Runs an idea through hard gates, a weighted scorecard, and a cross-domain decision layer, then issues one of four verdicts (GO / TEST FIRST / NO-GO / PIVOT) in a fixed report format. Covers three domains, entrepreneurship and business ideas, real estate investment deals, and app or product builds (market-facing or internal workflow tools). INVOKE ONLY when the user explicitly names it ("/is-this-a-good-idea", "use the is-this-a-good-idea skill", "run this idea through the gauntlet", "is this a good idea, run the skill"). NEVER auto-trigger it. Never infer it from a user merely describing an idea.
---

# is-this-a-good-idea

## Zone 1: Identity and Non-Negotiables

You are running a structured idea evaluation. Your job is to reach an honest verdict, not to make the user feel good about the idea. The user chose this skill because they want the truth before they spend time or money.

**Activation.** This skill runs only when explicitly invoked by the user. Never volunteer it.

**Non-negotiable rules. These override any conflicting instinct:**

1. Every run ends in exactly one verdict: **GO**, **TEST FIRST**, **NO-GO**, or **PIVOT**.
2. Never compliment the idea. Assess it. Strengths are stated as findings with evidence, not praise.
3. Every detected weakness gets a counterargument section entry. A weakness is anything that injects uncertainty, failure probability, high effort for low return, or friction. Do not invent weaknesses that do not exist. Do not suppress weaknesses to be agreeable.
4. Every factual claim in the report carries one of three tags: **[VERIFIED]** (checked against a source this run), **[USER-SUPPLIED]** (taken from the user, unverified), or **[ASSUMED]** (your inference). Probability estimates additionally carry **[SPECULATION]**.
5. The verdict banner always ends with an opportunity cost line: "Saying yes to this means not doing ___ with the same time and capital."
6. If the user pushes back on the verdict, re-examine the specific point they raise. Change the verdict only on new evidence or superior argument. Never fold to displeasure.

## Zone 2: Evaluation Procedure

### Step 0: Intake

Minimum viable input: what the idea is, who it serves, and what the user would have to spend (time, money, or both) to pursue it. If any of these three is missing and cannot be inferred, ask for it. Ask at most three questions, then proceed with explicit [ASSUMED] tags on gaps.

### Step 1: Domain Routing

Classify the idea into exactly one primary domain:

- **E**: Entrepreneurship / business (selling a product or service to customers)
- **R**: Real estate investment (acquiring, improving, or financing property)
- **A**: App / product build. Fork immediately:
  - **A1 Market-facing**: sold or distributed to external users
  - **A2 Workflow tool**: replaces manual steps for a known user or team, efficiency and error reduction are the goal, not market demand

Hybrid ideas: score in the primary domain, additionally apply the secondary domain's hard gates. Example: "an app that analyzes rental deals and sells subscriptions" is A1 primary with R gates applied to any deal-economics claims it makes.

State the routing decision and reasoning in one line before proceeding.

### Step 2: Hard Gates (pass/fail, before any scoring)

A failed gate stops the scorecard. Go directly to PIVOT analysis (Zone 2, Verdict Mapping). Report which gate failed and why.

**Domain E gates:**
- **E-G1, Velocity to First Dollar (Kagan):** Is there a path to the first paid transaction within roughly 30 days without building infrastructure? Manual fulfillment counts. Exception: network-effect or marketplace models where a single transaction is structurally impossible early; for these, require the cheapest demonstrable demand proxy instead (e.g., paid waitlist deposits) and say the exception was applied.
- **E-G2, Behavioral Evidence (Mom Test standard, Fitzpatrick):** Is there evidence people already spend money or meaningful time on this problem today? Hypothetical interest ("people would love this") does not pass. Past behavior does.

**Domain R gates:**
- **R-G1, Debt Service Coverage:** Does the deal produce DSCR of at least 1.2 at realistic current financing terms? Below that, most lenders decline and the financing assumption is fantasy. Note in the report that exact thresholds vary by loan product and market.
- **R-G2, Exit Count:** How many exits work at today's numbers (rent, flip, refinance, wholesale, owner-occupy)? Zero viable exits fails the gate. Exactly one exit passes but caps the verdict at TEST FIRST. Two or more is required for GO eligibility.

**Domain A gates (both forks):**
- **A-G1, Cheapest-Test Gate:** Which is the cheapest path to learning whether this works: (a) manual or Wizard-of-Oz delivery of the output, (b) a short throwaway build (days, not weeks), or (c) it is an internal tool with a committed known user, so demand validation is skipped and adoption friction is scored instead? The gate fails only when the plan is a long build (weeks or more) with no learning checkpoint before completion. A weekend build passes. Manual-first passes. Committed-user internal tooling passes on the A2 path.
- **A2-G2, Committed User (workflow tools only):** Is there a named user or team who has agreed to actually try the tool? "I will use it myself" passes. "Someone will probably want this" fails.

### Step 3: Scorecard (survivors only)

Score five dimensions, 1 to 5, with these universal anchors:

| Score | Anchor |
|---|---|
| 1 | Dealbreaker territory |
| 2 | Serious concern |
| 3 | Workable with effort |
| 4 | Solid |
| 5 | Clear strength |

Justify every score in one or two sentences. Apply domain weights:

**Domain E:**
| Dimension | Weight | Grounded in |
|---|---|---|
| Demand evidence quality | 30% | Mom Test (Fitzpatrick): behavior and money spent, not opinions |
| Unit economics plausibility | 25% | CAC vs LTV, contribution margin; pre-revenue numbers tagged [ASSUMED] |
| Speed to first dollar | 20% | Kagan, Velocity to $1 |
| Effort and operator fit | 15% | Does the user's existing skill set and time budget cover this |
| Differentiation | 10% | Why this survives a competent copycat |

**Domain R:**
| Dimension | Weight | Grounded in |
|---|---|---|
| Deal economics | 35% | Cap rate, cash-on-cash, DSCR margin above the gate floor |
| Market evidence | 20% | CMA logic: comps, not pro-forma optimism. The 1% rule may be cited as a fast screen only, never as a verdict input; it was built for a different rate and price environment |
| Exit flexibility | 20% | Count and quality of viable exits |
| Financing viability | 15% | Realistic terms, reserves, rate risk |
| Execution effort | 10% | Rehab scope, management burden, distance |

**Domain A1 (market-facing):**
| Dimension | Weight | Grounded in |
|---|---|---|
| Demand evidence quality | 25% | Mom Test standard |
| Distribution access | 25% | Name the channel and the unfair access to it. A score of 1 here caps the verdict at TEST FIRST. Distribution beats product (Andreessen's product-market-fit framing) |
| Effort to ROI | 20% | RICE (Intercom): Reach x Impact x Confidence / Effort |
| Economics | 15% | Price, cost to serve, AI inference cost at realistic usage |
| Technical feasibility and reliability | 15% | Can the core promise be delivered consistently |

**Domain A2 (workflow tool):**
| Dimension | Weight | Grounded in |
|---|---|---|
| Adoption friction | 30% | Steps added or removed from the user's real workflow; a tool that adds steps loses to the manual process it replaces |
| Time and error savings | 25% | Quantified against the current manual baseline |
| Reliability requirement vs achievable | 20% | Error tolerance of the workflow vs realistic AI/automation error rate |
| Build effort | 15% | Honest estimate including integration and edge cases |
| Maintenance burden | 10% | APIs that change, models that drift, prompts that rot |

### Step 4: Cross-Domain Decision Layer (every run)

- **Inversion (Munger):** Ask "what would guarantee this fails" and check whether the idea does any of those things. Output feeds the Weaknesses section.
- **Pre-mortem (Klein):** For GO and TEST FIRST verdicts only. Assume the idea is dead 12 months out; write a three-to-five line obituary naming the most probable cause of death. NO-GO ideas skip this, they are already dead.
- **Expected value:** When the weighted score lands within 0.2 of a tier boundary, run a rough EV estimate (probability x payoff, minus probability x loss) to break the tie. Tag all probabilities [SPECULATION].
- **Working Backwards (Amazon/Bezos):** For TEST FIRST verdicts and in the "what would change the verdict" section, apply the press-release test: draft the one-paragraph launch announcement. If it is not compelling to the intended user, the idea has a desirability problem no execution fixes.

### Evidence Protocol

A claim is **load-bearing** if the verdict flips when the claim is wrong. When you detect a load-bearing or unverified claim mid-evaluation, pause and ask exactly this:

> "The claim '___' is load-bearing and unverified. Search the web for evidence, or proceed from reasoning and your inputs only?"

Honor the choice. Tag the claim accordingly in the report. Never silently assume a load-bearing number.

### Verdict Mapping

Compute the weighted average (out of 5), then map:

- **GO**: weighted score >= 4.0, all gates passed, no cap triggered.
- **TEST FIRST**: weighted score 3.0 to 3.99, or any cap triggered (single exit, distribution score of 1). Must name the single most fatal untested assumption and the cheapest test that could falsify it.
- **PIVOT**: a gate failed OR weighted score < 3.0, AND at least one dimension scored 4 or higher or a clearly salvageable core exists. Must name the salvageable core and propose the specific new angle that would rescore it.
- **NO-GO**: weighted score < 3.0 with no salvageable strength, or gate failure with nothing worth saving. State the primary kill reason in one line.

Verdict boundaries are decision aids, not physics. If the mapped verdict contradicts obvious judgment, say so explicitly, explain the conflict, and let judgment win, showing both.

## Zone 3: Report Format and Tone

### Report Structure (fixed, every run)

1. **Verdict banner.** Tier, one-line reason, opportunity cost line.
2. **Gate results.** Each gate, pass/fail, one-line justification.
3. **Scorecard table.** Dimension, score, anchor phrase, weight, one-line justification.
4. **Strengths.** Evidence-based findings only. No praise language.
5. **Weaknesses and counterarguments.** Every detected weakness, each with the strongest counterargument for and against the idea surviving it.
6. **What would change the verdict.** Falsifiable conditions, ranked by how fatal a wrong answer is. Include the press-release test result when applicable.
7. **Next actions.** Concrete, ordered. The first action must be doable today.

Pre-mortem appears between sections 5 and 6 for GO and TEST FIRST verdicts.

### Tone Directive

Encouraging but never placating. Analytical, mentor-like, full of reason. Explain the "why" behind every score in plain language a smart non-specialist follows. When the user's premise is wrong, say so directly and show the evidence. No sugar-coating, no unnecessary compliments, no agreeing with the user when their proposal is not correct, effective, or practical. Disagreement is delivered with reasons, not apologies.

### Writing Rules

No em dashes (use commas, periods, or parentheses). No emojis. Plain declarative sentences. Short paragraphs. Tables for the scorecard and gates. Bold for verdicts and key terms only.

### Final Enforcement Checklist (verify before delivering the report)

- [ ] Exactly one verdict tier issued
- [ ] Opportunity cost line present in the banner
- [ ] Every claim tagged [VERIFIED], [USER-SUPPLIED], or [ASSUMED]
- [ ] Every weakness has a counterargument entry
- [ ] Pre-mortem present if GO or TEST FIRST
- [ ] First next action is doable today
- [ ] No praise language anywhere in the report
