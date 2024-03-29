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

## Git Workflow

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
 
 ### Creating a senerio

 * First commit - create folder understanding with src, test folders
 * Second commit - Add files to src, test folders (main.py, each)
 * Third commit - Add any content into the files
 * Find logs for the above commits :

![Alt text](shots/112.PNG)

![Alt text](shots/13.JPG)

![Alt text](shots/14.JPG)
 
### Plumbing Commands

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

## Git Branching

* Branch in git always points to a latest commit id
* We checkout for branches using `git branch` command
* `Master` branch - points to the latest commit
* Branch allows us for parallel development in the same repo

* Now let's create a local repo and `git init` into it

![Alt text](shots/25.JPG)

* Make some changes having folders and files

![Alt text](shots/26.JPG)

* Add and Commit the changes

![Alt text](shots/27.JPG)

* Making another change and commit

![Alt text](shots/28.JPG)

![Alt text](shots/114.PNG)

* Here the head and master both pointing to the same commit (latest commit)
* Now we create a branch `R-1` (First release) where the head points to the branch 

![Alt text](shots/29.JPG)

![Alt text](shots/115.PNG)

* Here after moving into the branch using `git checkout` command , now both the master and head points to the same branch

![Alt text](shots/30.JPG)

![Alt text](shots/116.PNG)

* Now when we add a change in the branch and commit it, head points to the branch or latest commit made

![Alt text](shots/31.JPG)

![Alt text](shots/117.PNG)

* Now we get to master and check the history

![Alt text](shots/32.JPG)

![Alt text](shots/118.PNG)

* Now let's make changes to the master
* To update only the modified files we use, `git add -u` command
* Now both head and master points to the latest commit

![Alt text](shots/33.JPG)

![Alt text](shots/119.PNG)

* To have changes from one branch to another, we need to work with `Merging techniques`

    1. Merge 
        * Three-way merge
        * no fast-forward merge
    2. Rebase
    3. Cherry pick   

* The above processes may also lead to some conflicts `Merge conflicts`

#### git branching strategy

[Refer here : https://nvie.com/posts/a-successful-git-branching-model/ ]

## Git Merging

* Create a new folder `branches_demo` and make it a local repo
* Make the changes, `add` and `commit`

![Alt text](shots/34.JPG)

* Now let's change the branch name from _**master to main**_

![Alt text](shots/35.JPG)

* Create a `commit` on main

![Alt text](shots/36.JPG)

![Alt text](shots/37.JPG)

* Let's create a branch `sprint` from the main branch
  `git checkout -b sprint`

          or

  `git branch sprint` , `git checkout sprint`
* Here the `sprint` also points to the same commit such as main

  ![Alt text](shots/38.JPG)  

* we make a change in the sprint and also create a file
* To only add modified files ignoring the new created files, we use `git add -u`

![Alt text](shots/39.JPG)

### FAST FORWARD MERGE

* Now the current state of the branches is

![Alt text](shots/40.JPG)

* Before Merge 

![Alt text](shots/120.PNG)

* To obtain all the changes from the `sprint` branch to the `main`
* The merge command is `git merge <source-branch>` i.e. you should be in `target branch` (i.e, main)
* This is called the _**FAST-FORWARD merge**_
* Here the merge happens as the main combines with the latest commit (i.e, sprint)

* After Merge 

![Alt text](shots/121.PNG)

* Command Section

![Alt text](shots/41.JPG)

### THREE WAY MERGE

* Now make changes and commit to main branch

![Alt text](shots/122.PNG)

* Here we have added `msg` to `src/main.py`, added only the modified file and commited
* So we have 3 commit's now

![Alt text](shots/45.JPG)

* Current state

![Alt text](shots/46.JPG)

* Now we have different msg in both the src files of main branch and sprint branch
* Now while we merge there arises a conflict as to which to be stored, but for the test file there is only 1 msg stored (no conflict)
* This is to be resolved by the developer as to choose the display

![Alt text](shots/47.JPG)

* Now the new commit has to be made with a main commit and a sprint commit
* Three commit's being involved : `Three way merge`

![Alt text](shots/123.PNG)

* To resolve this conflict, we use notepad editor along with git generated lines 

![Alt text](shots/49.JPG)

* Now make the changes and save the file 

![Alt text](shots/50.JPG)

* And the command line follows 

![Alt text](shots/51.JPG)

* Here the `merge commit` has two parents and also the graph `git log --graph --all` represented as

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

* We look at all the scenerio using graph representation using `git log --graph --oneline --all` command

![Alt text](shots/65.JPG)

![Alt text](shots/66.JPG)

## Git Rebase

* Create a scenerio as follows

![Alt text](shots/67.JPG)

![Alt text](shots/120.PNG)

* Rebase is a command used to get changes from `one branch to other` by _**rewriting history**_
* Make two changes and commit them in the main branch
* To directly add and commit at same time we use `git commit -am "message"` command

![Alt text](shots/69.JPG)

![Alt text](shots/70.JPG)

![Alt text](shots/71.JPG)

* Now the chnages in the main branch to be merged into sprint branch, we have two ways :

1. Three way merge (confusing approach)

![Alt text](shots/72.JPG)

2. Rebase (cleaner approach)

* Rebase is useful for all the child branches but _**never rebase main/master from child**_ as rebase rewrites history.
* To rebase we checkout sprint and rebase to main using `git rebase main` command

![Alt text](shots/73.JPG)

![Alt text](shots/74.JPG)

* Here arises a merge conflict, with the src/main.py
* we open the file in notepad, edit with changes and now rebase again using `git rebase --continue` command

![Alt text](shots/75.JPG)

![Alt text](shots/76.JPG)

![Alt text](shots/77.JPG)

* Now after the rebase the commit id of the sprint branch gets changed as the parent get's changed and also shows that it is replaced after the main branch

![Alt text](shots/78.JPG)

* This is nothing but the _**rewriting of the history**_

## Git Cherry pick

* If we need to pick specific commits or specific range (sequence) of commits , cherry pick can be used
* Firstly, we add two commits

![Alt text](shots/79.JPG)

![Alt text](shots/80.JPG)

* Performing changes from any commit to any branch
* Now consider the above, we want changes from commit (commit id - 97bb278) into main branch
* So we use cherry pick `git cherry-pick <commit-ID>`
 * first checkout the target/destination
 * use cherry-pick `git cherry-pick 97bb278` command

![Alt text](shots/81.JPG)

## Remote Repository

* Git Remote Repository is a folder on any server
* To make `Git Remote`` accessible, generally two protocols are widely used :
   * http(s)
   * ssh
* Today let's get started with GitHub
  * Create an account in GitHub 
   
  [Refer Here : https://github.com/ ]

* Create a new repository in GitHub

![Alt text](shots/124.PNG)

![Alt text](shots/125.PNG)

![Alt text](shots/126.PNG)

* Now add this repository as `remote` to your `local repository`

![Alt text](shots/127.PNG)

* Now let's push the changes from local to remote : `git push <remote-name> <branch/tag name>`

![Alt text](shots/128.PNG)

![Alt text](shots/129.PNG)

* Now let's see all the branches in the repo

![Alt text](shots/130.PNG)

* The branches in `remote` represent `remote branches`
* Now let's push the sprint branch as well

![Alt text](shots/131.PNG)

* In Organizations we will already have some repositories, Now to get the changes from remote to local we perform clone. Let's `git clone https://github.com/spring-projects/spring-petclinic.git`

![Alt text](shots/132.PNG)

![Alt text](shots/133.PNG)

* Summary

![Alt text](shots/134.PNG)

### Multi User Git Scenarios

* Create a Git Repo in `GitHub`
* GitHub and many repositories use _**md**_ (markdown) as a default document format
* Simulate two users (RRR) :
   * Ram
   * Bheem
* Create local config's for username and emails

![Alt text](shots/135.PNG)

![Alt text](shots/136.PNG)

* Create a commit on each of thier machines

![Alt text](shots/137.PNG)

![Alt text](shots/138.PNG)

* Current status

![Alt text](shots/139.PNG)

* Let ram push the changes

![Alt text](shots/140.PNG)

* Current status

![Alt text](shots/141.PNG)

* Let Bheem push the changes

![Alt text](shots/142.PNG)

* This failed as bheems origin doesnot represent latest changes in Remote.
* Bheem now executes `git pull` which will fetch the changes from remote and merge the changes. In this situation due to merge an extra commit is created

![Alt text](shots/143.PNG)

* Now bheem pushes the changes to remote repo

![Alt text](shots/144.PNG)

* Current status

![Alt text](shots/145.PNG)

* Now let RAM does one commit

![Alt text](shots/146.PNG)

* RAM when pushes will fail, so ram decides to pull using rebase

![Alt text](shots/147.PNG)

* Now push the changes

![Alt text](shots/148.PNG)

### Git Authentication Methods

* Git has two popular authentication methods :
    * username and password/token
    * ssh key-pair
* Creating a PAT for GitHub 
  
  [Refer Here : https://docs.github.com/en/enterprise-server@3.4/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens ]
* Use ssh-keygen to generate `id_rsa` and `id_rsa.pub` files in `<HOME-DIR>/.ssh`
* copy the `id_rsa.pub` in 
=> GitHub => Settings => SSH and GPG keys => New SSH Key

### Git Remote and Branches

* The command to push `git push <remote-name> <branch-name>`

#### Upstream branches

* In Git while pushing the code if we observe the following errors :

![Alt text](shots/149.PNG)

![Alt text](shots/150.PNG)

* By setting the upstream branch we are setting the default remote

### Making changes in Local commits

* We have the latest commit in which there is `typo` in commit message which we want to correct

![Alt text](shots/151.PNG)

![Alt text](shots/152.PNG)

* Now let's delete this extra commit and then fix typo
* Clone the code from 

[Refer Here : https://github.com/GitPracticeRepo/Rework ]

* `git commit --amend` can be used to reword the latest commit not previous
* _**edit**_ : make the changes in commit
* _**reword**_ : change the commit message
* _**squash**_ : combine commits

* Exercise: 

[Refer Here : https://gitexercises.fracz.com/ ]

### Git Repository Types

* _**Bare Repository**_: This repository will have only `.git` folder `no working tree` This is used generally on server sides on git remotes
* _**Mirror Repostiory**_ : This repository also will have only `.git` folder and used to cater to other users
* _**Normal Repository**_ : Here we get working tree as well as `.git` and is used for development

### Other topics

* Force push `git push --force`, this command pushes the changes to git remote and overrides the remote repo history.
* Git maintains two logs in your local repo :
   * _**log**_
   * _**ref log**_ : maintains the history of all `changes done into local`

![Alt text](shots/153.PNG)

* Try `git log` examples and `git diff` examples
 

  


 

 