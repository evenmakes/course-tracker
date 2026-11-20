# First-run evaluation — 2026-11-20

Can an agent that has **only read SKILL.md** — no prior knowledge of the student, the courses, or this repository — build a correct course dashboard on its own?

This is the record of that test, run once, live, before the 1.0.0 release.

## Setup

- **Agent**: a fresh session with no memory of the user or the courses. Its only instructions were the first-run protocol in `SKILL.md`.
- **Environment**: the student's own logged-in LMS session (Moodle, University of Oulu), opened read-only. The agent was not told which courses existed.
- **Student input during the run**: none. No course names, components, weights or deadlines were provided.
- **Ground truth**: the Moodle gradebook, the individual activity pages, and the student records system (Peppi), checked independently.
- **Duration**: about 6 minutes for four courses.

## Results

| Course | What the agent modelled on its own | Ground truth | Verdict |
|---|---|---|---|
| Software Development | Structure theory 40 + group project 60; theory items 8/9/10 + quiz 10 = 37/40; grade bands 5 = 96–100, 4 = 86–95, 3 = 71–85 | Identical in gradebook and records | ✅ exact |
| Digitalisation | Course total **81.70 / 86 (95.00%)**; remaining 14 marks identified as a teacher-side workshop grade | Identical computed total in the gradebook | ✅ exact |
| Software Engineering | M1 Quiz 10.00/10 graded; Assignment 1 pass/fail and Assignment 2 /10 both due 2026-11-23 23:59; later module items in December | Identical | ✅ exact |
| Servitisation | Grade page returned **"Invalid user"** — agent reported the gradebook as unavailable instead of inventing figures, and still extracted the deadlines from the course page | The error is a teacher-side gradebook configuration issue, independently confirmed | ✅ honest failure |

**Fabrication check**: everything the platform did not show was marked "not shown on page". Zero invented marks, zero invented deadlines, zero totals presented as confirmed that were not backed by visible arithmetic.

## Defects found — and fixed in the protocol the same day

The test passed on numbers but exposed three gaps in the first version of the protocol:

1. **Ungraded items** were only checked in the gradebook, where they show as blank. → The protocol now requires checking each ungraded item's **activity page** for submission state.
2. **Final grades of finished courses** were looked for in the LMS, where they may lag. → The protocol now checks the **student records system** for registered final grades.
3. When the **course page and the grade page disagreed**, the protocol had no rule. → The grade page's computed figures now win; the conflict is flagged, never averaged.

## Limitations

- One institution, one platform (Moodle), one run. This is a smoke test with a perfect score, not a benchmark.
- Canvas, Blackboard and GPA-based scales are handled by the protocol's design but have **not** been live-tested.
- The dashboard the agent generated for itself during this test was verified against the gradebook by hand; an independent second-user run is the next evaluation milestone.

*Evaluation record for Course Tracker 1.0.0. The student in this test is the author; the point of the test was the protocol, not the person — the agent knew nothing about either.*
