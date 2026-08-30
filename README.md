# AOD — AI-Oriented Development

> **This repo is not just a description of AOD/ADD — it is itself the implementation proof of the
> methodology.** Its own content was produced by following the approach it defines: an intent spec
> was framed, an agent drafted the docs against that spec, and a human reviewed and accepted the
> result at the checkpoint. The repo is the artifact *and* the demonstration that the process works.

**AOD** (AI-Oriented Development) — also referred to as **ADD** (AI-Driven Development) — is a
software development paradigm built around treating AI agents as first-class participants in the
development process, not as autocomplete for a human who does all the real work.

The name is a deliberate nod to **OOD** (Object-Oriented Design/Development). OOD gave us a
vocabulary — objects, encapsulation, interfaces, inheritance, polymorphism — for organizing systems
around units of state and behavior. AOD proposes an analogous vocabulary for organizing *development
process* around units of autonomous or semi-autonomous work: agents, context, specs, and
verification loops.

This repo is the working definition of that paradigm: its principles, how it maps onto (and departs
from) OOD, and the concrete practices/workflow patterns that fall out of taking it seriously.

## Why two names?

- **AOD (AI-Oriented Development)** is the paradigm/design-philosophy name — parallel to
  "Object-Oriented Development." It's the noun you'd use in "we build our systems following AOD."
- **ADD (AI-Driven Development)** is the practice/process name — parallel to "Test-Driven
  Development." It's the verb-flavored one — "we develop this feature ADD-style, starting from an
  agent-executable spec."

They describe the same underlying paradigm from two angles: AOD is the *design* lens, ADD is the
*workflow* lens. Both are used throughout this repo; neither is more "correct."

## Contents

- [`MANIFESTO.md`](MANIFESTO.md) — the core claims, in short form.
- [`docs/principles.md`](docs/principles.md) — the pillars of AOD, with concrete definitions.
- [`docs/comparison-to-ood.md`](docs/comparison-to-ood.md) — a term-by-term mapping from OOD to AOD.
- [`docs/workflow.md`](docs/workflow.md) — what ADD looks like day-to-day: the loop, the artifacts,
  the checkpoints.
- [`docs/glossary.md`](docs/glossary.md) — terms used throughout, defined precisely.

## Status

Early draft. This is a living methodology document, not a finished spec — expect it to be revised
as the practices it describes are used and stress-tested.
