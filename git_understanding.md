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
