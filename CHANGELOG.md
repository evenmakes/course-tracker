# Changelog

All notable changes to Course Tracker are documented here.
Format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/); versions follow [Semantic Versioning](https://semver.org/).

## [1.0.0] — 2026-11-20

First public release.

### The protocol
- **First-run discovery**: after a single LMS login, the agent discovers the user's courses, graded components, weights, grade bands and deadlines from the platform itself. The user never types in a course, a component or a deadline.
- **Honest state model**: every mark lives in exactly one of seven states — graded, graded but unpublished, submitted awaiting grading, in progress, not submitted, not yet open, pass/fail — and each state has a fixed rendering. Not-submitted and awaiting-grading work is never drawn as zero.
- **Confirmed vs estimate, always separate**: confirmed totals come only from visible gradebook arithmetic. Estimates are shown apart, smaller, with their basis stated, and never merged into a confirmed figure.
- **Two lines per course**: over the marks still outstanding, the skill computes a safety line and a target line, flagged *locked*, *open* or *impossible* — so "how many marks to go" is always an exact answer, not a vibe.
- **Cross-check rule**: gradebook, activity pages and the student records system are three separate sources; the gradebook's computed figures win conflicts, and conflicts are flagged, never averaged away.
- **Group watching**: for team courses, who has delivered and who has gone silent, with a pre-meeting chase list.
- **Deadline reminders**: three days out, one day out, and a final call on the morning — each verified against the live state first, and stopped the moment the work is submitted.
- **Dashboard design standard**: one card per course, one very large number per card, bars whose full length is the full marks on one shared scale, pending work hatched, sources cited at the foot of every card; light and dark themes with identical semantics.

### Verification
- Live-tested end-to-end on a real University of Oulu Moodle with four real courses — see [EVAL.md](EVAL.md) for the full evaluation record, including the three protocol defects the test exposed and fixed.

### Known limits
- Only Moodle and the Finnish 1–5 grading scale are live-tested so far. Canvas, Blackboard and GPA scales are covered by the protocol but unverified.
- The skill never submits anything, sends messages, or changes records on the LMS. It reads, computes and reminds.
