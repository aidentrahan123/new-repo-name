# Comparing my Git work with the agent's

## What I did by hand in 2.2
I created the repository with `git init`, made the first commit myself, opened a branch called `add-noi-summary`, pushed it, opened a pull request on GitHub, and merged it. I then made an edit on `main` and on the branch to the same line of `notes.md`, which produced a conflict, and I resolved it in the editor by keeping both sentences and deleting the markers.

## What the agent did differently
I gave Claude Code the same task in a fresh folder. It ran `git init` and `git add -A` together and committed everything in one commit with the message "Initial commit". For the branch it used `git switch -c` where I had used `git checkout -b`. It opened the pull request with `gh pr create` from the terminal, which I had done by clicking through the website. When I asked it to create a conflict it did so, but it resolved the conflict by keeping only its own version of the line and dropping mine, and the commit message said "Resolve merge conflict" without saying which side won.

## One thing it could have done better, and what I changed
The conflict resolution dropped my sentence without telling me. The diff showed `notes.md` losing a line I had written on `main`. I amended the resolution to keep both sentences, which is what the lesson's example did, and I rewrote the commit message to say "Resolve conflict in notes.md, keeping both summaries". I also asked it to split the initial commit, because "Initial commit" with three unrelated files does not say what changed.

## What I would check first next time
The files-changed tab on the pull request before merging, specifically any file the agent touched that I did not mention in the instruction. In this run it also reformatted `README.md` line wrapping without being asked, which I only noticed afterwards.
