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
 
  add Remote Repository:
  git remote add origin https://github.com/vickywang0102/git_test.git

  use Proxy for Git:
  git config http.proxy http://10.50.20.69:3128
  
  remember username and password:
  git config --global credential.helper store
  
  remove Remote repository:
  git remote remove origin  
          
          
                                 