# AOD, mapped from OOD

OOD gave software design a vocabulary for organizing systems around objects. AOD borrows that
vocabulary's *shape* — not because AI agents are literally objects, but because the underlying
problem is similar: how do you decompose a large amount of work into pieces you can reason about,
verify, and compose, without any one piece needing global knowledge of the whole?

| OOD concept | AOD equivalent | Notes |
|---|---|---|
| Object | Agent (or agent invocation) | A unit with a scoped responsibility and its own "internal state" (context/reasoning) hidden from callers. |
| Class | Agent role / agent type | The reusable definition — "code-reviewer," "test-runner" — that gets instantiated per task. |
| Encapsulation | Context isolation | What's inside an agent's context window is deliberately curated; callers depend on the contract, not the internals. |
| Interface | Spec / prompt contract | Defines what must hold true on completion, without dictating implementation steps. |
| Inheritance | Skill/template reuse | A specialized agent role reuses a base prompt/skill and narrows or extends it. |
| Polymorphism | Model-agnostic behavior | The same role (e.g. "reviewer") can be filled by different underlying models and still satisfy the same contract. |
| Composition over inheritance | Orchestration over monolith | Prefer composing small agents via defined workflows (pipeline, fan-out, judge panel) over one agent doing everything. |
| Design patterns | Workflow patterns | Adversarial verify, judge panel, loop-until-dry, pipeline-vs-barrier — reusable shapes for composing agent work. |
| Unit test | Verification loop | A check, independent of the producer, that the producer's claim actually holds. |
| SOLID's Single Responsibility | Scoped agent responsibility | An agent should have one reason to be wrong. |
| God object (anti-pattern) | Unbounded agent task (anti-pattern) | "Fix the codebase" is to AOD what a 5,000-line class is to OOD. |
| Tight coupling (anti-pattern) | Context leakage (anti-pattern) | Feeding an agent irrelevant/stale context couples work that should be independent. |
| Access modifiers (public/private) | Autonomy boundary / checkpoint | What an agent may do unattended vs. what requires a human to invoke/approve. |

## Where the analogy breaks down

The mapping is a design aid, not a proof. A few places it doesn't hold cleanly:

- **Objects are deterministic; agents aren't.** An object's method, given the same state and
  inputs, returns the same output. An agent might not. This is *why* verification loops (pillar 4)
  are load-bearing in AOD in a way unit tests, while important, aren't quite as existential in OOD —
  in OOD a passing test stays passing; in AOD a passing check on one run doesn't guarantee the next.
- **There's no AOD equivalent of a compiler.** OOD gets static enforcement of its contracts (type
  systems, access modifiers). AOD's "contracts" (specs) are enforced by review and testing after the
  fact, not before invocation. This asymmetry is the strongest argument for keeping specs narrow and
  checks cheap.
- **Inheritance-style reuse is looser.** Skills and templates transfer *tendencies*, not guaranteed
  behavior, the way a subclass guarantees it satisfies its parent's interface.

Use the table as scaffolding for thinking about agent-based workflows, not as a literal 1:1 rulebook.
