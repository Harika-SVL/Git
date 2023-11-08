## Version Control Systems

* Software which helps organizations to maintain the source code
* VCS helps in `maintaining history of changes` and also allows us to maintain track of different releases which we give to customers
* It allows `parallel development` by multiple developers

### Types of VCS

  1. Local Version Control System
  2. Centralized Version Control System

![Alt text](shots/110.PNG)

  3. Distributed Version Control System

![Alt text](shots/111.PNG)

## Git 

* _**Distributed Version Control System**_
* Options for remote repos :
  
  1. Self hosted
     * Host it on your own
     * Options :
        * Gitolite
        * Git lab Selfhosted

  2. Cloud hosted
     * Hosted by some service provider
     * Options :
        * GitHub
        * GitLab
        * Azure Source Repos
        * AWS Code Commit
        * Bit Bucket
          
* `GITHUB` : OpenSource (now acquired by Microsoft)
* History of Git :

[Refer here : https://git-scm.com/book/en/v2/Getting-Started-A-Short-History-of-Git ]

* Cheatsheet for Github  (downloaded)

[Refer here : C:\Users\Harika\Desktop\DEVOPS + AWS\DEVOPS ]

### Git Workflow

![Alt text](shots/1.jpg)

### Git as local repository

* Having one user and one system
* Repository - storage space - maintaining history,
  e.g: google drive

### Starting with GitBash

* We enter into the `directory/`folder using `cd c/Git-Practice/`
* Create a folder `hellogit` inisde the first folder
* Using `pwd`(Pesent Working Directory) we can know the current directory
* Using `start .` the window will open where the folder/directory being created

![Alt text](shots/2.jpg)

* For making it a local repo we use `git init` command (.git folder with some sub folders gets created in the previous window)

![Alt text](shots/3.jpg)

* In the `.git` folder we have both local repo and the working tree
* Here `hellogit` is the working tree
* Now the changes versioned will be stored (history stored) in the local repo
* Now we create a folder `src` (coding done area) and a python based empty file `file.py`
* To check for any changes happened we ask for `git status`
* To ask for status we need to be in the `.git` folder or it's subfolders

![Alt text](shots/4.jpg)

* For here we have folder `src` (we have a change)
* Now to move the changes _**from working tree to staging area**_ we use `add` command
* Now the color changes from `red to green` to tell git about when you are changing and what are being changed 

![Alt text](shots/5.jpg)

* To move the changes _**from staging area to the local repo**_ we `commit` them along with the `message -m`
* Every `commit in git is a history recorded`

![Alt text](shots/6.jpg)

* Now check the status
* 'Working tree clean' in the status, shows that every thing we have in the working tree and the local repo are same
* Now to _**check the history**_ we use `log` command `git log`
* To show the history in a single line we use `git log --oneline`
* Every strange number for commit is the `commit id`

![Alt text](shots/7.jpg)

* Now we do another change, check status, add changes and finally commit the changes

![Alt text](shots/8.jpg)

![Alt text](shots/9.jpg)

![Alt text](shots/10.jpg)

* _**Travelling back and forth**_ with the commit id's using the `checkout` command

![Alt text](shots/11.jpg)

![Alt text](shots/12.jpg)

## Hashing (Commit ID)

* generates random numbers
* message is same, so the hash will be same
* Even a message is large, the hash created remains of same no.of digits
 
 ## Creating a senerio

 * First commit - create folder understanding with src, test folders
 * Second commit - Add files to src, test folders (main.py, each)
 * Third commit - Add any content into the files
 * Find logs for the above commits :

![Alt text](shots/112.PNG)

![Alt text](shots/13.JPG)

![Alt text](shots/14.JPG)
 
## Plumbing Commands

* For better understanding, we use these commands :
```
git cat-file -t <commit-ID> (type of content in the file)
git cat-file -p <commit-ID> (prints the content of the file)
```
![Alt text](shots/15.JPG)

* Type and contents of the commits made :

  1. Parent - previous commit
  2. Author/Commiter - username & email configured
  3. Message - the message we give
  4. Tree - folder/directory
  5. Blob - file

* Let's check for previous commits :

![Alt text](shots/16.jpg)

* Now checking the commit contents :

  1. First Commit

![Alt text](shots/17.JPG)

  2. Second Commit

* Here the contents from the previous commit, so the hash will be same for both src and test files

![Alt text](shots/18.JPG)

* Now check the contents of the src file
* Here the _**hash**_ of the blob of src and the Readme.md will be _**same**_ as the _**content remains the same**_

![Alt text](shots/20.JPG)

* Here src is an `empty file`

![Alt text](shots/21.JPG)

  3. Third Commit

![Alt text](shots/19.JPG)

* Now opening the tree

![Alt text](shots/22.JPG)

* Now opening contents of the src file

![Alt text](shots/23.JPG)

* Now displaying the content of the file

![Alt text](shots/24.JPG)

![Alt text](shots/113.PNG)

# Git Branching

* Branch in git always points to a latest commit id
* We checkout for branches using git branch command
* Master - points to the latest commit
* Branch allows us for parallel development in the same repo

* Now let's create a local repo and (git init) into it

![Alt text](shots/25.JPG)

* Make some changes having folders and files

![Alt text](shots/26.JPG)

* Add and Commit the changes

![Alt text](shots/27.JPG)

* Making another change and commit

![Alt text](shots/28.JPG)

* Here the head and master both pointing to the same commit(latest commit)
* Now we create a branch R-1(First release) where the head points to the branch 

![Alt text](shots/29.JPG)

* Here after moving into the branch using checkout command , now both he master and the head points to the branch

![Alt text](shots/30.JPG)

* Now when we add a change in the branch and commit it, head points to the branch or latest commit made

![Alt text](shots/31.JPG)

*Now we got to master and check the history

![Alt text](shots/32.JPG)

* Now let's make changes to the master
* To update only the modified files we use, (git add -u) command
* Now both head and master points to this latest commit

![Alt text](shots/33.JPG)

* To have changes from one branch to another,we need to work with
    1. Merge - Three-way merge
             - no fast forward merge
    2. Rebase
    3. Cherry pick   

* The above processes may also lead to some conflicts (Merge conflicts)

## Git Merging
* create a new folder (branches_demo) and make it a local repo
* Make the changes,add and commit

![Alt text](shots/34.JPG)

* Now let's change the branch name from master to main

![Alt text](shots/35.JPG)

* create a commit on main

![Alt text](shots/36.JPG)

![Alt text](shots/37.JPG)

* Let's create a branch sprint from the main branch
  (git checkout -b sprint)
          or
  (git branch sprint, git checkout sprint)
* Here the sprint also points to the same commit such as main

  ![Alt text](shots/38.JPG)  

* we make a change in the sprint and also create a file
* To only add modified files ignoring the new created files, we use (git add -u)

![Alt text](shots/39.JPG)

## FAST FORWARD MERGE

* Now the current state of the branches is

![Alt text](shots/40.JPG)

Before Merge the picture

![Alt text](shots/42.JPG)

* To obtain all the changes from the sprint branch to the main, we need to merge and to achieve that we need to be present in the target branch(i.e, main)
* This is called the FAST-FORWARD merge
* Here the merge happens as the main combines with the latest commit(i.e, sprint)

After Merge the picture

![Alt text](shots/43.JPG)

Command Section

![Alt text](shots/41.JPG)

## THREE WAY MERGE

* Now make changes and commit to main branch

![Alt text](shots/44.JPG)

* Here we have added msg to src/main.py, added only the modified file and commited
* So we have 3 commit's now

![Alt text](shots/45.JPG)

* Current state

![Alt text](shots/46.JPG)

* Now we have different msg in both the src files of main branch and sprint branch
* Now while we merge there arises a conflict as to which to be stored, but for the test file there is only 1 msg stored (no conflict)
* This is to be resolved by the developer as to choose the display

![Alt text](shots/47.JPG)

* Now the new commit has to be made with a main commit and a sprint commit
* Three commit's being involved (3 way merge)

![Alt text](shots/48.JPG)

* To resolve this conflict, we use notepad editor along with git generated lines as

![Alt text](shots/49.JPG)

* Now make the changes and save the file as

![Alt text](shots/50.JPG)

* And the command line follows as

![Alt text](shots/51.JPG)

* Here the merge commit has two parents and also the graph (git log --graph --all)represented as

![Alt text](shots/52.JPG)

![Alt text](shots/53.JPG)

## EXERCISE

![Alt text](shots/54.JPG)

## SOLUTION

![Alt text](shots/55.JPG)

![Alt text](shots/56.JPG)

* branches created

![Alt text](shots/57.JPG)

![Alt text](shots/58.JPG)

* commit a change in sprint_poc

![Alt text](shots/59.JPG)

![Alt text](shots/60.JPG)

* commit a change in sprint_dev

![Alt text](shots/61.JPG)

![Alt text](shots/62.JPG)

* Merging sprint_poc into sprint_dev

![Alt text](shots/63.JPG)

![Alt text](shots/64.JPG)

* We look at all the senerio using graph representation using (git log --graph --oneline --all)command

![Alt text](shots/65.JPG)

![Alt text](shots/66.JPG)

## Git Rebase

* Create a scenerio as follows

![Alt text](shots/67.JPG)

![Alt text](shots/68.JPG)

* Rebase is a command used to get changes from one branch to other by rewriting history
* Make two changes and commit them in the main branch
* To directly add and commit at same time we use (git commit -am "message") command

![Alt text](shots/69.JPG)

![Alt text](shots/70.JPG)

![Alt text](shots/71.JPG)

* Now the chnages in the main branch to be merged into sprint branch, we have two ways to do this

1. Three way merge as follows (confusing approach)

![Alt text](shots/72.JPG)

2. Rebase as follows (cleaner approach)

* Rebase is useful for all the child branches but never rebase main/master from child as rebase rewrites history.
* To rebase we checkout sprint and rebase to main using (git rebase main) command

![Alt text](shots/73.JPG)

![Alt text](shots/74.JPG)

* Here arises a merge conflict, with the src/main.py
* we open the file in notepad, edit with changes and now rebase again using (git rebase --continue) command

![Alt text](shots/75.JPG)

![Alt text](shots/76.JPG)

![Alt text](shots/77.JPG)

* Now after the rebase the commit id of the sprint branch gets changed as the parent get's changed and also shows that it is replaced after the main branch

![Alt text](shots/78.JPG)

* This is nothing but the rewriting of the history

## Git Cherry pick

* If we need to pick specific commits or specific range of commits (sequence) of commits , cherry pick can be used
* Firstly, we add two commits

![Alt text](shots/79.JPG)

![Alt text](shots/80.JPG)

* Performing changes from any commit to any branch
* Now consider the above, we want changes from commit (commit id - 97bb278) into main branch
* So we use cherry pick
 * first checkout the target/destination
 * use cherry-pick(git cherry-pick 97bb278)command

![Alt text](shots/81.JPG)

## Remote Repository

* Git Remote Repository is any folder on any server
* To make Git Remote accessible, generally two protocols are widely used
   1. http(s)
   2. ssh
* There are many popular Git Repositories which are available for free.
* lets get started with GitHub
* Create a new repository in GitHub








 

  


 

 