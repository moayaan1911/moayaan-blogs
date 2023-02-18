# Get started with GIT

Git is a widely-used version control system that allows developers to track changes to their codebase over time. It is an essential tool for collaborative software development and has become a fundamental component of modern software engineering.

In this guide, we will provide a comprehensive overview of Git, including its key concepts, basic commands, and best practices.

## **Key concepts of Git**

Before diving into the Git commands, it is important to understand some key concepts of Git. These include:

* **Repository:** A repository is a collection of files and directories that Git tracks.
    
* **Commit:** A commit is a snapshot of changes made to the repository at a particular point in time.
    
* **Branch:** A branch is a separate line of development that diverges from the main line (or "master" branch) of the repository.
    
* **Merge:** Merging is the process of combining changes from one branch into another.
    
* **Remote:** A remote is a copy of the repository that is hosted on a different server
    

## <mark>Basic Commands</mark> of Git

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1676637759265/51347da7-9544-434a-9efd-b4ae52fd14a9.png align="center")

[Image by Doabledanny](https://doabledanny.gumroad.com/l/git-commands-cheat-sheet-pdf)

`git init`: This command initializes GIT to your folder.

```bash
git init
```

`git add`: This command adds changes made to a file to the staging area, which prepares the changes to be committed to the repository. You can add specific files or directories by specifying their names after the `add` command. For example:

```bash
git add file.txt        # Add changes made to file.txt to the staging area
git add directory/     # Add changes made to all files in the directory to the staging area
```

`git commit`: This command saves changes made to the repository with a commit message that describes what changes were made. The `-m` option allows you to add a message to the commit, which is useful for keeping track of changes and collaborating with other developers. For example:

```bash
git commit -m "Added new feature"    # Commit changes with a descriptive commit message
```

`git push`: This command uploads changes from the local repository to a remote repository, such as a repository hosted on GitHub. The `origin` keyword refers to the remote repository you are pushing to, and `main` refers to the branch you are pushing changes from. For example:

```bash
git push origin main     # Push changes from the local main branch to the remote repository named origin
```

`git pull`: This command retrieves changes from a remote repository and merges them into the local repository. This is useful for keeping the local repository up-to-date with the latest changes made by other developers. For example:

```bash
git pull origin main     # Pull changes from the remote main branch into the local repository
```

`git branch`: This command lists all branches in the repository. The current branch is highlighted with an asterisk. For example:

```bash
git branch               # List all branches in the repository and show which branch is currently checked out
```

`git checkout`: This command switches to a different branch. You can specify the branch you want to switch to by providing its name after the `checkout` command. For example:

```bash
git checkout new-feature     # Switch to the new-feature branch
```

`git merge`: This command combines changes made in one branch with another branch. For example, if you want to merge changes made in the `new-feature` branch with the `main` branch, you can do the following:

```bash
git checkout main       # Switch to the main branch
git merge new-feature   # Merge changes from the new-feature branch into the main branch
```

`git clone`: This command creates a copy of a remote repository on your local machine. You can specify the URL of the repository you want to clone after the `clone` command. For example:

```bash
git clone https://github.com/user/repo.git    # Clone the repository located at https://github.com/user/repo.git
```

`git status`: This command displays the current state of the repository, including which files have been modified, which files are staged, and which branch the repository is currently on. For example:

```bash
git status    # Show the current status of the repository
```

`git log`: This command displays a list of commits made to the repository, including the commit message, author, and date. You can use options to filter the list, such as displaying only the last 5 commits or only commits made by a specific author. For example:

```bash
git log         # Display a list of all commits made to the repository
git log -5      # Display the last 5 commits made to the repository
git log --author="John"   # Display only commits made by the author "John"
```

`git fetch`: This command retrieves changes from a remote repository without merging them into the local repository. This is useful for keeping the local repository up-to-date with changes made by other developers without modifying the local repository. For example:

```bash
git fetch origin    # Fetch changes from the remote repository named origin
```

`git branch -d <branch>`: This command deletes a branch from the repository. You can only delete branches that have already been merged into another branch. For example:

```bash
git branch -d new-feature    # Delete the new-feature branch
```

`git clone -b <branch> <remote>`: This command clones a specific branch from a remote repository to your local machine. For example, to clone the `development` branch from the remote repository named `origin`, you can do the following:

```bash
git clone -b development https://github.com/user/repo.git    # Clone the development branch from the remote repository named origin
```

`git reset`: This command resets the repository to a specific commit, discarding any changes made after that commit. You can use it to undo changes or remove uncommitted changes from the repository. For example:

```bash
git reset HEAD~1    # Reset the repository to the previous commit, discarding any changes made after that commit
```

`git push <remote> <branch>`: This command pushes changes from the local repository to a specific branch in a remote repository. For example, to push changes from the local `main` branch to the `development` branch in the remote repository named `origin`, you can do the following:

```bash
git push origin main:development    # Push changes from the local main branch to the development branch in the remote repository named origin
```