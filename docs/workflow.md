# The ADD workflow

This is what "doing ADD" looks like in practice — the loop, the artifacts it produces, and the
checkpoints it passes through. It's the operational counterpart to the principles in
[`principles.md`](principles.md).

## The loop

1. **Frame the intent spec.** Before any agent touches code, write down: what must be true when
   this is done, what constraints apply (performance, compatibility, style), and what's explicitly
   out of scope. This is the interface the agent implements against. If you can't state a testable
   end condition, you're not ready to delegate — narrow the task or do it yourself first.

2. **Scope the agent(s).** Decide whether this is a single-agent task or should be decomposed into
   multiple scoped agents composed via a workflow pattern (see below). Bias toward decomposition
   once a task has more than one kind of "this could be wrong" failure mode.

3. **Assemble context deliberately.** Give the agent exactly what it needs to satisfy the spec:
   relevant files, prior decisions, constraints — and nothing that's stale, contradictory, or
   irrelevant. Context assembly is a design step, not a formality.

4. **Execute.** Let the agent(s) do the work. Reversible, local actions proceed without a
   checkpoint. Anything crossing the autonomy boundary (see below) pauses for a human decision.

5. **Verify independently.** Run the check that doesn't share the producer's blind spots: tests,
   an adversarial second agent, or a scoped human review against the original spec — not a general
   "does this look okay" skim. The question is always "does this satisfy the spec from step 1,"
   not "does this look plausible."

6. **Decide, don't rubber-stamp.** A human (or a higher-authority verification step) makes the
   accept/reject/revise call. If revising, the loop restarts at whichever step the failure traces
   back to — usually the spec was underspecified, or the context was wrong, not that the agent is
   "bad."

## Common workflow patterns (the AOD equivalent of design patterns)

- **Pipeline.** Independent stages, each agent's output feeding the next, with no artificial
  synchronization between items. Default shape for most multi-step work.
- **Parallel fan-out + barrier.** Multiple agents attack the same problem from different angles;
  results are collected together *only* when a later step genuinely needs all of them at once
  (e.g., deduplication before expensive verification).
- **Adversarial verify.** N independent agents are asked to *refute* a claim/finding rather than
  confirm it; the claim survives only if a majority fail to refute it. Directly implements pillar 4.
- **Judge panel.** Multiple independent attempts at a problem, scored by independent judges,
  synthesized from the best one rather than iterating a single attempt to death.
- **Loop-until-dry.** For open-ended discovery (bugs, edge cases, unknowns), keep spawning finders
  until several consecutive rounds surface nothing new — a fixed round count silently misses the
  tail.

## The autonomy boundary

Every ADD workflow should have an explicit answer to: *what can proceed without a human, and what
can't?* As a starting default:

**Proceeds autonomously:** reading code, drafting, running local tests, editing local
files/branches, iterating on a task within its stated scope.

**Requires a human checkpoint:** pushing/publishing, deleting or force-overwriting anything,
touching shared infrastructure or CI/CD, spending money, contacting third parties, anything where
the cost of being wrong is high and hard to undo.

This boundary should be written down per project, not re-litigated per task.
