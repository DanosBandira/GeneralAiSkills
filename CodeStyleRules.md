# Coding Style Rules

These rules apply to C-like languages but are intended to be language-agnostic.
Where a language has its own established conventions, follow those conventions
while keeping the intent of these rules. The rules reinforce each other: small
steps (Rule 1) with descriptive names (Rule 2) make most "what" comments
unnecessary (Rule 3).

## Goal of these rules

The goal is code that the next developer can read and change easily. The rules
serve that goal. If applying a rule literally makes the code harder to read,
prefer readability and mention the deviation.

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

### Guards

Guards (input checks, early returns, precondition checks) may be placed wherever
they make logical sense: at the top of the orchestrator, between steps, or
inside a step. Choose the place based on what the guard protects. A check that
decides whether the whole flow may run belongs in the orchestrator; a check that
only concerns one step belongs in that step.

## Rule 2: Naming

**Rule.** Prefer long, complete, descriptive names over abbreviations.
`maximumRetryCount` is better than `maxRetCnt`.

- A name expresses **intent and meaning**, not type or implementation.
- A name is **honest about everything the method does**. If a method validates,
  saves and notifies, name it `ValidateAndSaveAndNotify`. Never shorten a name in
  a way that hides part of its behavior: a method called `Save` must only save.
- Follow the naming conventions of the language in use, such as casing style
  and widely accepted abbreviations (`id`, `url`, `i` as a loop index). If the
  conventions for the language or project are unclear, ask before choosing.

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
- Documentation comments on public APIs (XML doc, Javadoc, Doxygen) describe the
  contract: parameters, return value and errors. They are allowed and are not
  "what" comments in the sense of this rule.

### File and class headers

Every file or class starts with a short header comment that explains:

- **What** it is responsible for, in a few sentences.
- **How** it is used: its role in the larger system and how other code is
  expected to use it (for example: which method to call, what to set up first).

This is an overview for someone opening the file for the first time. It is
allowed and is not a "what" comment in the sense of this rule. Keep it short;
details belong in the code and in the method names.

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

### From steps to components

When a group of steps forms its own responsibility, move it into a separate
component instead of adding more private methods. Signals:

- The steps share their own state or data that the rest of the class does not use.
- The steps would be useful elsewhere or could be tested as a unit on their own.
- The class contains several clearly separate groups of steps.

## Applying these rules to existing code

When working in existing code that does not follow these rules, ask the user
whether that code should be refactored to this style or left as it is. Do not
refactor existing code on your own initiative. New code always follows these
rules.
