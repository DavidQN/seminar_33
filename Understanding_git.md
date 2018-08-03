# Learning Git

##### IMPORTANT: Any `shell` commands you are not familiar with in this README.md please check this [site](https://explainshell.com/)

## Understanding Git

First let us initialize a repository, what this does is create our local repository in our current directory. Every new thing we create now in this folder is associated with the local repository we just created. Remember that git only tracks files as long as it is within a repo.

create a .txt file and in the file let us create a line that just says

```
Important change
```

If we do a git status we will notice that there is current an untracked change. This file is currently in something called the workspace. This is where we are most of the time as we update our files.

When we feel we have made some meaningful change we put our code in something called the staging area also referred to as the INDEX. What the staging area does is a state of your working tree, such that the subsequent git commit takes that frozen state and uses it as the point of contact.

Git commit takes your frozen tree in the staging area and builds a valid tree object, and commits that to our repo. We can view such commits by writing `git log`, this states the commits with whatever message was associated with it during creation.

Now, let us add this file to our staging area

```
git add fileone.txt
```

If we try git status we will notice that our changes are colored green with a small text on top stating “Changes to be committed:”.

Well perhaps I didn’t want these changes to be added to my staging area, to remove it what I could do is run

```
git rm --cached fileone.txt
```

So what that does is remove it from the staging area. If we run `git status` we will notice that the file is labeled `untracked`. So let us re-add this to our staging area.

```
git add .
```

`git add .` adds all changed files from the current PATH onward, so if we created a file in our current directory called filetwo.txt and a folder called somenew and within that folder we create a file called filethree.txt

```
touch filetwo.txt
mkdir somenew
cd somenew
touch filethree.txt
cd ..
```

So if you run

```
tree
```

you should get:

<img width="287" alt="screen shot 2018-08-02 at 12 45 51 pm" src="https://user-images.githubusercontent.com/23644019/43599035-46bd40a0-9654-11e8-8697-6cb9001a183b.png">

Now let us delete the folder `somenew`

```
rm -rf somenew
```

Let us run a `git status`, we should see a bunch of untracked/deleted files so to add all changes to our repo (both deleted and created)

```
git add -A
```

This should clear all those untracked changes.

---
