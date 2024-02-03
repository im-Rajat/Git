# Git
 
- Git is a version control system.
- Git helps us to keep track of code changes.
- Git is used to collaborate on code.
- Git help us to Manage projects with **Repositories**

### Version Control System (VCS)

- Git allows multiple developers to work on a project simultaneously without interfering with each other.
- It keeps track of changes made to the source code over time, making it easier to collaborate and manage different versions of a project.

### What is GitHub?

- Git is not the same as GitHub.
- GitHub is a web-based platform that provides hosting for software development and version control using Git
- GitHub makes tools that use Git.
- GitHub offers a range of features that enhance the development workflow and make it easier for teams to work together on software projects. 
- Key features provided by GitHub include:
    - Issues, Discussions, Pull requests, Notifications, Labels, Actions, Forks, Projects

### Configure Git

- We can download Git for free from the following website: https://www.git-scm.com/
- To check git version:
    - `git --version`
    - Output will look like this: `git version 2.34.1`
- To configure Git, you must define some global variables: **user.name** and **user.email**. Both are required for you to make commits:
    - `git config --global user.name "<USER_NAME>"`
    - `git config --global user.email "<USER_EMAIL>"`
- To check the changes:
    - `git config --list`

### Set up your Git repository

- Create a folder named NewProject using `mkdir` command. This folder will be the project directory, also called the working tree. The project directory is where all files related to your project are stored:
    - `mkdir NewProject`
- Change to the project directory by using the `cd` command.
    - `cd NewProject`
- Initialize our  new repository and set the name of the default branch to main:
    - `git init --initial-branch=main` or
    - `git init -b main`
- For earlier versions of Git, we can use these commands:
    - `git init`
    - `git checkout -b main`
- After running these initialize command, we will something similar like:
    - `Initialized empty Git repository in /home/<user>/Cats/.git/`
    - `Switched to a new branch 'main'`
- Get help from Git:
    - `git --help`
    - `git <any_command> -help` - see all the available options for the specific command, for example: `git commit -help`
    - `git help --all` -  see all possible commands
  
### Git Staging Environment

- The staging environment allows you to selectively choose which changes in your working directory should be included in the next commit.
- Files in our Git repository folder can be in one of 2 states:
    - **Tracked:** files that Git knows about and are added to the repository
    - **Untracked:** files that are in our working directory, but not added to the 
    - repository
- To stage changes to prepare for a commit:
    - `git add`
- To check status of the working tree:
    - `git status`
    - `git status --short` - to see the changes in a more compact way
- To stage all ll files in the current directory to the Staging Environment:
    - `git add .` or
    - `git add --all`
    - The shorthand command for `git add --all` is `git add -A`
-  Unstage changes from the staging area, allowing us to modify or re-select changes before committing.
   -  `git reset`


### Git Commit

- We are ready move from `stage` to `commit` for our repo.
- When we `commit`, we should always include a message.
- The commit command performs a `commit`, and the `-m "message"` adds a message.
    - `git commit -m "<Your Message>"`
    - `git commit -m "Initial commit"`
- To see information about previous commits:
    - `git log`
- Make an commit without a commit message or blank commit message:
    - `git commit --allow-empty-message --no-edit`
- To create an empty Git commit with a specified commit message:
    - `git commit --allow-empty -m "Commit Message`
    -  It's useful when we want to make a commit that doesn't introduce any changes but serves a specific purpose, such as triggering a CI/CD pipeline or marking a milestone.

#### Git Commit without Stage:

- If you want to make a commit directly from your working directory (not using the staging environment), use this syntax:
- `git commit -a`
- `git commit -a -m "Our commit message here"`
- This command automatically stages and commits all changes in tracked files in our working directory.
- This command only stages changes for files that are already being tracked by Git. It won't include changes in untracked files.
- The `-a` option stands for "all" and automatically stages any changes to tracked files before committing.

### Git Branch

- In Git, a `branch` is a new/separate version of the main repository.
- With a new branch called new-design, edit the code directly without impacting the main branch.
- Branches allow us to work on different parts of a project without impacting the main branch.
- Create a new branch:
    - `git branch new_branch` - Creates a new branch named "new_branch", but doesn't switch to it. We need to explicitly run `git checkout new_branch` to switch.
    - `git checkout -b new_branch` - Creates a new branch named "new_branch"and immediately switches to it.
- To list all branches in our repository:
    - `git branch`
    - The current branch is usually indicated with an asterisk (`*`).
- To switch to an existing branch:
    - `git checkout existing_branch` or
    - `git switch existing_branch` - with more recent versions of Git
- To delete a branch:
    - `git branch -d branch_to_delete`
    - `git branch -D branch_to_delete` - If the branch contains changes that haven't been merged, we may need to use `-D` to force the deletion:
- To rename a branch:
    - `git branch -m old_branch new_branch`
- To see remote branches:
    - `git branch -r`
- To see both local and remote branches:
    - `git branch -a`

#### Git Branch Merge

- Branch merging is a common operation in Git that involves combining changes from one branch into another.
- First Switch to the target branch:
    - Before we merge changes into a branch, we need to switch to the branch that will receive the changes (usually the main/master branch)
    - `git checkout main` or `git switch main`
- Merge the Source Branch:
    - Once we are on the target branch, use the `git merge` command to merge changes from the source branch
    - `git merge source_branch`
- Resolve Conflicts (if any):
    - Git will automatically merge most changes, but it may encounter conflicts if different branches modified the same file sections.
    - We manually need to edit the conflicted files to resolve the differences.
    - And Stage the resolved files with `git add.`
- Push Changes (if necessary):
    - After a successful merge, we may need to push the changes to the remote repository to make them available to others
    - `git push origin main`

### Push Local Repository to GitHub

- First we need to create a Repository on GitHub.
- As we already set up a local Git repo, we are going to push that to GitHub Repository.
- We need to get https link of the GitHub Repository from GitHub.
- `git remote add origin URL` specifies that we are adding a remote repository, with the specified `URL`, as an `origin` to our local Git repo.
    - `git remote add origin https://github.com/im-Rajat/Git.git`
- We need push our main branch to the origin url, and set it as the default remote branch:
    - `git push --set-upstream origin main`
    - `--set-upstream` is typically done when we have created a new branch locally and want to push it to the remote repository for the first time.
- Since we are first time connecting to GitHub, we will get some kind of notification to authenticate.
- After push is successful, we can check GitHub and see that the repository has been updated.


### Git Pull from GitHub

- Use `pull` to update our local Git:
- To pull changes from a GitHub repository to your local repository, you can use the `git pull` command.
- The `git pull` command fetches changes from a remote repository (such as GitHub) and merges them into your current working branch.
- `git pull origin main` - If we are on the main branch
- `git pull` - If our local branch is tracking the remote branch, we can use a simpler form without specifying the remote or branch:
- `pull` is a combination of 2 different commands:
    - `fetch` & `merge`
- `fetch` gets all the change history of a tracked branch/repo.
    - `git fetch`
- After running `git fetch` we need to run `git merge` to merge those fetched changes
    - `git merge origin/main`
    - `merge` combines the current branch, with a specified branch.
- `git pull` combines the `git fetch` and `git merge` commands. It fetches changes from the remote repository and automatically merges them into the current branch.
- Use `git fetch` if:
    - We want to see what changes are on the remote branch before merging.
    - We want to fetch changes without automatically merging them into your working branch.
- Use `git pull` if:
    - We want to fetch changes and automatically merge them into your working branch.
    - We are confident that automatic merging will not lead to conflicts.

### Git Push to GitHub

- To push changes from your local Git repository to a repository on GitHub, you can use the `git push` command. 
- Stage your changes:
    - `git add .` - will stage all files
- Commit your changes:
    - `git commit -m "Your commit message here"`
- Push Changes to GitHub:
    - `git push origin main`
    - If this is first time we are pushing to the remote repository or if we haven't saved your GitHub credentials, we may be prompted to enter your GitHub username and password or a personal access token.
    - `git push -f origin main` -  to force push changes, the `-f` flag stands for "force" and it overrides the default behavior of Git, allowing us to overwrite the remote branch with your local changes. Should not use it.
    - `origin` - This is the default name of the remote repository. It represents the remote repository on GitHub.




### References

- https://learn.microsoft.com/en-us/training/modules/intro-to-git/
- https://www.w3schools.com/git/
- ChatGPT
- 