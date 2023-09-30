
Source code management (SCM) is the practice of tracking and controlling changes to source code throughout the software development lifecycle. SCM involves using specialized tools and practices to manage the versioning, collaboration, and organization of source code files. It allows multiple developers to work on a project simultaneously, keeps a history of changes, facilitates code merging and branching, and helps maintain the integrity and traceability of the codebase.

**Centralized VCS (CVCS):** 
Examples include Subversion (SVN), where a central repository stores the code, and developers check out and commit changes to this central location.

**Distributed VCS (DVCS):** 
Examples include Git and Mercurial. In DVCS, each developer has a complete copy of the repository, allowing for more flexibility and easier branching.

![maxresdefault (2)](https://github.com/sagarkulkarni1989/DevOps-Journey/assets/46215433/85953552-8245-4798-a9c8-3d412f64c4cf)

**Available tools:**
- GitHub
- Git
- GitLab
- Apache Subversion (SVN)
- Bitbucket Server
- Team Foundation Server (TFS)

**Git:** Git is a distributed version control system (VCS) that allows developers to track changes in source code during software development. It provides features like version history, branching, merging, and collaboration. Git operates locally on the developer's machine, allowing them to work offline and commit changes to their local repository. It's known for its speed, efficiency, and flexibility.

**GitHub:** GitHub is a web-based hosting service for Git repositories. It provides a platform for collaborative software development and offers features like pull requests, issue tracking, code reviews, project management tools, and documentation. 

**GitLab:** GitLab is a web-based DevOps platform that provides both source code management and a variety of other features like CI/CD pipelines, issue tracking, project management, and container registry. It is similar to GitHub but aims to offer a complete end-to-end DevOps solution in a single application.

**Bitbucket:** Bitbucket is a web-based platform that supports both Git and Mercurial repositories. It offers features like source code hosting, pull requests, issue tracking, code reviews, and integration with other Atlassian tools such as Jira and Confluence. Bitbucket is popular among smaller development teams, startups, and organizations that use other Atlassian products.

While Git is the core version control system that allows developers to manage source code changes locally, GitHub, GitLab, and Bitbucket provide platforms for hosting Git repositories and additional collaboration and project management features. 

**Git architecture**

**git init** The command git init is used to create an empty Git repository. 

**git add .**  We need to use the git add command to include the changes of a file(s) into our next commit. 

```
git add <file>

```
**git commit**  

```
git commit -m "commit message"
```



**git remote**

**Git push:** git push <remote> <branch-name>

**git clone :** Git clone is a command for downloading existing source code from a remote repository (like Github, for example).

```
git clone <https://name-of-the-repository-link>
```
**Git branch:** By using branches, several developers are able to work in parallel on the same project simultaneously.

```
git branch <branch-name>    #This command will create a branch locally. To push the new branch into the remote repository,

git push -u <remote> <branch-name>

Viewing branches: git branch or git branch --list
Deleting a branch: git branch -d <branch-name>

```
**Git checkout :** We use git checkout mostly for switching from one branch to another.

```
git checkout <name-of-your-branch>
git checkout -b <name-of-your-branch>

```
Git status: gives us all the necessary information about the current branch. 

**GIT Merge and Rebase**

Git merge and rebase are two different strategies used to incorporate changes from one branch into another branch in Git version control.

**Git Merge:**

- Merging is a strategy that combines changes from one branch (the source branch) into another branch (the target branch).
- When you merge a branch, Git creates a new merge commit that represents the combination of changes from the source branch.
- The merge commit preserves the history of both branches, showing that they have been merged together at a specific point in time.

**Git Rebase:**

- Rebasing is a strategy that integrates changes from one branch onto another by moving or replaying commits from the source branch onto the target branch.
- When you rebase a branch, Git applies the commits from the source branch onto the tip of the target branch, resulting in a linear commit history.
- Unlike merging, which creates merge commits, rebasing replays commits on top of the target branch, maintaining a cleaner and more linear history.

**Practical : Git merge and Rebase ????**

**Git pull and fetch**

In Git, both git pull and git fetch are used to update your local repository with changes from a remote repository.

**Git Fetch:**

- git fetch retrieves the latest changes from a remote repository but does not merge them into your current branch.
- It updates your local copy of the remote branches, allowing you to see any new commits made by others.
- Fetching is a safe operation that does not modify your local branches or working directory.
- After fetching, you can inspect the fetched changes and decide how to integrate them into your local branches.

**Git Pull:**

- git pull combines the fetching of changes from a remote repository with the automatic merging of those changes into your current branch.
- It fetches the latest changes from the remote repository and merges them into your current branch in one step.
- Pulling is a convenient way to quickly update your branch with the latest changes and incorporate them into your working directory.

**Practical -- Git pull and fetch ???**

**git revert:** 

- The git revert command creates a new commit that undoes the changes made in a previous commit.
- It is a safe way to revert changes as it doesn't alter the commit history but instead adds a new commit that undoes the changes.
- This command is suitable when you want to revert changes while preserving the commit history and allowing for easy future reference.
- git revert <commit_id>

**git reset**

- The git reset command allows you to move the current branch to a specific commit, effectively removing commits from the branch's history.
- It is a more powerful command that can be used to remove commits permanently.
- This command is suitable when you want to remove one or more commits entirely and do not need to preserve them in the history.
- git reset <commit_id>

**Practical - git revert and reset ??**

**git stash**

In Git, the git stash command is used to temporarily save changes that you have made to your working directory, allowing you to switch branches or perform other operations without committing your changes.
- To apply the changes from a stash and bring them back to your working directory, you can use git stash apply.
- To remove a stash from the stash stack, you can use git stash drop.
- If you want to apply and remove a stash in a single step, you can use git stash pop.

git cherry-pick



