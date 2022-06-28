
full script: https://github.com/freeCodeCamp/learn-git-by-building-an-sql-reference-object/blob/main/TUTORIAL.md


## bash 

mkdir <foldername> = make new folder

cd <foldername> = change directory" 

cd ~/project/sql_reference

### touch .env 
.env files are used to store environment variables for running code. Often times, there may be sensitive information in it. Add the text SECRET=MY_SECRET to the file.

## GIT

= Git is a version control system to keep track of your code.

*** The process is to create a branch, make the changes you want, commit them, and then merge the changes into branch you started on. Pretty simple, lets keep going. ***

### git init
turn folder in git repository
(type in terminal)
-> codeally@b1af495b8637:~/project/sql_reference$ ls -a
.  ..  .git (git init create hidden git folder)

### git status 
= to see the status of where you are

### git diff
--> You can see the changes you made

### branches 

--> A git repository has branches to help keep track of things you are doing with your code

= main  branch which might be for your production code
= other branches for adding new features or fixing bugs

### git branch branch_name
--> You can create a branch 
--> fix/ or feat/
ex: git branch feat/add-create-table-reference

--> our new branch is a clone of the main branch since that's the branch you were on when you created it.

*** when you create a branch, it will be a clone of whatever branch you are on when you create it. *** 

### git checkout -b new_branch
You can create and go to a new branch
ex: git checkout -b main 
--> The -b stands for "branch"

### git checkout branch_name
--> Switch to your branch.
"*" = marks the branch you working on 
ex: git checkout main

--> this branch will be for some new changes. What you will do is make the changes and commits here, then merge them into the main branch when they are ready.

### Create and checkout a branch named feat/add-gitignore
git checkout -b feat/add-gitignore
--> ADDING filename (ex: .env to .gitignore file) --> Now the .env file is being ignored by git because you added it to the .gitignore file. There are often a number of things you don't want to include in a repository, especially if it's publicly visible. Now, you know how to keep them from being tracked by git. Add your new changes to staging.

### git merge branch_name
--> bring changes from a branch into the branch you are currently on


### git rebase main
--> Since then, a commit for a bug fix was added to main. This is common with many people working on a codebase simultaneously. You need to update this branch so it has the same commits from main, but you can't just merge that branch into this one. You need that bug fix commit to be in the same order here as it is on main, right after the "drop table" commit.
ex: git rebase main 

---> Now, when this branch is ready to be merged into main, it will have the same commit history. You should try to keep your branches up to date like this by rebasing them often.

--> There was a commit to main since you last worked on this from when you merged the "add more row references" branch. Rebase this branch against main so it's up to date and you can finish working on it.

### conflicts for rebase:
-->  confict arose because the first commit you added to this branch changed the same lines as the commit from main
-->  There are sections, separated by characters (<, >, and =), that represent the commit you are on (HEAD) and the commit that is trying to be added (feat: add column reference

### after fixing conflicts
git rebase --continue


### git branch -d branch_name
= -d stands for "delete"
-->  delete a branch

### git stash
--> put your changes aside --> Stash your changes so you can add them to a different branch.

### git stash list
--> View the things you have stashed 
### You can use the name at the front of each stash 
= stash@{#}

### git stash pop
Bring the changes back

### git stash show
-->  View a condensed version of the changes in the latest stash
### You can use the name at the front of each stash
= git stash show stash@{0}

### git stash show -p
--> View the full changes of the latest stash 
--> -p stands for "patch".

### git stash apply
--> add the latest stash while keeping it in the list

### git stash drop
git stash drop <stash_name>


### touch <foldername>
= create folder in branch after go to branch 

--> The file you created has not been added to git yet so it is showing that it is untracked. 

Solution:

1. 

### git add file_name
= Add your file to the staging area

2. Now you have files in staging.

### git commit -m "Initial commit"
--> -m stands for "message"
= To commit files
--> fix: or feat: to help people understand what your commit was for.
ex: git commit -m "feat: add create database reference"

after: --> nothing to commit, working tree clean

### remove or undo a commit: 
git reset command to travel to any point in your commit history.
### git reset HEAD~1
--> If the message is wrong --> then git add ., and then you can try to make the commit again
#### If you used the --hard flag with the reset, the changes would have not been added to the working tree. 
### git revert HEAD
Reverting is a good way to undo a commit because you don't lose the commit from the history. 
### git rebase --interactive HEAD~2 
The HEAD~2 means you will have a chance to change the last two commits.
--> At the top of Nano, you can see the two commits with pick next to them. Below them, there's a list of options for working with them. pick means that it will use the commits as they were. At the bottom, it says, d, drop = remove commit. Replace the word pick preceeding your two commits with a d to drop them both. When you are done, save the file and exit Nano.
### git rebase --interactive --root
--root means that the rebase will go back to your very first commit.

### Nano: Squash feat/add-column-references Commits
1. git rebase --interactive HEAD~5
Squashing commits means that you will take a bunch of commits and turn them into one. This is helpful to keep your commit history clean and something you want try to do. Replace pick with an s next to all your commits except the one with the message feat: add column references. When you are done, save and exit the file. You will find yourself in another instance of Nano. Don't change anything in it yet.
2. Replace pick with an s next to the suggested commits
3. Save and exit the file by pressing ctrl+x then y then enter



### git log
= to see commmit history 
### --oneline flag 
= condense the output so it's more readable.
ex: git log --oneline
### -1 instead of --oneline 
this time to view only the last commit.
ex: git log -1


## JSON

### create an object with a reference for how to create a database 

{
  "database": {
    "create": "CREATE DATABASE database_name;"
  }
}

### explained 

{
  "database" *** = object: {
    "create" *** = key: "CREATE DATABASE database_name;"
  }
}