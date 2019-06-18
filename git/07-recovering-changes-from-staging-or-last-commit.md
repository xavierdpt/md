# Git 07 - Recovering changes from staging or last commit

What follows assumes you have a file named `helloworld.txt` at the root of your git repository.

Let's modify our file, and add it to staging.
```
echo "Nice to meet you" >>helloworld.txt
git add helloworld.txt
```

And add a third line to the file.
```
echo "I'm John" >>helloworld.txt
```

Now, let's say we're not happy about those changes, and we want to get back the version that we staged but did not commit yet.

That's actually easy, just do
```
git checkout helloworld.txt
```

To get back the version from the last commit instead, do
```
git checkout HEAD helloworld.txt
```







