---
name: norman-interaction-review
description: Use Don Norman's interaction-design principles as a decision base for UI/UX, frontend-backend interaction, and customer-facing interface work. MUST USE when the user needs to design, review, or decide interaction flows, user interfaces, product screens, forms, dashboards, onboarding, checkout, settings, permissions, async job states, error handling, or any new customer-facing User Interface. Also MUST USE when the user asks for advice, product judgment, UX suggestions, or help independently deciding what interactions, content, states, or flows a project should include. Use as a base for decisions, not only as a source of suggestions. Do not use for purely visual styling, backend-only logic, copyediting, or implementation tasks with no user interaction surface.
---

# Norman Interaction Review

## Purpose

Use this skill to think like a human-centered interaction reviewer before and during interface work. It distills Don Norman's practical ideas from *The Design of Everyday Things* into a working method for frontend/backend interaction, UI/UX decisions, and product-flow judgment.

This is not a book-summary skill. Use it to decide what a user should see, understand, do next, recover from, and trust.

## Core Stance

Start from the assumption that user mistakes are often design evidence. When a flow is confusing, first look for missing signifiers, poor feedback, bad mapping, hidden state, fragile error recovery, or a system image that does not match the user's mental model.

The job is to make the right action discoverable, the system state legible, the result interpretable, and the recovery path humane.

## Always Start With The Human Task

Before giving advice or writing UI code, identify:

- Who is the user, and what are they trying to accomplish?
- What do they already know, and what should not be required from memory?
- What system state matters to them right now?
- What is risky, irreversible, ambiguous, delayed, or easy to confuse?
- What would make the user feel "I know what happened and what I can do next"?

If these are unclear and the missing answer materially changes the interface, ask one concise question. Otherwise infer and proceed.

## The Main Operating Model: Seven Stages Of Action

For any meaningful interaction, walk the flow through these seven stages. Use them as a checklist, not as theory decoration.

1. **Goal**: What outcome is the user trying to achieve?
2. **Intention**: What action do they believe will move them toward that goal?
3. **Action specification**: Can they tell exactly which control, field, option, or step to use?
4. **Execution**: Can they perform the action without awkward sequencing, hidden prerequisites, or accidental triggers?
5. **Perception**: After action, can they perceive what changed?
6. **Interpretation**: Can they understand what the change means in their language, not the system's internal language?
7. **Evaluation**: Can they judge whether the original goal was met and what to do next?

When a design feels wrong, locate the broken stage. Then fix that stage directly.

## The Two UX Gulfs

Use these whenever reviewing a flow, state machine, form, or async process.

**Gulf of execution**: The user knows what they want, but the interface does not make the next action obvious.

Common fixes:
- expose the primary next action
- remove hidden prerequisites
- group controls by task, not implementation
- add signifiers, labels, examples, defaults, or constraints
- reduce steps that only reflect backend mechanics

**Gulf of evaluation**: The user acted, but cannot understand what happened, whether it worked, or what remains.

Common fixes:
- show immediate feedback
- distinguish saved, saving, failed, queued, processing, completed, canceled, and partial states
- provide timestamps, source, owner, or data freshness when relevant
- explain errors in user-goal terms
- provide next actions such as retry, edit, undo, view details, or contact support

## The Eight Norman Lenses

Apply the relevant lenses. Do not force every lens into every answer.

1. **Bad design is not the user's fault**
   Treat confusion, repeated mistakes, and support questions as signals that the interface is under-explaining itself.

2. **Action cycle**
   Design the complete path from goal to action to evaluation. Do not stop at "there is a button."

3. **Execution and evaluation gaps**
   Decide whether the main problem is "I don't know what to do" or "I don't know what happened." Many flows have both.

4. **Affordances and signifiers**
   Separate what is technically possible from what is visibly discoverable. In digital UI, signifiers usually matter more: button styling, disabled states, cursor/hover, labels, icons, empty states, drag handles, selected states, and affordance copy.

5. **Mapping and feedback**
   Controls should map naturally to outcomes. Feedback should be immediate enough, specific enough, and persistent enough for the user's risk level.

6. **Mental models and system image**
   Users infer how the system works from what the interface exposes. Translate backend architecture into a coherent product model: objects, states, relationships, ownership, and consequences.

7. **Error prevention and recovery**
   Assume slips, wrong selections, duplicate submissions, stale data, mistaken deletes, invalid inputs, and interrupted network requests will happen. Prevent what you can; make recovery obvious for the rest.

8. **Human-centered iteration**
   Prefer observation, prototypes, small tests, and real task walkthroughs over designer or engineer confidence. If unsure, create the smallest artifact that can reveal where users hesitate.

## Frontend/Backend Interaction Patterns

Use these translations for common frontend/backend interaction work.

**Forms and data entry**
- Make required inputs, formats, defaults, examples, and constraints visible before submission when possible.
- Validate close to the field, but reserve final cross-field validation for submit.
- Preserve user input on failure.
- Convert backend validation into user-fixable language.

**Async jobs and long-running operations**
- Do not collapse everything into loading.
- Model states explicitly: idle, pending, queued, running, partial, completed, failed, canceled, expired, retrying.
- Show what is happening, whether the user can leave, what will notify them, and how to recover.

**Save, publish, sync, import, export**
- Separate draft, saved, published, synced, and failed states.
- Show scope: what changed, where it applies, who can see it, and whether it is reversible.
- Avoid optimistic UI when consequences are high unless rollback is clear.

**Permissions, auth, and access**
- Explain why access is blocked and what would resolve it.
- Avoid dead ends. Provide request access, switch account, contact owner, or view limited mode when possible.

**Dangerous or irreversible actions**
- Prefer undo or reversible design over modal confirmations when feasible.
- If confirmation is needed, name the object, consequence, and recovery limit.
- For destructive bulk actions, make selection count and affected scope impossible to miss.

**Dashboards and operational tools**
- Make data freshness, empty states, filters, selected time range, and applied segments visible.
- Do not require users to remember hidden filter state.
- Put diagnosis near the data, not in a separate mental puzzle.

**AI-assisted interfaces**
- Help users form intentions: what can the AI do, what input does it need, and what counts as success?
- Help users evaluate output: show evidence, uncertainty, editable drafts, comparison, provenance, and next actions.

## Decision Modes

### Designing From Scratch

Return:
- user goals and top tasks
- proposed interaction model
- necessary screens or content sections
- critical states and transitions
- error and recovery design
- what to simplify or postpone
- one clear recommendation

### Reviewing An Existing Flow

Lead with issues, not theory. For each issue include:
- severity
- broken Norman lens or action stage
- why it will confuse or slow the user
- concrete fix

### Giving Product Advice

When the user asks what to build or which direction to choose, use Norman as a decision base:
- choose the option with the smaller execution/evaluation gulf
- prefer visible state over hidden rules
- prefer reversible actions over brittle warnings
- prefer task language over backend language
- prefer a smaller coherent model over a larger confusing feature set

### Implementing UI

Let the review shape the implementation. Add controls, states, constraints, and feedback in code when the task calls for it. Do not produce a long UX essay unless the user asked for one.

## Output Style

For advisory work, use concise sections:

```markdown
Human Goal
Interaction Model
Critical States
Norman Risks
Recommendation
```

For review work, use:

```markdown
Findings
Recommended Flow
State / Error Checklist
Decision
```

For implementation work, mention only the interaction decisions that materially shaped the change.

## What To Avoid

- Do not turn every response into a full theory lecture.
- Do not blame users for mistakes that the interface invites.
- Do not treat visual polish as a substitute for discoverability, mapping, feedback, and recovery.
- Do not expose backend implementation as the user's mental model unless the user genuinely needs it.
- Do not add confirmations everywhere; use constraints, previews, defaults, undo, and safer flows first.
- Do not hide complexity so aggressively that users lose trust or cannot evaluate outcomes.

## Source Basis

This skill is based on operationalized principles from Don Norman's *The Design of Everyday Things*, especially discoverability, signifiers, mapping, feedback, conceptual models, constraints, errors, the seven stages of action, the gulf of execution, the gulf of evaluation, and human-centered design. It also draws on Norman's later clarification that digital design often needs explicit signifiers because many screen actions are otherwise invisible.
