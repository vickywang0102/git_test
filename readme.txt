# this is my first file

1. Init Git reporsitory, use 'git init' command.

2. add to Git reporsitory, two steps:
  git add <file> Noted: can repeat this command and add multiple files.
  git commit, complete.
  git commit -m "comments"

3. update Readme.txt.
  git status. can check the status of the reporsitory and check which files are updated.
  git diff. can check the changes with previous version.


4. Roll back version.

  roll back to previous version:     git reset --hard HEAD^
  roll back to previous two version: git reset --hard HEAD^^
  roll back to specify version:      git reset --hard <commit-id> 
  check the check-in log:            git log
  record your command whihc you had implemented: git reflog

  check the version which the HEAD pointer point to:  git reset --hard 

5. Working director and Reporsitory
  add file to stage:      git add
  commit file to branch:  git commit

6. Management the changes.
  each change should be added before being committed.
  first modify -> git add -> second modify -> commit -> result<the second modify will not be committed>
  first modify -> git add -> second modify -> git add -> commit -> result <all changes should be committed>

6. Revert your changes.
  1)discard the changes in Work directory:       
    git checkout -- filename
  2)discard the changes already added in Stage:  
    git reset HEAD filename  -> revert the change in stage to work directory.
    git checkout -- filename
  3)discard the changes already commit to Reporsitory.
    git reset --hard HEAD^
    
7. Remove files.
  git rm
  git commit -m ""
  
  Work dir                Stage               Repository
             -> add ->           -> commit->
        <-reset &checkout        <- reset <-

===================================================
8 Remote Repository
http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001374385852170d9c7adf13c30429b9660d0eb689dd43a000
  1)create SSH Key:
    ssh-keygen -t rsa -C "youremail@example.com"
  2)login GitHub. open Account settings -> click SSH key  -> add SSH Key
 
  3)add Remote Repository:
  git remote add origin https://github.com/vickywang0102/git_test.git

  4)use Proxy for Git:
  git config http.proxy http://10.50.20.69:3128
  
  5)push your locoal file to remote repository
  git push -u origin master
  
  6)remember username and password:
  git config --global credential.helper store
  
  7)remove Remote repository:
  git remote remove origin  
          
9 clone a local repository from remote repository 
  git clone   -> default branch is master branch      


=======================================================
10 create&delete branch:
  
  main branch: master(pointer)
  dev branch:  devt (pointer)
  
  check branch: git branch
  
  1) createa and change to devt branch:
     git checkout -b devt   or (git branch devt && git checkout devt)
     commit your change to devt branch.
  2) merger devt branch back to master branch.
     git checkout master
     git merge devt
  3) delete devt branch
     git branch -d devt
  4) resoved conflict and commit the fixes.
  
  5) Bug branch
     git stash. save the current working dir. then can go to another branch and fix some urgent bugs.
     git stash apply/git stash drop/git stash pop/git stash list
     git stash apply stash@{0} -> restore the specify version
  6) Feature Branch.
     create a new featrue branch for each new feature.
  7) Co-operative multiplayer
     now we need remote repository.
     1)git remote or git remote -v
     2)git push origin master or git push origin <dev branch name>
     3)git pull. if you push failed and the remote version is advanced to your local version.
     4)Non-master branch. need to create link between your local and remote repository.
        git checkout -b branch-name origin/branch-name
        git branch --set-upstream branch-name origin/branch-name
     5)Create Remote dev branch of Origin to local working dir: 
        git checkout -b dev origin/dev    
        git branch --set-upstream branch-name origin/branch-name
        
     6) if the dev branch name is diff between your local and remote, you have to specify the branch name:
        git push remote <branch name>:<remote branch name>
        git push remote dev:dev_1
        
     Note: Master branch have to sync with remote repository since it's main branch.
           devt branch also need to be sync'd with remote repository since all developer work on this branch.
           

11. TAG
    1) create tag
        git tag -a tagname -m "description" commitID
    2) check tag info
        git show tagname
    3) push tag to remote
        git push origin tagname
        git push origin --tags (push all tags to remote)
    4) delete tag
        git tag -d version1.0    
        1)if the tag already pushed to remote repository.
        git tag -d version1.0
        git push origin :refs/tags/version1.0   



                      