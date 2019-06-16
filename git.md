# Learning Git #

## Quick start ##

First, you need to install git.

On Ubuntu, simply do

```
sudo apt-get install git
```

For other systems, I invite you to look for the instructions yourself, then check that you have git correctly installed by typing in a terminal:

```
git --version
```

Now, let's create a directory

```
mkdir myproject
cd myproject
```

Then, inside this empty directory, type

```
git init
```

Cool, you should have a .git folder in there.

Next thing is to set up user and email. Do this, and change it if you'd like to:

```
git config --local user.name User
git config --local user.email user@localhost
```

Now, you should be able to see those settings in .git/config

```
cat .git/config
```

You can also use the `--global` option to set the value globally, but it can leads to trouble when working on different repositories if you require different information for some of them.

Now, to see all the current settings, do
```
git config --list --show-origin
```

And to see that git correctly finds your user name, do
```
git config user.name
```

## Adding files ##

Let's create a file.

```
echo "Hello World" >helloworld.txt
```

Check that the new file is not tracked.

```
git status
```

Add the file to staging. I.e. tell git to track it.

```
git add helloworld.txt
```

Check that the file will be committed.

```
git status
```

And commit.

```
git commit -m "Been introduced to world"
```

Now, check that everything is clean.

```
git status
```

And check that the commit is been performed.

```
git log -1
```

See details about the files which have been changed.

```
git log --stat -1
```

And about the actual content

```
git log -c -1
```

Now share you're changes with the world.

```
git push
```

Oops. Says it needs something about remotes. That's normal, we have to tell git where to push to, it will not guess by itself. We'll do that later.

So far, we have a fully functional git repository, except for the remote part.

## Deleting a file ##

Git as a simple command to delete files.

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
git add .
```

## Modifying between add and commit ##

What happen if we modify a file after adding it?

Let's modify the file first. Do whatever you want here, but change something.
```
vim helloworld.txt
```

Now add.
```
git add helloworld.txt
```

Now modify again.
```
vim helloworld.txt
```

And now, look at the state of things.
```
git status
```

You should see the file appear twice.

With the condensed view, you get twice the `M`.

```
git status -s
```

What actually happens here is that git actually copies files to staging when tracking them. So new changes are different from staging. Usually, you just want to add again, but sometimes, you may wonder if the new changes are actually errors.

**Diffing**

To compare the staged version to the original version, do this:
```
git diff --staged helloworld.txt
```

To compare the staged version to the version in the working directory, do this:
```
git diff helloworld.txt
```

If you want to compare the version in the working directory to the last commit, do this:
```
git diff HEAD hello.txt
```

## Ignoring files ##

Often, I work on a lot of files.
Then I add them to staging.
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

## Removing a file with changes in staging

Let's modify our file, and add it to staging.
```
echo "Nice to meet you" >>helloworld.txt
git add helloworld.txt
```

Now let's attempt to remove it.
```
git rm helloworld.txt
```

Git notices that the file is already in staging, and denies the remove request.
This is to avoid losing staged changes by mistake, which would become unrecoverable.
To actually do it, use
```
git rm -f helloworld.txt
```

## Recovering changes from staging

Let's assumed we did not performed the last command in the previous section.

And add a third line to the file.
```
echo "I'm John" >>helloworld.txt
```

Now, let's say we're not happy about those changes, and we want to get back the version that we added but did not commit yet.

That's actually easy, just do
```
git checkout helloworld.txt
```

It will get the version that was staged.








