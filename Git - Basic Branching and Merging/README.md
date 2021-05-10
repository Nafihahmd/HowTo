# Git Branching 
This guide gives you a brief on working with **remote** branches.  

## Objective
Suppose you are working with a large project and want to test adding a new feature to it. It is always advicable to add your new unstable code to a side branch and not to the source code. That is where branching becomes handy. So this tutorial includes:
- Creating local branches
- Creating Remote branches
- Pushing changes in local branch to remote branch
- Merging local and remote branches
- Removing local and remote branches

## Procedure
1. Create local branch for new feature. Use a relevant branch name, eg., "new-feature"
```
git branch new-feature
```

2. Create remote branch for new feature. 
```
git push origin new-feature
```

3. Editing in the new branch  
	First change from mater branch to the newly created branch using `checkout` command.

```
git checkout new-feature
```
	Afetr adding/editing your required files stage and commit the changes.
```
git add *	#Staging changes 
git status
git commit -m "<describe change here>"
 ```
 	Finally push it to remote branch
 ```
 git push origin new-feature
 ```

 4. Merging branch
Change to master branch first. 
```
git checkout master
git merge new-feature 
git push origin master	#merging remote branch
```
5. Removing branch
This step assumes you have remote-tracking branches. Otherwise this this procedure will not work for remote branches. If you have followed the tutorial from step 1 just ignore above two sentences.
```
git branch -d new-feature	#remove local branch
git push origin -d new-feature	#remove remote branch
```