---
description: Run a structured idea evaluation with hard gates, a weighted scorecard, and a four-tier verdict (GO / TEST FIRST / NO-GO / PIVOT). Covers business ideas, real estate deals, and app builds.
---

# /is-this-a-good-idea

Load and follow the skill at `~/.claude/skills/is-this-a-good-idea/SKILL.md` exactly.

The idea to evaluate: $ARGUMENTS

Rules for this command context:

1. If `$ARGUMENTS` is empty, ask the user to describe the idea, who it serves, and what it would cost them to pursue (time, money, or both). Ask at most three questions total, then proceed with [ASSUMED] tags on gaps.
2. Run the full procedure from the skill: domain routing, hard gates, scorecard, cross-domain decision layer, verdict.
3. Display the full report in the conversation. Do not write any files unless the user explicitly asks for the report saved to disk. If asked, save to `_ideas/YYYY-MM-DD-<slug>.md` relative to the current working directory.
4. Honor the evidence protocol: pause on load-bearing unverified claims and offer the search-or-reasoning choice before continuing.
5. Apply the skill's tone directive and writing rules without exception.
