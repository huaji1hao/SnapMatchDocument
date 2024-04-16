# Team 17

### How To Develop At Home

##### Issue Workflow

1. Let's say there is a bug or problem in the code or one of your JUnit tests; 
instead of adding a feature (as described below), you follow a very similar 
process with some slight differences
2. Firstly, navigate to the issues tab on the left-hand side of the git page
and create a new issue
3. Name the issue accordingly and give it a brief description, e.g. 
**Title: *Compile Errors***, **Desc: *File.java has symbol compile errors***
4. Assign the issue to yourself, and choose the most appropriate milestone. You
should also assign it a relevant label if possible for readability
5. When the issue is created, it will be given an ID that you can see underneath
the name in the *Issues -> Lists* tab with **#** before it
6. Follow the exact same steps as described in the Git Workflow below by creating
a new branch etc., except this time, you ***must*** give the branch a specific name
7. Name the branch ***\<id>**-issue-description* where ***\<id>*** is replaced by 
the ID of the issue you created, and ***issue-description*** is the title of the issue you created;
in this case it would be *\<id>-Compile-Errors*
8. Follow the same workflow as normal, committing and pushing to the branch you just 
created
9. When the issue is resolved, and all changes are pushed to the branch you created, create
a merge request for your branch into *dev*
10. The description of the merge branch should be *Closes #\<id>* where \<id> is the ID of the issue
you created
11. Remember to check *delete source branch* so that your issue branch is removed from the repo
12. The issue should now be automatically closed, but it may not be, so check in the issues tab
and manually close the issue if it is still there
13. If everything was done right, you should see the related branch you created and all the commits
in the issue (that you created)'s page
14. The purpose of all of this is to link issues to commits and changes to easily track things
    ***(+ we get marked on our usage of issues)***

##### Git Workflow

1. Type `git branch` to check what branch you are currently in
2. Make sure you are in the *main* branch by typing `git branch`
   1. **IMPORTANT:** If you are not in the *main* branch, type `git checkout main`
      1. If you type `git branch` and there is no local dev branch, you must type `git branch -r` to get a list of all remote repositories
      2. You should see a remote branch called *remotes/origin/main* in red
      3. Type `git checkout -t *remotes/origin/main*` 
   2. Type `git branch` again to confirm you are now in the *main* branch
3. Let's say you have two completely separate features you are working on, **feature 1** *(Anything remotely related should be grouped as the same feature*)
4. Create a new branch for each feature with this naming format: `git switch -c name/feature1 `. This should create the branch while also placing you in it.
   1. If you are not in the *name/feature1* branch, type `git switch name/feature1`
   2. Type `git branch` again to confirm you are now in the *name/feature1* branch
5. Now work on it as you normally would, by committing and pushing the changes you make.
   1. Let's say you add some stuff to **feature 1**: `git commit -am "added some stuff to feature 1"` then `git push`
   2. Then you finish **feature 1**:` git commit -am "finished feature 1"` then `git push`
6. Finally, you want to merge the **feature 1** branch into main and avoid any conflicts; the best way to do this is on the website:
   1. Navigate to *Merge Requests* on the left navigation menu.
   2. Press *New merge request.*
   3. Select the branch you would like to merge as the *Source branch*, for example, **the feature 1** branch, *name/feature1.*
   4. **IMPORTANT:** Make sure you set the *Target branch* to *main.*
   5. Press *Compare branches and continue.*
   6. Optional: Add a description that describes the goal of the changes and what any reviewers should be made aware of.
   7. Assign the merge request to yourself.
   8. When merging code, you should *always* set the reviewer to another member of the team!
   9. Select the corresponding feature/issue milestone and labels
   10. Press *Create merge request*
   11. Navigate to the *merge requests* tab and go to your newly created request. Make sure that *Delete source branch* is ticked!
   12. Once it has been reviewed and approved, and you are sure there are no conflicts, press *Merge* on the merge request
7. Finally, delete the **feature 1** branche locally *(they should be deleted remotely already if you did step 9.11)* by typing `git branch -d name/feature1` 
    1. If you get an error trying to locally delete the branch, it is probably because you are still in it. Type `git switch main` and `git branch` to make sure you are not in the branch you are trying to delete, then repeat step 11!
8. **DONE!**

## Project Contributors

- Desange Nkumu
- Kian Surani
- Junfeng ZHU
- Mari Thorpe
- Yongkang WANG
- Ellie McCartney
- Shuli WANG
- Adwoa Kumi-Addo