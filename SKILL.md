---
name: course-tracker
description: Track your courses end to end after one login. The agent discovers your courses from your learning platform, computes how many marks you still need for your target grade, ranks what to do next, watches group work, and keeps one living dashboard honest. Not submitted is never zero, and estimates are never mixed with confirmed scores.
---

# Course Tracker

The promise this skill keeps: the user does two things, installs the skill and logs in once, and the agent does everything else.

## Run the first-run protocol

- After install, ask the user for exactly one action: log in to their learning platform and student email in the browser, and bring that login window to the front so they cannot miss it.

- Never ask the user to type in courses, components, weights or deadlines during setup, because every typed field is a reason to abandon the skill.

- Once login works, discover the courses yourself from the learning platform: enumerate the enrolled courses, then open each course and extract its graded components, full marks or weights, grade bands, deadlines and submission states.

- Open the activity page of every component that has no score yet, because a dash on the grade page cannot distinguish not submitted from submitted and awaiting grading, and those two states must never be merged.

- For a finished course whose grade page shows no total, check the student records system for the registered final grade before calling the course unmodelled, because final grades often live there rather than in the learning platform.

- Build the dashboard from what you found and present it as the first result, with a one line report per course: its name, how its grade is composed, and which course looks riskiest.

- Where a course hides its grading structure, ask for that one course's syllabus or grading page only, and keep the rest of the setup automatic.

## Keep the score states honest

- Give every component exactly one state from this set: graded, graded but score unpublished, submitted and awaiting grading, in progress, not submitted, not yet open, or passed on a pass or fail basis.

- Never render a not submitted or awaiting grading component as zero marks, an empty bar or a 0 out of 10 line, because an empty bar reads as a failed score and corrupts every average built on it.

- Keep confirmed scores and estimates in separate figures everywhere they appear, and attach the basis to every estimate in one short phrase.

- When the course page and the grade page disagree about a total or a scale, trust the grade page's computed figures, show the conflict on the dashboard, and never average the two versions into a third number.

- Treat a score the user states as confirmed only when it agrees with the visible arithmetic, such as component scores summing to a total inside the band of a registered final grade, and flag any mismatch instead of silently adopting the number.

## Compute two lines, not one

- For every course compute a safety line and a target line: what is still needed on the remaining work to pass, and what is still needed to reach the user's target grade.

- Show each requirement as one line over the marks still outstanding, such as needing 11.30 of the remaining 14, and flag the outcome as locked when the confirmed total already reaches the band, impossible when the requirement exceeds what remains, and open otherwise.

- Rank the remaining work across all courses by marks divided by estimated effort, so the user always knows which single task buys the most grade for the next hour.

- Answer what-if questions by recomputing the affected course and the programme rollup with the hypothetical score in place of the outstanding component, and label the result as a scenario.

- Recalculate every figure the moment any component changes state or score, and never let a stale total survive a new grade.

## Watch the group work

- For group courses, track each member's components from the course channels and shared documents: who has delivered, who is in progress, and who has shown no sign of life.

- Before a group meeting, prepare a short chase list of the silent members and the decisions the meeting must settle, such as unbooked exam slots.

- Report a silent member or a slipping group deadline to the user as soon as the check finds it, not at the next summary.

## Track deadlines and remind

- Keep every deadline in the dashboard timeline with its owner label, and treat an unsubmitted personal or group item as the unit that reminders exist for.

- Attach the place to every event that has one, meaning the room or address for an offline meeting and the join link for an online one, taken from the course page, the calendar entry, the group chat or the mail that announced it.

- Put the place or the link inside the reminder itself, so the user can walk in or join straight from the reminder without hunting for it.

- Remind on a ladder rather than once: surface the item in the daily digest three days out, remind directly one day out, and give a final call on the morning of the deadline day.

- Verify the item's live state before every reminder, and stop reminding the moment it is submitted, because a reminder about finished work destroys trust in all the others.

- Batch the reminders of one round into a single message ordered by the marks at stake, and never send one message per item.

- Give teacher-side deadlines no action reminders, because the user cannot act on them, and mark them as information only in the timeline.

## Maintain it without the user typing anything

- Pull updates from the sources that already carry them, such as the learning platform, school mail reaching a watched inbox, and course group chats.

- Verify the live state before writing any figure into the dashboard, and stamp each course with its last verified date so the user can see how fresh every number is.

- Report a source whose login has expired as expired, with its last successful check time and the login window brought to the front, never as no news and never as no new grades.

- When the user asks to check grades, refresh the sources first, update the dashboard, and report only what changed.

- Accept a score the user speaks as a fallback entry when no source can be reached, mark it as user reported, and replace it with the verified figure at the next successful check.

## Roll up to the real goal

- Record the programme-level rule above the courses when one exists, such as a best-three average used for admission, because the rollup is what the user actually optimizes for.

- Show the confirmed rollup first and the scenario range second, with the assumptions of the range named in one phrase.

- At the end of the term, close every course out into an archive: final grades, the score rate by component type, and where the effort went, saved where the user keeps their records.

## Present one dashboard, not chat fragments

- Keep the tracker as one living dashboard in a Space that the user opens to check standing, finished work and outstanding work, and update that same dashboard instead of building a new chart per question.

- Let the homepage answer only three questions per course: the current grade or state, what is still missing for the target, and the next action with its deadline.

- Draw every bar on one shared scale where the full length equals the full marks of whatever it measures, and use a stacked bar of obtained, still to be graded and a target threshold tick only when the course has a real total.

- List confirmed components without a percentage bar when a course has no unified total, rather than forcing components with different scales into one invented percentage.

- Put the deadline timeline in its own section sorted in the user's local time, defaulting to the next seven days of unfinished work, with the owner label of personal, group or teacher-side on every row.

- Push grading detail, estimate basis, source links and history into a detail layer per course, and keep the homepage free of small print.

- Keep the numbers large and the layout quiet, give each course one accent colour for its bar and its key figure, and carry state in words on small pills rather than in colour alone.

## Design the dashboard to this standard

The dashboard is the product, so build it to the reference look rather than to a generic table.

- Give each course its own card on a quiet off-white background, with thin borders, generous whitespace and small muted labels in capitals, and keep filler headlines and rule explanations out.

- Set one number per card very large, the confirmed total or the marks still needed, and let everything else stay small, because the eye should land on the number that matters first.

- Give each course one decisive sentence with its critical figure highlighted in the course accent colour, in the shape of: of the 14 marks left, you need 10.80.

- Draw every bar so its full length equals the item's full marks, keep one shared scale across all courses, mark the target line with a tick, draw a pending segment hatched, and give a not submitted item no bar at all, only its status pill.

- Show state with small pills that carry the honest words, such as Final, Awaiting grading or Not submitted, and never let colour alone carry the meaning.

- Show a confirmed figure and an estimate as two separate blocks side by side, the estimate smaller with a dashed underline and its basis attached, and never merge them into one bar or one number.

- Spend each course's accent only on its bar and its key figure, keep the base ink on off-white, and use no gradients, no glass effects and no numbered step columns anywhere.

- Put the source links at the bottom of each card in faint small text, so every figure can be traced back to the page it came from.

- When the environment cannot render a page, keep the same hierarchy in plain text, with the big number first, the decisive sentence second and the sources last.
