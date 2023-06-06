# GIT Practice Notes
## Introduction 

* Distributed Version Control System
* Options for remote repo :
    1.Self hosted
    2.Cloud hosted
* Github : opensource (now acquired by Microsoft)
* using of cheatsheet

## Git Workflow

![1.jpg](git/1.jpg)

## Git as local repository
* Having one user and one system
* Repository - storage space - maintaining history,
    e.g: google drive

## Starting with GitBash

* we enter into the directory/folder using cd - c/Git-Practice
* we create a folder (hellogit) inisde the first folder
* using pwd we can know the current directory
* using start . the window will open where the folder/directory being created

![2.jpg](git/2.jpg)


* For making it a local repo we use git init command (.git folder with some sub folders gets created in the previous window)

![3.jpg](git/3.jpg)

* In the .git folder we have both local repo and the working tree
* Here hellogit is the working tree
* Now the changes versioned will be stored(history stored) in the local repo
* Now we create a folder src (coding done area) and a python based empty file (file.py)
* To check for any changes happened we ask for git status.
* To ask for status we need to be in the .git folder or it's subfolders

![4.jpg](git/4.jpg)

* For here we have folder src (we have a change)
* Now to move the changes from working tree to staging area we use add command
* Now the color changes from red to green

![5.jpg](git/5.jpg)

* To tell git about when you are changing and what are being changed 
* To move the changes from staging area to the local repo we commit them along with the message -m
* Every commit in git is a history recorded

![6.jpg](git/6.jpg)

* Now check the status
* 'Working tree clean' in the status, shows that every thing we have in the working tree and the local repo are same
* Now to check the history we use log command( git log )
* To show the history in a single line we use (git log --oneline)
* Every strange number for commit is the commit id

![7.jpg](git/7.jpg)

* Now we do another change, check status, add changes and finally commit the changes

![8.jpg](git/8.jpg)

![9.jpg](git/9.jpg)

![10.jpg](git/10.jpg)

* Travelling back and forth with the commit id's using the checkout command

![11.jpg](git/11.jpg)

![12.jpg](git/12.jpg)

## Hashing (Commit ID)
* generates random numbers
* message is same, so the hash will be same
* Even a message is large, the hash created remains of same no.of digits
 
 ## Creating a senerio
 * First commit - create folder understanding with src,test folders
 * Second commit - Add files to src,test foleders (main.py, each)
 * Third commit - Add any content into the files
 * make log for the above commits

![13.jpg](git/13.JPG)

![14.jpg](git/14.JPG)
 
## Plumbing Commands
For better understanding, we use these commands

* git cat-file -t (type we are lokking at)
* git cat-file -p (prints the values)

![15.jpg](git/15.JPG)

* Types and contents of the commit made :
  1. Parent - previous commit
  2. Author/Commiter - username & email configured
  3. Message - the message we give
  4. Tree - folder/directory
  5. Blob - file

* let's check for previous commits

![16.jpg](git/16.jpg)

* Now checking the commit contents

First Commit

![17.jpg](git/17.JPG)

Second Commit

* Here the contents from the previous commit, so the hash will be same for both src and test files

![18.jpg](git/18.JPG)

* Now check the contents of the src file
 Here the hash of the blob of src and the Readme.md will be same as the content remains the same

![20.jpg](git/20.JPG)

Here src is an empty file

![21.jpg](git/21.JPG)

Third Commit

![19.jpg](git/19.JPG)

* Now opening the tree

![22.jpg](git/22.JPG)

* Now opening contents of the src file

![23.jpg](git/23.JPG)

* Now displaying the content of the file

![24.jpg](git/24.JPG)

# Git Branching

* Branch in git always points to a latest commit id
* We checkout for branches using git branch command
* Master - points to the latest commit
* Branch allows us for parallel development in the same repo

* Now let's create a local repo and (git init) into it

![25.jpg](git/25.JPG)

* Make some changes having folders and files

![26.jpg](git/26.JPG)

* Add and Commit the changes

![27.jpg](git/27.JPG)

* Making another change and commit

![28.jpg](git/28.JPG)

* Here the head and master both pointing to the same commit(latest commit)
* Now we create a branch R-1(First release) where the head points to the branch 

![29.jpg](git/29.JPG)

* Here after moving into the branch using checkout command , now both he master and the head points to the branch

![30.jpg](git/30.JPG)

* Now when we add a change in the branch and commit it, head points to the branch or latest commit made

![31.jpg](git/31.JPG)

*Now we got to master and check the history

![32.jpg](git/32.JPG)

* Now let's make changes to the master
* To update only the modified files we use, (git add -u) command
* Now both head and master points to this latest commit

![33.jpg](git/33.JPG)

* To have changes from one branch to another,we need to work with
    1. Merge - Three-way merge
             - no fast forward merge
    2. Rebase
    3. Cherry pick   

* The above processes may also lead to some conflicts (Merge conflicts)

## Git Merging
* create a new folder (branches_demo) and make it a local repo
* Make the changes,add and commit

![34.jpg](git/34.JPG)

* Now let's change the branch name from master to main

![35.jpg](git/35.JPG)

* create a commit on main

![36.jpg](git/36.JPG)

![37.jpg](git/37.JPG)

* Let's create a branch sprint from the main branch
  (git checkout -b sprint)
          or
  (git branch sprint, git checkout sprint)
* Here the sprint also points to the same commit such as main

![38.jpg](git/38.JPG)    

* we make a change in the sprint and also create a file
* To only add modified files ignoring the new created files, we use (git add -u)

![39.jpg](git/39.JPG)

## FAST FORWARD MERGE

* Now the current state of the branches is

![40.jpg](git/40.JPG)

Before Merge the picture

![42.jpg](git/42.JPG)

* To obtain all the changes from the sprint branch to the main, we need to merge and to achieve that we need to be present in the target branch(i.e, main)
* This is called the FAST-FORWARD merge
* Here the merge happens as the main combines with the latest commit(i.e, sprint)

After Merge the picture

![43.jpg](git/43.JPG)

Command Section

![41.jpg](git/41.JPG)

## THREE WAY MERGE

* Now make changes and commit to main branch

![44.jpg](git/44.JPG)

* Here we have added msg to src/main.py, added only the modified file and commited
* So we have 3 commit's now

![45.jpg](git/45.JPG)

* Current state

![46.jpg](git/46.JPG)

* Now we have different msg in both the src files of main branch and sprint branch
* Now while we merge there arises a conflict as to which to be stored, but for the test file there is only 1 msg stored (no conflict)
* This is to be resolved by the developer as to choose the display

![47.jpg](git/47.JPG)

* Now the new commit has to be made with a main commit and a sprint commit
* Three commit's being involved (3 way merge)

![48.jpg](git/48.JPG)

* To resolve this conflict, we use notepad editor along with git generated lines as

![49.jpg](git/49.JPG)

* Now make the changes and save the file as

![50.jpg](git/50.JPG)

* And the command line follows as

![51.jpg](git/51.JPG)

* Here the merge commit has two parents and also the graph (git log --graph --all)represented as

![52.jpg](git/52.JPG)

![53.jpg](git/53.JPG)

## EXERCISE

![54.jpg](git/54.JPG)

## SOLUTION

![55.jpg](git/55.JPG)

![56.jpg](git/56.JPG)

* branches created

![57.jpg](git/57.JPG)

![58.jpg](git/58.JPG)

* commit a change in sprint_poc

![59.jpg](git/59.JPG)

![60.jpg](git/60.JPG)

* commit a change in sprint_dev

![61.jpg](git/61.JPG)

![62.jpg](git/62.JPG)

* Merging sprint_poc into sprint_dev

![63.jpg](git/63.JPG)

![64.jpg](git/64.JPG)

* We look at all the senerio using graph representation using (git log --graph --oneline --all)command

![65.jpg](git/65.JPG)

![66.jpg](git/66.JPG)

## Git Rebase

* Create a scenerio as follows

![67.jpg](git/67.JPG)

![68.jpg](git/68.JPG)

* Rebase is a command used to get changes from one branch to other by rewriting history
* Make two changes and commit them in the main branch
* To directly add and commit at same time we use (git commit -am "message") command

![69.jpg](git/69.JPG)

![70.jpg](git/70.JPG)

![71.jpg](git/71.JPG)

* Now the chnages in the main branch to be merged into sprint branch, we have two ways to do this

1. Three way merge as follows (confusing approach)

![72.jpg](git/72.JPG)

2. Rebase as follows (cleaner approach)

* Rebase is useful for all the child branches but never rebase main/master from child as rebase rewrites history.
* To rebase we checkout sprint and rebase to main using (git rebase main) command

![73.jpg](git/73.JPG)

![74.jpg](git/74.JPG)

* Here arises a merge conflict, with the src/main.py
* we open the file in notepad, edit with changes and now rebase again using (git rebase --continue) command

![75.jpg](git/75.JPG)

![76.jpg](git/76.JPG)

![77.jpg](git/77.JPG)

* Now after the rebase the commit id of the sprint branch gets changed as the parent get's changed and also shows that it is replaced after the main branch

![78.jpg](git/78.JPG)

* This is nothing but the rewriting of the history

## Git Cherry pick

* If we need to pick specific commits or specific range of commits (sequence) of commits , cherry pick can be used
* Firstly, we add two commits

![79.jpg](git/79.JPG)

![80.jpg](git/80.JPG)

* Performing changes from any commit to any branch
* Now consider the above, we want changes from commit (commit id - 97bb278) into main branch
* So we use cherry pick
 * first checkout the target/destination
 * use cherry-pick(git cherry-pick 97bb278)command

![81.jpg](git/81.JPG)

## Remote Repository

* Git Remote Repository is any folder on any server
* To make Git Remote accessible, generally two protocols are widely used
   1. http(s)
   2. ssh
* There are many popular Git Repositories which are available for free.
* lets get started with GitHub
* Create a new repository in GitHub








 

  


 

 