# Basic Git Commands

> This is a list about Git commands that are frequently used while working with Git.


## 1. git init
In the project directory
```
git init
```
This command initialize a Git repository for our local project folder. Git will create a hidden .git directory and use it for keeping its files organized in other subdirectories.

## 2. git add
>git add [file(s) name]
```
git add filename
```
This will add the specified file(s) into the Git repository, the staging area, where they are already being tracked by Git and now ready to be committed.

>git add . or git add *
```
git add .
```
This will take all our files into the Git repository

### 3. git commit
```
git commit -m “message”
```
This command records or snapshots files permanently in the version history. All the files, which are there in the directory right now, are being saved in the Git file system.

## 4. git status
```
git status
```
This command will show the modified status of an existing file and the file addition status of a new file, if any, that have to be committed.



## 5. git remote

>git remote add origin “[URL]”
```
git remote add origin [URL]
```

>git remote show origin 
```
git remote show origin
```

>git remote rm originn 
```
git remote rm originn
```


## 6. git push
>Usage: git push origin [branch name]


```
git push [branch]
```
we have made some changes in the file and want to push the changes to our remote repository on a particular branch. By using the command ‘git push,’ the local repository’s files can be synced with the remote repository



## 7. git clone
>Usage: git clone [URL]
```
git clone [URL]
```

## 8. git branch
>Usage: git branch [name-of-the-branch]

Create a branch

```
git branch nameofyourbranch
```


>Usage: git branch -D [name -of-the-branch]

Delete a branch
```
git branch -D nameofyourbranch
```


## 9. git checkout
>Usage: git checkout [name-of-the-new-branch]

We use this command to navigate to an existing branch, add new files, and commit the files:
```
git checkout nameofyourbranch
```


>Usage: git checkout -b [name-of-the-new-branch]

We use this command to create a branch and navigate to that particular branch (say, the ‘name-of-the-new-branch’ is ‘branch2’) at the same time:
```
git checkout -b nameofyourbranch
```


## 10. git log
>Usage git log

This command is used when we want to check the log for every commit in detail in our repository.

```
git log
```

>Usage: git log –graph
```
git log --graph
```
>Usage: git log –graph –pretty=oneline
```
git log –graph –pretty=oneline
```

## 11. git stash
>Usage git stash

This command can be used when we want to save our work without staging or committing the code to our Git repository and want to switch between branches.
```
git log
```

>Usage: git log –graph
```
git stash
```

```
git stash save "my_stash"
git stash list
git stash apply stash@{n}
git stash pop stash@{n}
git stash show -p stash@{1}

```

>Usage: git stash -u

This command is used when we want to stash the untracked files.

```
git stash -u
```



## 12. git revert
>Usage git revert [commit id]

The git revert command can be considered as an ‘undo’ command. However, it does not work as the traditional ‘undo’ operation. It figures out how to invert the changes introduced by the commit and appends a new commit with the resulting inverse content.

<!-- ![Test Image 4](https://imgur.com/mZ8ghEd)
[Imgur](https://i.imgur.com/mZ8ghEd.png) -->
[Imgur](https://i.imgur.com/mZ8ghEd.png)


## 13. git diff
>Usage git diff [commit-id-of-version-x] [commit-id-of-version-y]

Diffing is a function that takes two input datasets and outputs the changes between them. The git diff command is a multi-use Git command which, when executed, runs a diff function on Git data sources. These data sources can be commits, branches, files, and more. The git diff command is often used along with the git status and git log commands to analyze the current state of our Git repository. We use git log to get the details of commit IDs.
```
git diff idcommit1 idcommit2
git diff HEAD~1 HEAD
```

## 14. git merge
>Usage git merge [another-file-name]

This command will combine multiple sequences of commits into one unified history. In the most frequent use cases, git merge is used to combine two branches. The git merge command takes two commit pointers, usually the branch tips, and finds a common base commit between them. Once it finds a common base commit, it will create a commit sequence.

```
git merge branch1
```

## 15. git rebase
>Usage git rebase [base]

Rebase is the process of moving and combining a sequence of commits to a new base commit. Rebasing is changing the base of our branch from one commit to another, making it appear as if we’ve created our branch from a different commit. Internally, Git accomplishes this by creating new commits and applying them to the specified base. It’s very important to understand that even though the branch looks the same, it is composed of entirely new commits.

The git rebase command performs an automatic git checkout <branch> before doing anything else. Otherwise, it remains on the current branch.

```
git rebase origin master
```

Consider a situation where we have branched off from the master and have created a feature branch, but the master branch is still having more commits. We want to get the updated version of the master branch in our feature branch, keeping our branch’s history clean, so that it appears as if we are working on the latest version of the master branch.

Note: We don’t rebase public history. We should never rebase commits once they are pushed to a public repository. Why because the rebase would replace the old commits with the new ones, and it would appear that a part of our project history got abruptly vanished.



## 16. git fetch
>Usage git merge [another-file-name]

When we use the command git fetch, Git gathers any commit from the target branch that does not exist in our current branch and stores it in our local repository. However, it does not merge it with our current branch.

```
git fetch --all
```

This is particularly useful when we need to keep our repository up to date but are working on something that might break if we updated our files. To integrate the commits into our master branch, we use merge. It fetches all of the branches from the repository. It also downloads all the required commits and files from another repository.



## 17. git reset
>Usage git reset –hard [SOME-COMMIT]

We use this command to return the entire working tree to the last committed state.

```
git reset -hard
```
This will discard commits in a private branch or throw away the uncommitted changes!

Here, we have executed a ‘hard reset’ using the –hard option. Git displays the output indicating that the HEAD is pointing to the latest commit. Now, when we check the state of the repo with git status, Git will indicate that there are no pending changes (if any prior addition of a new file or modification of an existing file is done before using the ‘git reset –hard’ command). Our modifications to an existing file, if not committed, and the addition of a new file, if not staged, will be destroyed. It is critical to take note that this data loss cannot be undone.

If we do git reset –hard [SOME-COMMIT], then Git will:

*Make our current branch (typically master) back to point < SOME-COMMIT>

*Make the files in our working tree and the index (“staging area”) the same as the versions committed at < SOME-COMMIT>



If the commit you want to get rid of was the last commit, and you have not done any additional work you can simply use git-reset
```
git reset HEAD^
```
Takes your branch back to the commit just before your current HEAD. However, it doesn't actually change the files in your working tree. As a result, the changes that were in that commit show up as modified - its like an 'uncommit' command.

## 18. git pull
>Usage git pull origin master

The git pull command first runs ‘git fetch’ which downloads the content from the specified remote repository and then immediately updates the local repo to match the content.
```
git git pull origin master
```

## 18. git log
>Usage git log

The git log command is atool allows you to view information about previous commits that have occurred in a project. 
```
git log
git log --all
git log --oneline
git log --oneline --decorate
git log --oneline | cat
git log --author <name>
git log --committer <name>
git log --before <date>
git log --after <date>

```


## 18. git clean [-d] [-f] [-i] [-n] [-q] [-e <pattern>] [-x | -X] [--] <path>…
>Usage git clean -n
Print out the list of files which will be removed (dry run)
  
>Usage git clean -n
Delete the files from the repository
```
git clean -n
git clean -f
```
