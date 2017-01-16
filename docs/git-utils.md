#Git Utils

I always forget certain git commands so this is a compilation of those. 

## Delete local and remote branch

```
git push origin --delete <branch_name>
git branch -d <branch_name>
```

## Git aliases

### Create branch
This git alias creates a new branch and publishes to origin

```newBranch = !git checkout -b $1 && git push -u origin```

Use it like `git newBranch myBranch` This will create a branch called `myBranch` and will be pushed to origin (so the remote branch will be created too)

### Delete branch

`delBranch = !git push origin --delete $1 && git branch -d`