📌 Merge Conflicts & Conflict Resolution – Reflection
⭐ What is a merge conflict?

A merge conflict happens when Git cannot automatically decide which version of a file is correct.
This usually occurs when:

Two branches modify the same line of a file

A file is deleted in one branch but edited in another

Branch history diverges and Git can't auto-merge changes

Git needs a human decision to choose which version to keep.

🔥 What caused the merge conflict in my repo?

To intentionally create a merge conflict, I performed the following steps:

Created a new branch

git checkout -b conflict-branch


Edited a file (e.g., notes.md) and committed the change.

Switched back to main

git checkout main


Modified the same line of the same file and committed again.

Tried to merge:

git merge conflict-branch


Git produced a conflict because the same line had two different versions.

🧩 How I resolved the conflict

Using GitHub Desktop / VS Code:

Git marked the conflict in the file like this:

<<<<<<< HEAD
This is the version from the main branch
=======
This is the version from the conflict-branch
>>>>>>> conflict-branch


I manually chose how the final version should look:

Kept relevant parts

Removed conflict markers <<<<<<<, =======, >>>>>>>

Saved the file.

Marked conflict as resolved:

git add .


Completed the merge:

git commit


The merge was successful, and the history remained clean.

🧠 What I learned

Merge conflicts are normal and expected, especially in collaborative projects.

Conflicts happen when Git cannot decide automatically which change to keep.

Good communication and small, frequent commits reduce conflict likelihood.

Using tools like GitHub Desktop, VS Code, and Git’s conflict markers makes resolving conflicts easier.

I now understand how to:

Reproduce a conflict

Read conflict markers

Decide which version to keep

Finalize the merge correctly

Writing Meaningful Commit Messages — Reflection
⭐ What makes a good commit message?

A good commit message should be:

Clear and concise → It explains what changed and why.

Action-oriented → Typically starts with a verb (e.g., “Add”, “Fix”, “Refactor”).

Specific → Mentions the exact feature, bug, or file affected.

Structured → Many teams follow this format:

<type>: <short description>

Optional longer explanation if needed


Examples of good types: fix, feat, docs, refactor, test, chore.

A meaningful commit message acts as documentation for your future self and teammates.

🔍 Examples I Created in My Repo
1️⃣ Vague Commit Message (bad example)
fixed stuff


Problems:

Doesn’t explain what was fixed

Unhelpful during debugging

No context for collaborators

2️⃣ Overly Detailed Commit Message (too much information)
Updated the calculateDifference function by adding multiple condition checks, reorganizing the code structure, renaming variables, adding error handling, rewriting loops, modifying spacing, adjusting indentation, updating documentation, cleaning comments, and testing manually.


Problems:

Too long; mixes multiple changes

Hard to scan

Suggests commit should have been split into smaller commits

3️⃣ Well-Structured Commit Message (good example)
refactor: rename variables and simplify calculateDifference function

Improved readability by updating variable names and removing unnecessary logic.


Why this is good:

Short title

Describes the change + the reason

Easy for teammates to understand

Helps with debugging later

🤝 How clear commit messages help team collaboration

Teammates can quickly understand changes without reading the entire diff

Easier code reviews

Smoother handovers between developers

Better project documentation and history tracking

Makes it easier to revert or trace the source of bugs

Good commit messages reduce confusion and save time for everyone.

⚠️ How poor commit messages cause issues later

Hard to understand why a change was made

Difficult to find the commit that introduced a bug

Slows down onboarding for new developers

Makes debugging and refactoring painful

Leads to messy project history

A project with vague commit messages becomes much harder to maintain.
