# Git 06 - Removing a file with changes in staging #

What follows assumes you have a file named `helloworld.txt` at the root of your git repository.

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