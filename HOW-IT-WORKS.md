# how astral uses this intake (internal doc)

this explains the workflow for jordi / the studio. not for clients.

## the flow

```
client downloads template
  ↓
fills 01-08 markdown files
  ↓
drops assets into files/
  ↓
sends folder back (zip / github fork / shared drive)
  ↓
45-min call with jordi — close gaps
  ↓
jordi writes 00-INTAKE.md (the synthesized brief)
  ↓
client signs off on 00-INTAKE.md
  ↓
jordi creates new repo from ralph-template
  ↓
jordi copies 00-INTAKE.md → ARCHITECTURE.md in new repo
  ↓
jordi breaks features into TASKS.md (atomic, 20-50 lines each)
  ↓
jordi seeds first commits at quality bar
  ↓
remote trigger created (hourly)
  ↓
ralph loop builds
  ↓
jordi does weekly 60min human pass per repo
```

## where this lives

- template: `github.com/jcatalaamat/intake-template` (public — shareable)
- per-client fills: `github.com/jcatalaamat/{client-slug}-intake` (private)
- per-client builds: `github.com/jcatalaamat/{client-slug}` (private)

keep the 3 separate. the intake repo is an artifact, the build repo is the product.

## the 45-min call

agenda:

1. **first 10min** — read their filled answers out loud back to them. they correct you. this surfaces where their writing ≠ their meaning.
2. **next 20min** — gaps. any `_answer:_` left blank, any fuzzy answer. push for specifics.
3. **next 10min** — alignment on v1 scope. say what's P0. say what's out. get a verbal "yes".
4. **last 5min** — access and timeline. what you need from them in the next week. what they get from you in the next week.

## the synthesis rules

when writing `00-INTAKE.md`:

- every line must be a claim you could defend. no vague marketing language.
- if the client gave you fluff, translate it to action. "revolutionary UX" → "onboarding takes ≤60s, measured".
- if two client answers contradict, flag it. resolve on the call or as an open question.
- never invent. if it wasn't said, it's an open question, not a filled line.

## when to walk away

if the intake comes back with:
- more than 5 blank `_answer:_` fields
- contradictory answers across 3+ files
- no access commitments in `06-access.md`
- "budget: flexible" with no range

the client isn't ready. tell them. offer a paid discovery week ($500-1500) to unblock before committing to build.

## pricing adjustment signals

scope is sized from `04-features.md`:
- ≤5 P0 features with simple auth: low end of your range
- 5-10 P0 features or complex integrations: mid
- 10+ P0 or compliance requirements: high end, or split into v1a/v1b
