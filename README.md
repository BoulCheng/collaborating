# The project is a sample for [Collaborating with issues and pull requests](https://help.github.com/en/categories/collaborating-with-issues-and-pull-requests)


# Github Help Notes

## Collaborating with issues and pull requests

### Working with forks
#### About forks
Any user or organization on GitHub can fork a repository. Forking a repository is similar to copying another repository, with two major differences:

- You can use a pull request to suggest changes from your fork to the original repository, also known as the upstream repository.
- You can bring changes from the upstream repository to your local fork by synchronizing your fork with the upstream repository.

When you make changes in your fork and open a pull request that compares your work to the upstream repository, you can give anyone with push access to the upstream repository permission to push changes to your pull request branch.

#### Configuring a remote for a fork (mac)
You must configure a remote that points to the upstream repository in Git to sync changes you make in a fork with the original repository. This also allows you to sync changes made in the original repository with the fork.
- List the current configured remote repository for your fork.
```
$ git remote -v
> origin  https://github.com/YOUR_USERNAME/YOUR_FORK.git (fetch)
> origin  https://github.com/YOUR_USERNAME/YOUR_FORK.git (push)
```
- Specify a new remote upstream repository that will be synced with the fork.
```
$ git remote add upstream https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git
```
- sample
```
zhenglubiaodeMacBook-Pro:collaborating zlb$ 
zhenglubiaodeMacBook-Pro:collaborating zlb$ pwd
/Users/zlb/IdeaProjects/lb/fork/collaborating
zhenglubiaodeMacBook-Pro:collaborating zlb$ 
zhenglubiaodeMacBook-Pro:collaborating zlb$ 
zhenglubiaodeMacBook-Pro:collaborating zlb$ 
zhenglubiaodeMacBook-Pro:collaborating zlb$ git remote -v
origin  https://github.com/lubiaozheng/collaborating.git (fetch)
origin  https://github.com/lubiaozheng/collaborating.git (push)
zhenglubiaodeMacBook-Pro:collaborating zlb$ 
zhenglubiaodeMacBook-Pro:collaborating zlb$ 
zhenglubiaodeMacBook-Pro:collaborating zlb$ git remote add upstream https://github.com/BoulCheng/collaborating.git
zhenglubiaodeMacBook-Pro:collaborating zlb$ git remote -v
origin  https://github.com/lubiaozheng/collaborating.git (fetch)
origin  https://github.com/lubiaozheng/collaborating.git (push)
upstream        https://github.com/BoulCheng/collaborating.git (fetch)
upstream        https://github.com/BoulCheng/collaborating.git (push)
zhenglubiaodeMacBook-Pro:collaborating zlb$ 
zhenglubiaodeMacBook-Pro:collaborating zlb$ 
```

#### Syncing a fork
Sync a fork of a repository to keep it up-to-date with the upstream repository.

Fetch the branches and their respective commits from the upstream repository. Commits to master will be stored in a local branch, upstream/master.
```
$ git fetch upstream
```
Merge the changes from upstream/master into your local master branch. This brings your fork's master branch into sync with the upstream repository, without losing your local changes.
```
$ git checkout master
$ git merge upstream/master
```
- sample
```
zhenglubiaodeMacBook-Pro:collaborating zlb$ git remote -v 
origin  https://github.com/lubiaozheng/collaborating.git (fetch)
origin  https://github.com/lubiaozheng/collaborating.git (push)
upstream        https://github.com/BoulCheng/collaborating.git (fetch)
upstream        https://github.com/BoulCheng/collaborating.git (push)
zhenglubiaodeMacBook-Pro:collaborating zlb$ 
zhenglubiaodeMacBook-Pro:collaborating zlb$ 
zhenglubiaodeMacBook-Pro:collaborating zlb$ pwd
/Users/zlb/IdeaProjects/lb/fork/collaborating
zhenglubiaodeMacBook-Pro:collaborating zlb$ 
zhenglubiaodeMacBook-Pro:collaborating zlb$ 
zhenglubiaodeMacBook-Pro:collaborating zlb$ 
zhenglubiaodeMacBook-Pro:collaborating zlb$ git merge upstream/master
merge: upstream/master - not something we can merge
zhenglubiaodeMacBook-Pro:collaborating zlb$ 
zhenglubiaodeMacBook-Pro:collaborating zlb$ 
zhenglubiaodeMacBook-Pro:collaborating zlb$ git fetch upstream 
remote: Enumerating objects: 14, done.
remote: Counting objects: 100% (14/14), done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 8 (delta 1), reused 8 (delta 1), pack-reused 0
Unpacking objects: 100% (8/8), done.
From https://github.com/BoulCheng/collaborating
 * [new branch]      master     -> upstream/master
zhenglubiaodeMacBook-Pro:collaborating zlb$ 
zhenglubiaodeMacBook-Pro:collaborating zlb$ 
zhenglubiaodeMacBook-Pro:collaborating zlb$ git merge upstream/master
Updating e3a80fe..7c3dee3
Fast-forward
 collaborating.iml                      | 2 --
 src/main/java/com/zlb/UpstreamAdd.java | 9 +++++++++
 2 files changed, 9 insertions(+), 2 deletions(-)
 delete mode 100644 collaborating.iml
 create mode 100644 src/main/java/com/zlb/UpstreamAdd.java
zhenglubiaodeMacBook-Pro:collaborating zlb$ 
zhenglubiaodeMacBook-Pro:collaborating zlb$ 
zhenglubiaodeMacBook-Pro:collaborating zlb$ git push origin master:master
Username for 'https://github.com': 1964530386@qq.com
Password for 'https://1964530386@qq.com@github.com': 
Counting objects: 8, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (5/5), done.
Writing objects: 100% (8/8), 666 bytes | 666.00 KiB/s, done.
Total 8 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/lubiaozheng/collaborating.git
   e3a80fe..7c3dee3  master -> master
zhenglubiaodeMacBook-Pro:collaborating zlb$ 
```

#### Merging an upstream repository into your fork
Check out the branch you wish to merge to. Usually, you will merge into master.
```
$ git checkout master
```
Pull the desired branch from the upstream repository. This method will retain the commit history without modification.
```
$ git pull https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git BRANCH_NAME
```
If there are conflicts, resolve them. For more information, see "Addressing merge conflicts".
Push the merge to your GitHub repository.
```
$ git push origin master
```
- sample
```
zhenglubiaodeMacBook-Pro:collaborating zlb$ 
zhenglubiaodeMacBook-Pro:collaborating zlb$ git checkout master 
Already on 'master'
Your branch is up to date with 'origin/master'.
zhenglubiaodeMacBook-Pro:collaborating zlb$ 
zhenglubiaodeMacBook-Pro:collaborating zlb$ git remote -v 
origin  https://github.com/lubiaozheng/collaborating.git (fetch)
origin  https://github.com/lubiaozheng/collaborating.git (push)
upstream        https://github.com/BoulCheng/collaborating.git (fetch)
upstream        https://github.com/BoulCheng/collaborating.git (push)
zhenglubiaodeMacBook-Pro:collaborating zlb$ 
zhenglubiaodeMacBook-Pro:collaborating zlb$ git pull https://github.com/BoulCheng/collaborating.git master
From https://github.com/BoulCheng/collaborating
 * branch            master     -> FETCH_HEAD
Already up to date.
zhenglubiaodeMacBook-Pro:collaborating zlb$ git pull https://github.com/BoulCheng/collaborating.git master
remote: Enumerating objects: 14, done.
remote: Counting objects: 100% (14/14), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 8 (delta 2), reused 8 (delta 2), pack-reused 0
Unpacking objects: 100% (8/8), done.
From https://github.com/BoulCheng/collaborating
 * branch            master     -> FETCH_HEAD
Updating 7c3dee3..3149b63
Fast-forward
 src/main/java/com/zlb/UpstreamAddB.java | 9 +++++++++
 1 file changed, 9 insertions(+)
 create mode 100644 src/main/java/com/zlb/UpstreamAddB.java
zhenglubiaodeMacBook-Pro:collaborating zlb$ 
zhenglubiaodeMacBook-Pro:collaborating zlb$ 
zhenglubiaodeMacBook-Pro:collaborating zlb$ git push origin master:master
Username for 'https://github.com': 1964530386@qq.com
Password for 'https://1964530386@qq.com@github.com': 
Counting objects: 8, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (5/5), done.
Writing objects: 100% (8/8), 629 bytes | 629.00 KiB/s, done.
Total 8 (delta 2), reused 0 (delta 0)
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To https://github.com/lubiaozheng/collaborating.git
   7c3dee3..3149b63  master -> master
zhenglubiaodeMacBook-Pro:collaborating zlb$ 
```


### Proposing changes to your work with pull requests
#### About branches
You can merge a branch into another branch using a pull request.
The default branch is considered the base branch in your repository, against which all pull requests and code commits are automatically made, unless you specify a different branch.

Repository administrators can enable protections on a branch. If you're working on a branch that's protected, you won't be able to delete or force push to the branch. Repository administrators can additionally enable several other protected branch settings to enforce various workflows before a branch can be merged.

To see if your pull request can be merged, look in the merge box at the bottom of the pull request's Conversation tab

#### Creating and deleting branches within your repository
forks is disabled ? 

#### About pull requests
Pull requests let you tell others about changes you've pushed to a branch in a repository on GitHub. Once a pull request is opened, you can discuss and review the potential changes with collaborators and add follow-up commits before your changes are merged into the base branch.
- About pull requests
Once you've created a pull request, you can push commits from your topic branch to add them to your existing pull request. These commits will appear in chronological order within your pull request and the changes will be visible in the "Files changed" tab.
Other contributors can review your proposed changes, add review comments, contribute to the pull request discussion, and even add commits to the pull request.
You can see information about the branch's current deployment status and past deployment activity on the "Conversation" tab.

- Draft pull requests
When you create a pull request, you can choose to create a pull request that is ready for review or a draft pull request. Draft pull requests cannot be merged, and code owners are not automatically requested to review draft pull requests.
When you're ready to get feedback on your draft pull request, you can mark your pull request as ready for review. Then, the pull request can be merged, and code owners will be requested to review the pull request

- tip
The way you use pull requests depends on the type of development model you use in your project.
There are two main types of development models with which you'd use pull requests.
	- fork and pull model
	In the fork and pull model, anyone can fork an existing repository and push changes to their personal fork without needing access to the source repository.
	This model is popular with open source projects as it reduces the amount of friction for new contributors and allows people to work independently without upfront coordination.
	- shared repository model
	In the shared repository model, collaborators are granted push access to a single shared repository and topic branches are created when changes need to be made.
	This model is more prevalent with small teams and organizations collaborating on private projects.

#### About comparing branches in pull requests

#### Creating a pull request
Create a pull request to propose and collaborate on changes to a repository. These changes are proposed in a branch, which ensures that the master branch only contains finished and approved work.
By default, pull requests are based on the parent repository's default branch.

When thinking about branches, remember that the base branch is where changes should be applied, the head branch contains what you would like to be applied.

When you change the base repository, you also change notifications for the pull request. Everyone that can push to the base repository will receive an email notification and see the new pull request in their dashboard the next time they sign in.

#### Creating a pull request from a fork
If you've forked a repository and made changes to the fork, you can ask that the upstream repository accept your changes by creating a pull request.

You also have the option to give the upstream repository's maintainers the ability to make commits on your topic branch to update your pull request

If your pull request compares your topic branch with a branch in the upstream repository as the base branch, then your topic branch is also called the compare branch of the pull request

- step tip 
	- Navigate to the original repository(the upstream repository) you created your fork from.
	- On the Compare page, click compare across forks.
	- If you do not want to allow anyone with push access to the upstream repository to make changes to your PR, unselect Allow edits from maintainers.

#### Changing the stage of a pull request
Pull request authors and anyone with admin permissions for the repository can mark a draft pull request as ready for review.
When you're ready to get feedback on your draft pull request, you can mark your pull request as ready for review. Then, the pull request can be merged, and code owners will be requested to review the pull request.
Under your repository name, click  Pull requests.

#### Requesting a pull request review
After you create a pull request, you can ask a specific person to review the changes you've proposed. If you're an organization member, you can also request a specific team to review your changes.
Note: Pull request authors can't request reviews unless they are either a repository owner or collaborator with write access to the repository.

#### Changing the base branch of a pull request
After a pull request is opened, you can change the base branch to compare the changes in the pull request against a different branch.

#### Committing changes to a pull request branch created from a fork
You can commit changes on a pull request branch that was created from a fork of your repository with permission from the pull request creator.

Only the user who created the pull request can give you permission to push commits to their branch