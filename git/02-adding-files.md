# Git 02 - Adding files #

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

Check that the file is now tracked and ready to be committed.

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

And check that the commit has been performed.

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

Oops. Says it needs something about remotes. That's normal, we have to tell git where to push to, it will not guess it by itself. We'll do that later.

So far, we have a fully functional git repository, except for the remote part.
