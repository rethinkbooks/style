My previous company did this Git workflow, so it's how I've always done it. It works well for me but I'm open to any improvements.

1) Create a new branch off dev branch, name it something like jn-feature-branch.  
    `git checkout dev`  
    `git checkout -b jn-feature-branch`  
    
2) Work on your branch and only commit to your branch.  

3) When you are done with your feature, checkout the dev branch and pull the latest.  
    `git checkout dev`  
    `git pull origin dev`  
    
4) Go back to your feature branch, and rebase dev with interactive mode.  
    `git checkout jn-feature-branch`  
    `git rebase -i dev`  
    
5) You will be taken into an interactive screen. I like to squash my commits into a single commit, but it's probably ok if you don't want to squash them. However, squashing makes it very easy to revert later on if something goes badly because everything is in a single commit. [http://gitready.com/advanced/2009/02/10/squashing-commits-with-rebase.html](http://gitready.com/advanced/2009/02/10/squashing-commits-with-rebase.html).  
  - If you have conflicts, you can fix them individually and then continue with the rebase.  
     `git rebase --continue`  
  - If you screwed things up while fixing conflicts, you can abort the rebase.  
     `git rebase --abort`   

6) When you are done rebasing, you can rebase your branch back into dev.  
   `git checkout dev`  
   `git rebase jn-feature-branch`  
   
7) Push that bad boy  
   `git push origin dev`  