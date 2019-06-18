# Git 03 - Deleting a file #

What follows assumes you have a file named `helloworld.txt` at the root of your git repository.

Git has a simple command to delete files.

```
git rm helloworld.txt
git status
git ls
```

We see that the file removal will be committed and the file is not more in the working directory.

**Recovering**

So now, you're happy about your big commit and all, but you want to recover that file. Here's how to do it:
```
git checkout HEAD helloworld.txt
git status
```

Now, the file is here again, and also the deletion has been forgotten in the commit log.

## Two phase delete ##

Usually, you remove files like this.
```
rm helloworld.txt
```

Then, the removal is not tracked by git. To let git know about it is the same as the previous section.
```
git rm helloworld.txt
```

Only now, you cannot use the shell's completion mechanism because the file is gone.

Most of the time, we change a lot of files anyway, and we want to commit all the changes. And the files we do not want to commit are safely taken care of by `.gitignore`. So here's the usual way of doing it, simple track all the changes in the current directory.
```
git add -A .
```
