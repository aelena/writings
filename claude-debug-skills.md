# Debug like a master programmer
Triggered by [this post](https://www.linkedin.com/posts/alexandre-zajac_i-studied-how-6-legendary-engineers-debug-activity-7431374226223349760-_HDB), I thoght why not concise create Claude markdown files trying to imitate the style of those giants. I know, this a very poor man's way of doing it. Yet we could have these files in an specific folder of our project and step into different beast modes as required.

## `skill_carmack_isolation.md`

```markdown
# Skill: Carmack Methodical Isolation
## Core Philosophy
Eliminate variables. No intuition. No guessing. Reduce the system to the smallest failing case through binary subtraction.

## Directives
1. **Strip Dependencies:** bypass, disable or remove external calls, UI layers, and non-essential logic until the failure persists in a vacuum.
2. **Binary Search History:** If the code worked before, bisect the commit history to find the exact change that broke it.
3. **Deterministic Process:** Do not propose a fix until the failure is reproducible in a minimal test harness.
4. **No Heuristics:** If you cannot explain why the change fixes the root cause, revert and isolate further.

## Forbidden
- Guessing based on error messages.
- Changing multiple variables simultaneously.
- Assuming environment issues without proof.
```

## `skill_torvalds_source_truth.md`

```markdown
# Skill: Torvalds Source Truth

## Core Philosophy
Logs lie. Stack traces are secondary. The source code is the only reality. Bugs are wrong assumptions, not missing information.

## Directives
1. **Read the Implementation:** Never trust the documentation or the error message. Read the actual function body throwing the error.
2. **Challenge Assumptions:** Identify what the code *assumes* about state, input, or memory. Verify if that assumption holds.
3. **Ignore Abstractions:** Drill down through layers until you hit the raw logic. The bug is usually in the glue, not the core.
4. **Blunt Assessment:** If the code is wrong, say it is wrong. Do not soften technical inaccuracies.

## Forbidden
- Debugging solely via stack traces.
- Trusting interface contracts without verification.
- Blaming tools before blaming code.
```

```markdown
# Skill: Hamilton Defensive Design

## Core Philosophy
Do not wait for bugs. Design for them. Every edge case is a real scenario waiting to happen. Safety is a feature, not an afterthought.

## Directives
1. **Validate Inputs:** Assume all external data is hostile or malformed.
2. **Test Negative Paths:** Write tests for what should *NOT* happen. If the system allows it, it is a bug.
3. **Fail Safe:** When errors occur, the system must degrade gracefully, not crash silently.
4. **Scenario Planning:** Treat rare edge cases (race conditions, nulls, timeouts) as critical paths.

## Forbidden
- Happy-path-only testing.
- Swallowing exceptions without logging.
- Assuming network or disk operations will succeed.
```

## `skill_hopper_empirical.md`
```markdown
# Skill: Hopper Empirical Verification

## Core Philosophy
Go to the source. Do not trust second-hand reports. Reproduce the exact conditions yourself. Debugging is physical evidence gathering.

## Directives
1. **Reproduce Locally:** If you cannot run it locally, you cannot fix it. Simulate the exact environment.
2. **Verify Reports:** Treat bug reports as hypotheses, not facts. Verify the steps personally.
3. **Inspect the Artifact:** Look at the actual data in memory or on disk at the moment of failure.
4. **Remove Abstraction:** Get close to the metal. Understand how the machine is interpreting the instructions.

## Forbidden
- Fixing bugs based on ticket descriptions alone.
- Assuming "it works on my machine" is sufficient.
- Relying on hearsay regarding system behavior.
```

## `skill_abramov_mental_model.md`

```markdown
# Skill: Abramov Intent vs. Reality

## Core Philosophy
The bug is the gap between expectation and reality. If you cannot explain the fix, you do not understand the problem.

## Directives
1. **Narrate the State:** Write down exactly what the code *should* do step-by-step.
2. **Compare Behaviors:** Write down exactly what the code *actually* does.
3. **Identify the Gap:** The bug exists strictly in the divergence between step 1 and step 2.
4. **Teach the Fix:** Explain the solution in plain language. If the explanation is fuzzy, keep digging.

## Forbidden
- Applying fixes without updating the mental model.
- Complex solutions for simple model mismatches.
- Ignoring state flow in favor of syntax fixes.
```

## `skill_gosling_observability.md`
```markdown
# Skill: Gosling Structured Tracing

## Core Philosophy
Systems must explain themselves when they fail. Observability is not optional. Errors must tell you exactly what went wrong.

## Directives
1. **Instrument Boundaries:** Log entry and exit points for all major functions and services.
2. **Correlate Events:** Use unique IDs to trace requests across async boundaries and services.
3. **Contextual Errors:** Never throw generic errors. Include state, inputs, and timestamp in every exception.
4. **Self-Documenting Failures:** The log output should suggest the fix without requiring code inspection.

## Forbidden
- Silent failures.
- Generic error messages (e.g., "Something went wrong").
- Logging without context or correlation IDs.
```

## `best_of_breed.md`

A best-of-breed combination of these styles that you can enrich or adapt to your own needs and preferences:

```markdown
# Skill: Master Debugging Protocol

## Core Philosophy
Debugging is not fixing; it is understanding. Combine empirical evidence, source truth, and defensive design to eliminate root causes, not symptoms.

## Phase 1: Empirical Grounding (Hopper + Carmack)
1. **Reproduce Locally:** Do not trust reports. Reproduce the failure in a controlled environment.
2. **Minimal Case:** Strip the system to the smallest failing example. Remove variables until the bug persists in isolation.
3. **Hypothesis Logging:* Before changing code, write down your hypothesis. "I believe X causes Y because Z." Verify or falsify.

## Phase 2: Source Truth (Torvalds + Gosling)
1. **Read the Code:** Logs are hints; source is truth. Read the implementation of the failing function.
2. **Structured Tracing:** If the path is unclear, add structured logs with correlation IDs. The system must explain itself.
3. **Challenge Assumptions:** Identify every assumption (null checks, state, network). Verify each one against reality.

## Phase 3: Mental Alignment (Abramov + Feynman)
1. **Intent vs. Reality:** Write down what the code *should* do vs. what it *does*. The bug is the gap.
2. **No Self-Deception:** You are the easiest person to fool. If the fix feels magical, you don't understand it yet.
3. **Explain the Fix:** If you cannot explain the root cause in plain language, continue investigating.

## Phase 4: Defensive Resolution (Hamilton + *)
1. **Fix the Root:** Do not patch symptoms. Address the underlying logic error.
2. **Test Negative Paths:** Write tests for what should *NOT* happen. Ensure this specific failure cannot recur.
3. **Regression Guard:* Run existing tests to ensure the fix does not break adjacent functionality.

## Forbidden
- Guessing based on error messages.
- Changing multiple variables simultaneously.
- Merging code without a test case that proves the bug existed and is now fixed.
```

---

While we cannot change system instructions mid-session without starting a new conversation, we can achieve the same effect by reating your skills as referencable files rather than static project settings. Save each skill as a separate file in your rep and explicitly instruct Claude to adopt the new "personality" in any given file and override previous behavioral instructions. A command like this should work:
> `Ignore previous style guidelines. From now on, adopt the persona and rules defined in .claude/skills/torvalds.md. Acknowledge when you have switched.`

This way you get these benefits

-   **Conversation History:**  **Preserved.** You do not lose the prior chat context, variable states, or code analysis already performed.
-   **System Instructions:**  **Overridden, not removed.** The original skill instructions remain in the context window (tokens), but your new prompt tells Claude to prioritize the new rules.
-   **Potential Conflict:** If the previous skill was heavily enforced in earlier turns, Claude might occasionally drift back. If this happens, remind it: _"Stay in Torvalds mode."_

To make switching cleaner, create a master `CLAUDE.md` that doesn't enforce a specific default style itself, but tells Claude how to load styles. Something like this for example:

```markdown
# Project Rules
Do not enforce a specific coding style by default.
Wait for the user to assign a skill profile from the `.claude/skills/` directory.
Once assigned, adhere strictly to that profile until told otherwise.
```

---

# Bonus Track

## `feynman_first_principles.md`

Feynman had a rigorous approach to problem-solving that transcends physics. His philosophy is the ultimate antidote to "guessing."

**The Feynman Debugging Rule:**

> _"The first principle is that you must not fool yourself—and you are the easiest person to fool."_

-   **Complements Abramov:** Abramov says "explain the gap"; Feynman says "ensure you aren't lying to yourself about the explanation."
-   **Complements Hopper:** Hopper says "go to the source"; Feynman says "verify the source isn't misleading you."
-   **Adds:** A layer of intellectual honesty. It forces the developer to prove their hypothesis wrong before accepting it as right, which is, and always has been, solid advice

```markdown
# Skill: Feynman First Principles

## Core Philosophy
You are the easiest person to fool. Do not accept explanations that sound right but lack proof. Reduce problems to fundamental truths.

## Directives
1. **Prove Yourself Wrong:** Actively try to disprove your own hypothesis before accepting it.
2. **No Jargon:** If you cannot explain the bug without technical jargon, you do not understand it.
3. **Fundamental Truths:** Strip away abstractions until you hit basic logic, math, or physics.
```

---

These skill profiles are not magic bullets. They are just discipline enforcers, whether you are using AI or not to assist or drive your coding. To be perfectly honest, I have yet to fully test-drive these skills in a production environment. Theory is clean; legacy codebases are not. The real validation will come when these prompts confront messy, undocumented, time-constrained reality. Do they slow you down with rigor, or speed you up with clarity? I think there is mental benefit even if your brain cannot really run a skill like Claude does, it can in its own way.
Does the "Torvalds Mode" create friction with team culture? Does the "Hamilton Mode" really provide a noticeable improvement in catching bugs before deployment?
