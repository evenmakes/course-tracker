# Course Tracker

A skill for AI agents that tracks a student's courses end to end.

The student does two things: installs this skill, and logs in once to their learning platform and student email. The agent does everything else. It discovers the enrolled courses on its own, extracts each course's graded components, full marks, grade bands and deadlines, builds a living dashboard, and keeps it current from the learning platform, school mail and course group chats.

## The one question it answers

How many marks are still needed, on the work that remains, to reach the target grade. Every course gets two lines: the safety line for passing, and the target line. Remaining tasks are ranked by marks per hour, so the student always knows what to do next.

## The honesty rules

- Not submitted is never shown as zero marks.
- Confirmed scores and estimates are always kept apart, with the basis attached to every estimate.
- A source that cannot be reached is reported as unreachable, never as no news.

## Install

    npx skills add <owner>/course-tracker

Then tell your agent: "Here is my learning platform, I am logged in, the rest is yours."

---
Built from one real semester of tracking four courses at the University of Oulu.
