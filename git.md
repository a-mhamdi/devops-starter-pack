# Basic Git and GitHub Commands

These commands cover the basics of version control with `Git` and interacting with `GitHub` repositories.

> [!IMPORTANT]
>
> It is **important** to set your identity at first. To do so, you need to use the following commands:
> ```bash
> git config --global user.name "Your Name"
> git config --global user.email "your.email@example.com"
> ```

## Git Basics

`Git` is a version control system for tracking changes in code.

- **Initialize a Git repository**  
    ```bash
    git init
    ```
    Creates a new `Git` repository in the current directory.

- **Check repository status**  
    ```bash
    git status
    ```
    Shows the current state of the working directory and staging area.

- **Stage files for commit**  
    ```bash
    git add <file>
    ```
    Adds a specific file to the staging area. Use `git add .` to stage all changes.

- **Commit changes**  
    ```bash
    git commit -m "commit message"
    ```
    Saves staged changes with a descriptive message.

- **View commit history**  
    ```bash
    git log
    ```
    Displays the commit history for the repository.

- **Create a new branch**  
    ```bash
    git branch <branch-name>
    ```
    Creates a new branch for isolated development.

- **Switch to a branch**  
    ```bash
    git checkout <branch_name>
    ```
    Switches to the specified branch. Use `git checkout -b <branch_name>` to create and switch in one step.

- **Merge branches**  
    ```bash
    git merge <branch_name>
    ```
    Merges the specified branch into the current branch.

- **View differences**  
    ```bash
    git diff
    ```
    Shows changes between the working directory and the last commit.

## GitHub Basics

`GitHub` is a platform for hosting and collaborating on `Git` repositories.

- **Clone a repository**  
    ```bash
    git clone <repository_url>
    ```
    Downloads a repository from `GitHub` to your local machine.

- **Link local repository to GitHub**  
    ```bash
    git remote add origin <repository_url>
    ```
    Connects your local repository to a remote `GitHub` repository.

- **Push changes to GitHub**  
    ```bash
    git push origin <branch_name>
    ```
    Uploads local commits to the specified branch on `GitHub`.

- **Pull changes from GitHub**  
    ```bash
    git pull origin <branch_name>
    ```
    Downloads and merges changes from the specified branch on `GitHub`.

- **Create a pull request**  
    On `GitHub`'s website:
        1. Navigate to the repository.
        2. Click the "Fork" button.
        2. Click the "Pull requests" tab.
        3. Click "New pull request" and select the branches to compare.
        4. Add a title and description, then submit.

> [!INFO] 
> If `git merge` or `git pull` results in conflicts, edit the conflicting files, stage them with `git add`, and complete the commit.

> [!NOTE]
> Use `git help <command>` for more details on any command.

[Go to README](README.md)
