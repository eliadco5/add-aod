# Principles of AOD

Five pillars, each with an OOD-era pillar as its nearest analogue (see
[`comparison-to-ood.md`](comparison-to-ood.md) for the full mapping table).

## 1. Agents as units of responsibility

An agent in AOD is scoped the way a well-designed class is scoped: it has a clear responsibility,
a defined interface (its prompt/spec and its output contract), and it hides its internal
reasoning the way an object hides its internal state. You don't need to know *how* an agent arrived
at an answer to use it correctly — you need to know what it's responsible for and what it promises
to return.

Corollary: an agent with an unbounded, vague responsibility ("improve the codebase") is a design
smell, exactly like a God object. Split it.

## 2. Specification-driven delegation

Work is handed to an agent as an intent specification: preconditions, desired end state, and
constraints — not a step-by-step script. This is the AOD analogue of programming to an interface
rather than an implementation. The tighter and more testable the spec, the more autonomously the
agent can be trusted to operate against it.

A spec that can't be checked mechanically or reviewed quickly is not yet a spec — it's a wish.

## 3. Context engineering as encapsulation

What an agent can see determines what it can get right. AOD treats context assembly — which files,
which prior decisions, which constraints, which memory — as a deliberate design activity, not an
afterthought. Leaking irrelevant or stale context into an agent is the AOD equivalent of leaking
implementation details across a class boundary: it couples things that should have been independent
and makes failures hard to localize.

## 4. Verification loops as tests

Every piece of AOD output has a corresponding check that does not share its blind spots:

- A second agent prompted adversarially to find flaws, not confirm them.
- An automated test suite.
- A human review, scoped to the specific claim being made ("does this handle the concurrent-write
  case," not "read all 400 lines").

An agent's own self-report of success is not a verification loop. This is the AOD analogue of "if
it's not tested, it's broken."

## 5. Human checkpoints at points of irreversibility

Autonomy scales with reversibility. Reading, drafting, running tests, editing local files: default
to autonomous. Pushing, deploying, deleting, force-anything, spending money, contacting third
parties: default to a human checkpoint, regardless of how confident the agent is. This isn't a trust
judgment about the agent — it's a statement about who absorbs the cost of being wrong.
