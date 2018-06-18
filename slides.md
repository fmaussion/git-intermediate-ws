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
- A typical "pull/merge request" cycle
- Handling conflicts
- Tags and DOIs with Zenodo
- Continuous integration: testing with Travis, documentation with ReadTheDocs
- Anything else?

---

### Q: Who is using git in this room, and what for?

---

**The version control system**

![git](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e0/Git-logo.svg/200px-Git-logo.svg.png)

----

<section style="text-align: left;">

## Installing git

Linux:

```bash
$ sudo apt install git
```

<br>

Elsewhere:

https://git-scm.com/downloads

<br>

On Windows: use Git Bash!

---

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
- [GitLab](https://about.gitlab.com/): not a hosting service - but an open-source
  platform: UIBK has its own deployment (https://git.uibk.ac.at)


---

## Hands-on!

----

## First-time setup

```bash
$ git config --global user.name "John Doe"
$ git config --global user.email johndoe@example.com
$ git config --global color.ui auto
```

----

## Create an online repository

- create a repository on gitlab: https://git.uibk.ac.at or github
- clone the repository (demo)
- **Alternative:** start from a local (empty) folder: ``$ git init``

----

## Top 5 git commands for beginners

```bash
$ git status
$ git add
$ git commit -a -m ""
$ git push origin master
$ git log
```
----

## Ignoring files

- ``.gitignore`` file

----

Git is best learned "by doing"! Try it at home and come back in two weeks
with questions ;-)

----

## Resources

- [git reference book](https://git-scm.com/book/en/v2)
- [git handbook from github](https://guides.github.com/introduction/git-handbook/)


---

## Github-pages

----

<section style="text-align: left;">

- [github-pages](https://pages.github.com/): service to host your
website as a git repository
- each time you push to the online repository, the website is built and updated <!-- .element: class="fragment" -->
- good: free, easy, custom domains allowed <!-- .element: class="fragment" -->
- bad: all your content is on github.com <!-- .element: class="fragment" -->

----

## Demo + hands-on in five steps

---

# Thank you for your attention!
