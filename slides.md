---
title: Intermediate git workshop
theme: white_nb.css
---

### Intermediate git workshop

<img align="center" width="30%" src="https://www.uibk.ac.at/public-relations/grafik_design/images/logo/download/sublogos/institute-sublogos/atmospheric-and-cryospheric-sciences.png"/>

ARMU-DPs Workshop, 19.06.2018

[Fabien Maussion](http://fabienmaussion.info)


---

## How to use these slides

- ``<space>`` : go to the next slide
- ``<shift+space>``: go back
- ``<left right up down arrows>``: navigate through the presentation structure
- ``<esc>``: toggle overview mode

---

## Agenda

- Short revision: git setup, git basics
- Web hosting pros and cons: GitHub, GitLab, BitBucket
- Working with branches and remotes
- A typical "pull/merge request" cycle
- Handling merge conflicts
- Tags and DOIs with Zenodo
- (Continuous integration: testing with Travis, documentation with ReadTheDocs)

----

### Q: Anything else you'd like to talk about?

----

### Q: Who is using git in this room, and what for?

---

**The version control system**

![git](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e0/Git-logo.svg/200px-Git-logo.svg.png)

----

## First-time setup

```bash
$ git config --global user.name "John Doe"
$ git config --global user.email johndoe@example.com
```

----

# Semantics

----

## Semantics: snapshot

- picture of how your files look like at a point in time
- you decide when to make a snapshot
- you can *always* go back to old snapshots

----

![snapshots](https://git-scm.com/book/en/v2/images/snapshots.png)

----

## Semantics: commit

- the act of creating a snapshot (verb or noun: *"I commited code"*, *"He just made a new commit"* )
- a project is made up of a lot of commits

----

![gitlog](/img/git-log.png)

----

## A commit contains

1. information about changes to previous commits
2. a reference to the previous (parent) commit
3. a hash code name

----

## Semantics: repository

- a collection of all the files and their history
- contains a ``.git`` folder
- can live on a local machine or a remote server (GitHub, GitLab, BitBucket)

----

## Semantics: cloning

- copying an entire repository from a remote server to a local machine

----

## Semantics: pulling

- downloading commits that don't exist on your local machine from a remote directory

----

## Semantics: pushing

- adding your local changes to the remote repository

----

## Semantics: branch

- all commits live in some branch
- there can be many of them
- the main branch of a project is called **master branch**

----

## Semantics: fork

- a remote copy of a remote directory
- useful for: collaborative work, or for a fresh start (e.g. template websites)

----

## Semantics: hosting service

- where to store your remote repository
- [GitHub](https://github.com/): free for open repositories, most famous (by far),
  just aquired by Microsoft (?)
- [BitBucket](https://bitbucket.org/): free for private repositories, less famous
- [GitLab](https://about.gitlab.com/): open-source
  platform: UIBK has its own deployment (https://git.uibk.ac.at)


---

## Hosting service comparison

----

### BitBucket

<section style="text-align: left; font-size: 0.7em">


**Pros**:
- free for small teams and private repositories
- not GitHub

**Cons**:
- no continuous integration service (not for free)
- not GitHub

----

### GitLab

<section style="text-align: left; font-size: 0.7em">


**Pros**:
- web-hosted OR self-hosted
- open source
- different pricing plans
- integrated continuous integration
- growing fast!
- Gitlab Pages
- not GitHub

**Cons**:
- quite new
- not GitHub

----

### GitHub

<section style="text-align: left; font-size: 0.7em">

**Pros**:
- established and used by many (everybody?)
- plugins, bots, etc.
- social network: looks good on your CV

**Cons**:
- Microsoft?!?
- closed source

----

### Today's practicals

Use either UIBK's GitLab OR GitHub

(just pick one, we'll show both in class)

---

## Warm up: working with branches

----

```bash
$ cd /home/user/my_project
$ git init
> Create a new file and edit it
> add and make a first commit
> edit again and commit
$ git log
```

----

![gitsnap](https://git-scm.com/book/en/v2/images/commits-and-parents.png)

<div align="right">
<small> <small> Source: [git book](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell)</small></small>
</div>

----

```bash
$ git branch testing
```

![gitsnap](https://git-scm.com/book/en/v2/images/two-branches.png)

<div align="right">
<small> <small> Source: [git book](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell)</small></small>
</div>


----

```bash
$ git checkout testing
```

![gitsnap](https://git-scm.com/book/en/v2/images/head-to-testing.png)

<div align="right">
<small> <small> Source: [git book](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell)</small></small>
</div>

----

```bash
> create a NEW file, add and commit
$ git log
```

----

![gitsnap](https://git-scm.com/book/en/v2/images/advance-testing.png)

<div align="right">
<small> <small> Source: [git book](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell)</small></small>
</div>

----

```bash
$ git checkout master
```

![gitsnap](https://git-scm.com/book/en/v2/images/checkout-master.png)

<div align="right">
<small> <small> Source: [git book](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell)</small></small>
</div>

----

```bash
> edit the first file again and commit
$ git log
```

----

![gitsnap](https://git-scm.com/book/en/v2/images/advance-master.png)

<div align="right">
<small> <small> Source: [git book](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell)</small></small>
</div>

---

## Careful! Let's merge

```bash
$ git merge testing
```

----

![gitsnap](https://git-scm.com/book/en/v2/images/basic-merging-2.png)

<div align="right">
<small> <small> Source: [git book](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell)</small></small>
</div>

----

- merging a branch creates a new commit resulting from this three-way merge
- branches become useless after merge <br> (delete: ``git branch -d testing``)
- branches are lightweight: let's do plenty of those!
- conflicts might happen: let's go back to this later

----

## Careful! Let's rebase

----

This is a merge

```bash
$ git checkout master
$ git merge experiment
```

![gitsnap](https://git-scm.com/book/en/v2/images/basic-rebase-2.png)

<div align="right">
<small> <small> Source: [git book](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell)</small></small>
</div>

----

This is a rebase...

```bash
$ git checkout experiment
$ git rebase master
```

![gitsnap](https://git-scm.com/book/en/v2/images/basic-rebase-3.png)

<div align="right">
<small> <small> Source: [git book](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell)</small></small>
</div>

----

...followed by a merge.

```bash
$ git checkout master
$ git merge experiment
```

![gitsnap](https://git-scm.com/book/en/v2/images/basic-rebase-4.png)

<div align="right">
<small> <small> Source: [git book](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell)</small></small>
</div>

----

- rebase creates a more linear commit history
- can be dangerous in collaborative workflows (only if people work on the
  rebased branch)
- (IMO) better than merge, but some people have different opinions

---

<section style="text-align: left">

**Actually: <br> let's forget about this and do real world things**


The "real world" github / gitlab workflow is already quite far from these
local considerations. A basic understanding of branches is necessary, but
if you don't do naughty things you should never have to merge or rebase
yourself.

---

## Remotes: <br> just another branch

----


**Working with remotes: set-up an ssh key**

https://help.github.com/articles/connecting-to-github-with-ssh/

----

**Let's do a fork!**

Github: https://github.com/fmaussion/git-test-repo

GitLab: https://git.uibk.ac.at/c7071047/git-ws

**And clone it:**

```bash
$ git clone git@your-fork
```

----

**Give name to your remotes:**

- **upstream**: the "holy" www repository where you (usually) don't have write access
- **origin**: your www fork of the repository where you *have* write access
- **local**: a local clone of your fork


----

```bash
$ git remote -v

$ git remote add upstream git@github.com:fmaussion/git-test-repo.git
OR
$ git remote add upstream git@git.uibk.ac.at:c7071047/git-ws.git

$ git remote -v
```

----

**Locally:**

```bash
$ git checkout -b your-feature-branch
> add a NEW file with your nickname in the filename
> add / commit it
$ git status
```

**Push to origin:**
```bash
$ git push origin your-feature-branch
```

----

### Careful!

**Let's do a "pull-request" (github)**

**Let's do a "merge-request" (gitlab)**

---

### The review process

- reviews are *required* on all major OS projects
- they are a "normal" thing: people are nice but go straight to the point
- **pushing new commits to the branch update the PR / MR!**

----

**Let's play reviews**

---

### Merging

The three options in GitHub:
- merge commit
- **squash and merge** (best option)
- rebase and merge

---

### Updating from remotes

Basic rule: **Never work on the master branches locally**, always
keep master up to data and make new branches:

```bash
$ git checkout master
$ git fetch upstream
$ git merge upstream/master
$ git checkout -b new-branch
```

----

- pushing master to origin is not necessary
- normally one would delete branches after merge
- other (brutal) option: hard reset

```bash
$ git checkout dev-branch
$ git reset --hard upstream/master
$ git push --force origin/dev-branch
```

Only for your personal belongings!

---

**Recap**:

1. update from upstream
2. make a new branch
3. add a feature
4. commit and push
5. open a pull-request / merge-request
6. review and push
7. upstream: merge
8. repeat

---

### Merge conflicts: the hard way

This is a line in master

---

## Resources

- [git reference book](https://git-scm.com/book/en/v2)
- [git handbook from github](https://guides.github.com/introduction/git-handbook/)


---

# Thank you for your attention!
