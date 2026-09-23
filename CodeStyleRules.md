# Coding Style Rules

These rules apply to C-like languages but are intended to be language-agnostic.
Where a language has its own established conventions, follow those conventions
while keeping the intent of these rules. The rules reinforce each other: small
steps (Rule 1) with descriptive names (Rule 2) make most "what" comments
unnecessary (Rule 3).

## Rule 1: Orchestrating methods (Composed Method)

**Rule.** Prefer an **orchestrating method** that reads as a sequence of named
steps. Implement each step as its own small method directly below it. Someone
opening the method first sees *what* happens. They see *how* it happens only
when they drill into a step.

- All steps within an orchestrating method are at the **same level of
  abstraction**. Do not mix high-level steps with low-level details.
- Name steps with verbs that describe intent (`ValidateInput`, `CalculateTotals`,
  `WriteResults`), not their mechanics.
- Order methods top-down (the *stepdown rule*): a method is followed by the
  methods it calls, so the file reads like a narrative from high level to detail.

**Why.** The main flow is readable without scrolling. Each step can be tested
and replaced on its own. A change to one step produces a small, isolated diff.

### Steps may be small, even one-liners

**Preference.** A good name is worth more than a saved line. If a step has its
own meaning in the domain, give it a method, even if it is only one line today.
This costs one navigation jump and gives two benefits:

- The orchestrator reads like prose instead of implementation.
- If that single line grows into five lines six months later (a retry, a guard,
  a log statement), the place for it already exists. You change one method
  instead of breaking the flow open again.

**Boundary.** The deciding factor is domain meaning, not line count. Do not
extract code that has no name of its own beyond restating its implementation
(for example `IncrementCounter()` wrapping `counter++`). Extract it when the
name adds meaning the code itself does not show (for example
`MarkProductAsRejected()` wrapping `rejectCount++`).

## Rule 2: Naming

**Rule.** Prefer long, complete, descriptive names over abbreviations.
`maximumRetryCount` is better than `maxRetCnt`.

- A name expresses **intent and meaning**, not type or implementation.
- Follow the conventions of the language in use: casing style (camelCase,
  PascalCase, snake_case), required prefixes, and widely accepted abbreviations
  (`id`, `url`, `i` as a loop index).
- If a name is hard to write because it would be too long, the method or
  variable is probably doing too much. See Rule 1.

## Rule 3: Comments explain *why*, not *what*

**Rule.** Code expresses *what* happens. Comments exist for what the code cannot
express: reasoning, context, history, and deliberately accepted trade-offs.

- **Do** write comments for: why a non-obvious approach was chosen, external
  constraints (hardware, protocol, customer requirement), workarounds for known
  bugs, performance decisions, and deliberate compromises.
- **Do not** write comments that restate the code, narrate each line, or
  compensate for unclear names. Improve the code or the name instead.
- **Do not** remove or avoid valuable "why" comments. The guideline "Don't
  comment bad code, rewrite it" is often misread as "comments are a sign of
  weakness." That reading loses exactly the comments worth keeping.

## Rule 4: Prefer composition over inheritance

**Rule.** Build larger behavior out of small, independent components that work
together. Prefer this over inheritance hierarchies.

- Define behavior through interfaces or contracts, and combine small components
  that each have a single responsibility.
- Pass dependencies in (constructor or parameters) rather than inheriting them
  from a base class.
- Keep inheritance shallow. Use it only for a genuine "is-a" relationship.

**Exception.** When a framework or platform requires inheritance, for example
extending an engine node class or a base function block, use it as required.
Keep the logic inside that class composed from smaller parts.
