# OVERVIEW TIMELINE (12–16 weeks)

Phase   |	Output
---------------------------------
Phase 1	| Baseline paper selection

Phase 2	| Deep paper dissection

Phase 3	| Reproduction

Phase 4	| Gap identification

Phase 5	| Extension design

Phase 6	| Journal paper draft

# PHASE 1 — Choose the RIGHT baseline paper (CRITICAL)

## My baseline must satisfy all 4:

1. Agentic (planner / tool / memory)

2. Experimental (not just conceptual)

3. Reproducible (code or clear setup)

4. Weak on verification / safety / regression (this is my gap)

## Option A (BEST FIT)

“Self-Refine: Iterative Refinement with LLMs” (ICLR / NeurIPS-style)

Agents modify their own outputs

No hard guarantees

No regression control

No symbolic constraints

👉 Good baseline to extend into verified self-modification

## Option B

“Reflexion: Language Agents with Verbal Reinforcement Learning”

Agents learn from failure traces

Self-improvement loop exists

Completely heuristic and unsafe

👉 Great contrast point for “verified vs heuristic”

## Option C (Tool-focused)

“Toolformer” / “ReAct”

Tool-use policies learned

No safety or correctness verification

👉 Strong for tool-policy synthesis + constraints

# PHASE 2 — Deep paper dissection (1–2 weeks)

Before touching code, you must answer (in writing):

For the chosen paper:

1. What is the agent representation?

2. What is being modified (prompt? memory? policy?)

3. What is the learning signal?

4. What assumptions are implicit?

5. What is not measured?

6. Where can it fail silently?

7. Deliverable (to supervisor if asked)

A 2–3 page technical note:

“Critical Analysis of [Paper Name]”

# PHASE 3 — Reproduce the experiments (4–6 weeks)

This is where my supervisor’s trust is built.

### Reproduction checklist

* Clone code / reimplement minimal version

* Run the same benchmarks

* Match reported numbers (or explain deviation)

* Log failures and inconsistencies

### IMPORTANT

I do not need perfect replication.
I need:

1. honest reproduction

2. careful reporting

3. Deliverable

4. Reproduction report

5. Tables + plots

6. Notes on fragility / instability

👉 This naturally exposes research gaps

# PHASE 4 — Identify gaps (this becomes your problem statement)

After reproduction, gaps usually fall into buckets like:

## Gap	Example
1. No correctness guarantees	Agent learns bad behaviors
2. Silent regressions	Improves task A, breaks task B
3. Unsafe tool usage	Calls forbidden APIs
4. No interpretability	Cannot explain changes
5. No formal acceptance	Any change is accepted

#### verified synthesis engine fits here perfectly.

##### Example problem statement (early form)

“Existing self-refining agents rely on heuristic self-modification mechanisms that offer no guarantees on correctness, safety, or regression. This work addresses this limitation by…”

# PHASE 5 — Design a minimal extension (VERY IMPORTANT)

My first paper should NOT try to do everything.

Minimal, strong extension

Add one verification layer:

* typed DSL OR

* regression test gate OR

* symbolic tool constraints

Even just regression-safe acceptance is enough for Paper 1.

Example extension

Replace Reflexion’s “always accept reflection” with:
“Accept modification only if it passes symbolic checks + regression tasks”
