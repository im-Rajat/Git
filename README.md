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

#### Git Commit without Stage:
  - `git commit -a`
  - `git commit -a -m "Our commit message here"`
  - This command automatically stages and commits all changes in tracked files in our working directory.
  - This command only stages changes for files that are already being tracked by Git. It won't include changes in untracked files.
  - The `-a` option stands for "all" and automatically stages any changes to tracked files before committing.


### References

- https://learn.microsoft.com/en-us/training/modules/intro-to-git/
- https://www.w3schools.com/git/