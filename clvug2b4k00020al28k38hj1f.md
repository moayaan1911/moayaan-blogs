---
title: "Git in a Nutshell"
datePublished: Mon May 06 2024 04:11:05 GMT+0000 (Coordinated Universal Time)
cuid: clvug2b4k00020al28k38hj1f
slug: git-in-a-nutshell
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/KPAQpJYzH0Y/upload/8dbd7f248ed46f7584e259304bd76154.jpeg
tags: github, git, gitlab, github-actions-1, gitbash, gitcommands, gitcrashcourse

---

Git is a powerful version control system that helps developers collaborate, track changes, and manage their codebase effectively. In this quick cheat sheet, we'll cover the essential Git commands used in development, along with a bonus section on creating pull requests and draft pull requests on GitHub.

## Basic Commands

* Initialize a new Git repository:
    
    ```plaintext
    git init
    ```
    
* Check the status of your repository:
    
    ```plaintext
    git status
    ```
    
* Add files to the staging area:
    
    ```plaintext
    git add <file>
    git add .
    ```
    
* Commit changes with a message:
    
    ```plaintext
    git commit -m "Your commit message"
    ```
    
* View commit history:
    
    ```plaintext
    git log
    git log --oneline
    ```
    

## Branching and Merging

* List all branches:
    
    ```plaintext
    git branch
    ```
    
* Create a new branch:
    
    ```plaintext
    git branch <branch-name>
    ```
    
* Switch to a branch:
    
    ```plaintext
    git checkout <branch-name>
    ```
    
* Create a new branch and switch to it:
    
    ```plaintext
    git checkout -b <branch-name>
    ```
    
* Merge a branch into the current branch:
    
    ```plaintext
    git merge <branch-name>
    ```
    
* Rebase the current branch onto another branch:
    
    ```plaintext
    git rebase <branch-name>
    ```
    

## Undoing Changes

* Discard changes in the working directory:
    
    ```plaintext
    git restore <file>
    ```
    
* Unstage changes from the staging area:
    
    ```plaintext
    git restore --staged <file>
    ```
    
* Revert a commit by creating a new commit:
    
    ```plaintext
    git revert <commit-hash>
    ```
    

## Remote Repositories

* Clone a remote repository:
    
    ```plaintext
    git clone <repository-url>
    ```
    
* Add a remote repository:
    
    ```plaintext
    git remote add <remote-name> <repository-url>
    ```
    
* Fetch changes from a remote repository:
    
    ```plaintext
    git fetch <remote-name>
    ```
    
* Pull changes from a remote repository:
    
    ```plaintext
    git pull <remote-name> <branch-name>
    ```
    
* Push changes to a remote repository:
    
    ```plaintext
    git push <remote-name> <branch-name>
    ```
    

## Bonus: Pull Requests on GitHub

Pull requests are a way to propose changes to a repository on GitHub. Here's how to create a pull request:

1. Fork the repository you want to contribute to.
    
2. Clone the forked repository to your local machine.
    
3. Create a new branch for your changes:
    
    ```plaintext
    git checkout -b <branch-name>
    ```
    
4. Make your changes and commit them.
    
5. Push the branch to your forked repository:
    
    ```plaintext
    git push origin <branch-name>
    ```
    
6. Go to the original repository on GitHub and click on the "Pull requests" tab.
    
7. Click on "New pull request" and select your branch as the compare branch.
    
8. Provide a title and description for your pull request.
    
9. Click on "Create pull request" to submit your changes for review.
    

### Draft Pull Requests

Draft pull requests allow you to propose changes without requesting a review immediately. They are useful when you want to share your work in progress or get early feedback. To create a draft pull request, follow the same steps as above, but click on "Create draft pull request" instead of "Create pull request."

### Base Branch

When creating a pull request, you need to specify the base branch, which is the branch you want to merge your changes into. Typically, the base branch is the main branch of the repository, such as `master` or `main`.

That's it! You now have a handy cheat sheet for the most commonly used Git commands and a guide on creating pull requests on GitHub. Happy coding!