# Git Branching

## Learning Objectives
- Explain what a branch is in git
- Create, merge, and delete branches on local and remote repositories
- Describe how branching and merging allows for collaboration during development
- Describe Github Workflow using issues, branches, and pull-requests
- Resolve a merge conflict



## Review (10 min, 0:10)

Quickly review the basics of git:

<details>
<summary>1. What is the purpose of git? How does it differ from GitHub?</summary>

> **Git** is a version control system allowing us to easily track files, manage changes and move between versions.
>
> **GitHub** is a web application that hosts remote repositories and allows developers to easily host and share code.

</details>



<details>
<summary>2. What command is used to start tracking a directory? What commands record the changes that occurred in the tracked directory?</summary>

> `$ git init` - create an empty Git repo
>
> `$ git add <file-path>` - stage file(s) for commit
>
> `$ git commit -m "message"` - commit staged files

</details>



<details>
<summary>3. What's the difference between a fork and a clone?</summary>

> A fork is when you copy a repository on GitHub to your own GitHub account.
>
> A clone is when you download a remote repository (likely from GitHub) to your local file system.

</details>



<details>
<summary>4. What commands are used to share changes (commits) between local and remote repos?</summary>

> `$ git remote add <remote_name> <remote_url>` - add a remote repo with a given name and url
>
> `$ git push <remote_name> <branch_name>` - update a remote repo with commits from a branch of a local repo
>
> `$ git pull <remote_name> <branch_name>` - update a local repo with commits from a branch of a remote repo

</details>



## Framing (0:05 / 0:15)

As we discussed before, Git is a very powerful version control and collaboration tool. We've learned about the ability to keep track of changes to our code using staging and committing, how to work with others using  forks and pull requests.


Git has a couple of other really powerful features that we'll discuss today.


Think about these questions:

- What if I'm working on a feature and I want to try something out? Will I be able to cleanly remove that work if I decide I don't want to keep it?
- What if I'm working on a team and everyone is working on their own feature? How will we keep our work separate until it is finished?
- What if I'm working together with some other developers on a feature? How will we keep our work separate until it is finished?



<details>

​	<summary>What is the answer?</summary>

​	Branching.

</details>


### Create a git repo
```
echo "Sweet beast yowling nonstop the whole night or lie on your belly and purr when you are asleep yet scratch at fleas, meow until belly rubs, hide behind curtain when vacuum cleaner is on scratch strangers and poo on owners food unwrap toilet paper. Ears back wide eyed pooping rainbow while flying in a toasted bread costume in space this human feeds me, i should be a god yet hide head under blanket so no one can see." >> text-sample.txt
```

```
git init
git add .
git commit
```

## How Git Branching Works (15 min, 0:30)

In Git, branches are a part of your everyday development process. When you want to add a new feature or fix a bug — no matter how big or how small — you should set up a new branch to encapsulate your changes. This makes sure that unstable code is never committed to the main code base and it gives you the chance to clean up your feature’s commit history before merging it into the main branch.

Branches are incredibly lightweight "movable pointers" that help us as developers make experimental changes! A branch in git is just a label or pointer to a particular commit in a repository, along with all of it's history (parent commits).

What makes a branch special in git, is that we're always *on* a specific branch, and when we commit, the current branch HEAD moves forward to the new commit.

**Terminology:** HEAD is simply a reference to the current commit. By default, this is the most recent commit.

![Git Branch Diagram](https://raw.githubusercontent.com/wdi-sg/gitbook-2019/master/images/branching.png)

> The diagram above visualizes a repository with multiple lines of development, one is the master branch, and the others are feature branches. By developing in branches, it’s not only possible to work on branches in parallel, but it also keeps the main master branch free from questionable code.


### Add a branch to my text
```
git branch new-story
git checkout new-story
git status
```

Edit the text. Make a new line and change some text.
```
git add -u
git commit
```

## Merging (10 min, 0:40)

Now imagine that we have completed our awesome feature on its own branch and we want to bring those changes back into `master`, we now need a way to consolidate these two versions of our code base. The easiest way to do this is by  **merging** the feature branch into the master branch.

Let's see what this process looks like visually:

![before-merge](https://raw.githubusercontent.com/wdi-sg/gitbook-2019/master/images/merging.png)

***Locally***, all we need to do is checkout (switch to) the master branch and then run the merge command to integrate our feature branch:

```
$ git checkout master
```

```
$ git merge new-story
```


Once merged, you can delete the branch:

```bash
$ git branch -d new-story
```
***Remotely***, we could easily merge our branch back into master through a Pull Request and delete the branch on GitHub.

**Note:** You merge another branch in to your current branch. So if I want to merge `some_feature_branch` branch in to `master`, I have to checkout `master` and run `git merge some_feature_branch`

### You Do: Branching Exercise (15 min, 0:55)
[https://github.com/wdi-sg/git-branching](https://github.com/wdi-sg/git-branching)
