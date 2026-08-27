# The AOD/ADD Manifesto

1. **The agent is a developer, not a tool.** A tool waits to be invoked and does exactly one thing.
   A developer holds context, makes judgment calls, and is accountable for outcomes across a span of
   work. AOD treats the AI as the latter — which means giving it the context, boundaries, and
   feedback loops a developer needs, not the narrow input/output contract a tool gets.

2. **Specs are interfaces.** In OOD, you don't hand a class implementation to a caller — you hand it
   an interface and let it work out the internals. In AOD, the equivalent is an intent
   specification: what must be true when the work is done, not a line-by-line instruction of how to
   get there. Over-specifying the *how* defeats the point of delegating to an agent; under-specifying
   the *what* produces plausible-looking garbage.

3. **Context is state, and state must be managed deliberately.** An object's correctness depends on
   its internal state being consistent. An agent's output quality depends on its context window
   being accurate, relevant, and free of stale or contradictory information. Context engineering —
   what goes in, what gets summarized, what gets dropped — is not incidental to AOD, it *is* AOD's
   equivalent of encapsulation.

4. **Nothing ships without a verification loop.** An agent's confidence in its own output is not
   evidence. Every unit of agent-driven work pairs with an independent check: a test, a second agent
   with an adversarial prompt, a human review — something that doesn't share the first agent's blind
   spots. This is non-negotiable, not a nice-to-have.

5. **Humans own irreversibility.** Agents propose and execute reversible work continuously and
   autonomously. Anything hard to reverse, or that touches shared/external state, passes through an
   explicit human checkpoint. The line isn't "is the AI capable of this" — it's "who bears the cost
   if this is wrong."

6. **Workflows are composed, not monolithic.** A single agent given an enormous, vague task degrades
   the way a single 3,000-line class degrades: it becomes impossible to reason about or verify. AOD
   decomposes work into scoped units — the way OOD decomposes a system into classes — and composes
   them through defined workflows (pipelines, parallel fan-out, judge panels) rather than one agent
   doing everything in one pass.

7. **The paradigm is judged by outcomes, not by how "AI-native" it looks.** AOD is not about
   maximizing how much of the work an AI touches. It's about producing better, faster, more reliable
   software than the alternative. Where a human doing it directly is better, that's the right call —
   the paradigm has no ideological commitment to AI involvement for its own sake.
