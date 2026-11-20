# Course Tracker

**How many marks to go?**

A skill for AI agents that tracks a student's courses end to end.

The student does two things: installs this skill, and logs in once to their learning platform and student email. The agent does everything else. It discovers the enrolled courses on its own, extracts each course's graded components, full marks, grade bands and deadlines, builds a living dashboard, and keeps it current from the learning platform, school mail and course group chats.

See it: the promo page linked in this repo's About section shows the dashboard, the honesty rules and a shareable grade report card.

## The one question it answers

How many marks are still needed, on the work that remains, to reach the target grade. Every course gets two lines: the safety line for passing, and the target line. Remaining tasks are ranked by marks per hour, so the student always knows what to do next.

Deadlines are tracked with their meeting rooms and join links, and reminders climb a ladder as a deadline approaches. The moment work is submitted, the reminders stop.

## The honesty rules

- Not submitted is never shown as zero marks.
- Confirmed scores and estimates are always kept apart, with the basis attached to every estimate.
- A source that cannot be reached is reported as unreachable, never as no news.

## Install

    npx skills add ZhizhouZhao/course-tracker

Then tell your agent: "Here is my learning platform, I am logged in, the rest is yours."

## 中文

你只做两件事：装上这个 skill，在学习平台登录一次。剩下的交给你的 agent——它自己找到你的课，算出每门课离目标成绩还差多少分，按性价比排出先做哪件，盯着小组里谁交了谁没动，截止前三档提醒，交了就停。未提交永远不会显示成 0 分。

    npx skills add ZhizhouZhao/course-tracker

---
Built from one real semester of tracking four courses at the University of Oulu.
