# TICKET-000 - Git Fundamentals

## Objective

The goal of this ticket was to install Git on my RHEL 10 home lab and learn the basic Git workflow. I also wanted to create a repository that I can use to document my home lab as I learn more system administration skills.

## Tasks Completed

- Installed and verified Git on RHEL 10.
- Configured my Git username and email.
- Created my `Home_Lab` directory.
- Initialized the directory as a Git repository.
- Created a `README.md` file.
- Made my first Git commit.
- Modified the README and learned how Git tracks changes.
- Learned how to stage changes before committing them.
- Used Git to view my commit history.
- Updated the README to act as the homepage for my home lab project.
- Created a `tickets` directory to store documentation for each lab ticket.

## Commands Learned

- `git --version` - Shows the version of Git currently installed.
- `git config --global user.name` - Sets or displays the username attached to my commits.
- `git config --global user.email` - Sets or displays the email attached to my commits.
- `git status` - Shows the current state of my repository, including modified and staged files.
- `git add <file>` - Adds a file or its changes to the staging area.
- `git diff` - Shows changes I have made that have not been staged yet.
- `git diff --staged` - Shows the changes that are staged and ready for the next commit.
- `git diff HEAD` - Shows changes compared to the most recent commit.
- `git commit -m "message"` - Creates a commit with the staged changes and gives it a message.
- `git log` - Shows the commit history of the repository.
- `mkdir` - Creates a new directory.
- `nano` - Opens a file in the Nano text editor.

## Problems Encountered

One of my first problems was trying to run `git add README` when my actual file was named `README.md`. Git returned an error because it could not find a file named `README`.

I also tried running `git add` without specifying a file. Git told me that nothing was specified to be added.

While updating my README, I accidentally left some extra text on one of the ticket lines. I did not notice it until after making the commit, so I had to edit the file again and create another commit to fix it.

I also made a typo in my first commit message and wrote "Intitial commit" instead of "Initial commit."

## How I Solved Them

For the README error, I realized Git needed the correct filename and used `git add README.md`.

When `git add` did not stage anything, I learned that I needed to tell Git which file I wanted to add.

For the extra text in the README, I edited the file with Nano, staged the corrected version, and made another commit called `Remove extra text`.

I also learned that using `git diff` and `git diff --staged` before committing can help me catch mistakes before they become part of my commit history.

## What I Learned

I learned the basic Git workflow of modifying a file, checking its status, reviewing the changes, staging the changes, and then committing them.

I now understand that my working directory contains the files I am currently working on, while the staging area contains changes that I am preparing for the next commit. A commit saves a snapshot of those staged changes into the repository's history.

I also learned that `HEAD` points to my current commit and that Git keeps the older versions of my files in the repository history. This means that even when I replace or delete text from a file, previous committed versions are still part of the Git history.

Most importantly, I learned that I should check my work before committing instead of automatically adding and committing every change.
