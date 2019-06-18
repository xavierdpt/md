# Git 01 - Quick start #

This is a git quickstart, in which you will be walked through initializing a new local git repository.

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

You should have a .git folder in there.

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
