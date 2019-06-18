# Git 04 - Modifying between add and commit, and viewing differences #

What follows assumes you have a file named `helloworld.txt` at the root of your git repository.

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

You should see that the file appears twice.

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
