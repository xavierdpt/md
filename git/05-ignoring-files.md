# Git 05 - Ignoring files #

Often, I work on a lot of files.
Then I add them all to staging.
And then I see that some of those should be ignored.

So, here's a procedure for that.

Let's create and add a new file.
```
touch newfile ; git add newfile
```

And let's add it to the ignored files.
```
echo newfile >>.gitignore
git add .gitignore
```

Now the .gitignore file is in staging, but we still need to remove the new file from staging, because git only checks the .gitignore file which is in the working directory.

```
git rm --cached newfile
```