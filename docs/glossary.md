# Glossary

**AOD (AI-Oriented Development)**
The design paradigm: organizing software development around agents, specs, context, and
verification loops as first-class units — parallel to how OOD organizes systems around objects.

**ADD (AI-Driven Development)**
The practice/process name for the same paradigm, parallel to Test-Driven Development — emphasizes
the day-to-day workflow of spec → delegate → verify.

**Agent**
A scoped unit of AI-driven work with a defined responsibility and output contract. Analogous to an
object in OOD.

**Intent specification ("spec")**
A statement of what must be true when a task is complete — preconditions, desired end state,
constraints — deliberately excluding step-by-step implementation instructions. Analogous to an
interface in OOD.

**Context engineering**
The deliberate curation of what information an agent has access to for a given task: what's
included, what's summarized, what's excluded. Analogous to encapsulation in OOD.

**Verification loop**
An independent check on an agent's output that does not share the producing agent's blind spots —
a test, an adversarial second agent, or a scoped human review. Analogous to a unit test in OOD/TDD.

**Autonomy boundary**
The explicit line between actions an agent may take unattended and actions that require a human
checkpoint, defined by reversibility and blast radius rather than by the agent's confidence.

**Workflow pattern**
A reusable shape for composing multiple agents to accomplish a task — pipeline, parallel fan-out,
adversarial verify, judge panel, loop-until-dry. Analogous to a design pattern in OOD.

**Unbounded agent task (anti-pattern)**
A task given to a single agent with a vague, sprawling responsibility ("improve the codebase") with
no clear spec or verification target. Analogous to a God object in OOD.

**Context leakage (anti-pattern)**
Feeding an agent irrelevant, stale, or contradictory context, coupling work that should have been
independent and making failures hard to localize. Analogous to tight coupling in OOD.
