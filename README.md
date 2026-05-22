# PP5

## Goal

In this exercise you will:

* Use Git **locally** on your own machine: create branches, make commits, and merge them back.
* Set up and interact with a **bare** Git repository on an SSH‐accessible server (e.g. **vorlesungsserver**, or any machine you have SSH access to).
* Push and pull to/from **GitHub** and the **THGA GitLab** server.
* Practice **forking** an existing repo, making changes, and submitting a **Pull Request** (on GitHub) or **Merge Request** (on GitLab).

**Important:** Start a stopwatch when you begin and work uninterruptedly for **90 minutes**. Once time is up, stop immediately and document exactly where you had to pause.

---

## Workflow

1. **Fork** this repository
2. **Modify & commit** your solution
3. **Submit your link for Review**

---

## Prerequisites

* Several starter repos are available here:
  [https://github.com/orgs/STEMgraph/repositories?q=Git%3A](https://github.com/orgs/STEMgraph/repositories?q=Git%3A)
* Ensure you have **SSH access** to a remote server (e.g., “vorlesungsserver”).
* Throughout, consult Git’s built-in man-pages (`git help <command>`) for explanations and options.

---

## Tasks

### Task 1: Local Git – Branching & Merging

1. Create a new directory in your home directory and initialize a repository in it. 
2. In one of your cloned repos, initialize a new branch called `feature-1`.
3. On `feature-1`, create a file `feature.txt` containing a short description of what you’re doing.
4. Commit your changes, then switch back to `master` (or `main`), and merge `feature-1` into your `master`.
5. Resolve any merge conflicts (if they arise) by hand, then commit the merge. 

**Your Commands & Output**

```bash
git checkout -b feature-1
echo "This is my feature branch work" > feature.txt
git add feature.txt
git commit -m "Add feature.txt in feature-1"

git checkout -b main
git merge feature-1
git status

Initialized empty Git repository in /home/Lu21k09as/pp5-test/.git/
Switched to a new branch 'feature-1'
[feature-1 (root-commit) 983ee4d] Add feature.txt in feature-1
 1 file changed, 1 insertion(+)
 create mode 100644 feature.txt
Switched to a new branch 'main'
Updating 0000000..983ee4d
Fast-forward
 feature.txt | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 feature.txt
On branch main
nothing to commit, working tree clean

```bash
---

### Task 2: Bare Repository on an SSH Server

1. On your SSH server (e.g., “vorlesungsserver”), create a **bare** repo at `~/repos/myproject.git`:

   ```bash
   ssh youruser@vorlesungsserver \
     "mkdir -p ~/repos/myproject.git && cd ~/repos/myproject.git && git init --bare"
   ```
2. On your local machine, add it as a remote named `origin-ssh`:

   ```bash
   git remote add origin-ssh youruser@vorlesungsserver:~/repos/myproject.git
   ```
3. Push your `master` branch to `origin-ssh`, then clone it into a fresh directory to verify.

**Your Commands & Output**

```bash

ssh youruser@vorlesungsserver \
  "mkdir -p ~/repos/myproject.git && cd ~/repos/myproject.git && git init --bare"
# Ausgabe (Git bestätigt keine Commit-History, nur Initialisierung):
Initialized empty Git repository in /home/youruser/repos/myproject.git/


git remote add origin-ssh Lu21k09as@128.140.85.215:~/repos/myproject.git
git push origin-ssh main
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Writing objects: 100% (3/3), 100 bytes | 100.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To youruser@vorlesungsserver:~/repos/myproject.git
 * [new branch]      main -> main
cd ~
git clone Lu21k09as@vorlesungsserver:~/repos/myproject.git myproject-test
Cloning into 'myproject-test'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (3/3), done.
Receiving objects: 100% (3/3), 150 bytes | 150.00 KiB/s, done.
```

---

### Task 3: GitHub & THGA GitLab

1. On [GitHub](github.com), create a new empty repo under your account named `myproject-gh`.
2. On [THGA GitLab](gitlab.thga.de), create a new project named `myproject-gl`.
3. In your local repository, add these as remotes:

   ```bash
   git remote add github  git@github.com:YOUR_USERNAME/myproject-gh.git
   git remote add gitlab  git@gitlab.thga.de:YOUR_USERNAME/myproject-gl.git
   ```
4. Push your `master` branch to both `github` and `gitlab` remotes.

> Hint: You are just adding two more bare-remotes to your already existing repository!

**Your Commands & Output**

```bash
Lu21k09as@vorlesung:~/pp5-test$ mkdir -p ~/repos/myproject.git
Lu21k09as@vorlesung:~/pp5-test$ cd ~/repos/myproject.git
Lu21k09as@vorlesung:~/repos/myproject.git$ git init --bare
Initialized empty Git repository in /home/Lu21k09as/repos/myproject.git/

Lu21k09as@vorlesung:~/repos/myproject.git$ cd ~/pp5-test
Lu21k09as@vorlesung:~/pp5-test$ git remote add origin-ssh Lu21k09as@128.140.85.215:~/repos/myproject.git

Lu21k09as@vorlesung:~/pp5-test$ git push origin-ssh main
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Writing objects: 100% (3/3), 259 bytes | 259.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
To 128.140.85.215:~/repos/myproject.git
 * [new branch]      main -> main

Lu21k09as@vorlesung:~/pp5-test$ cd ~
Lu21k09as@vorlesung:~$ git clone Lu21k09as@128.140.85.215:~/repos/myproject.git myproject-test
Cloning into 'myproject-test'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Receiving objects: 100% (3/3), done.
```

---

### Task 4: Fork, Modify, and Pull/Merge Request

1. On GitHub, **fork** one of the repos from the STEMgraph org.
2. Clone your fork locally, create a branch `pp5-changes`, and make a small change (e.g., update the README).
3. Commit and push `pp5-changes` to **your** fork, then open a **Pull Request** against the original repo.
4. Repeat on THGA GitLab: fork another students repository, clone, branch, change, push, and open a **Merge Request**. If your peers opened a merge request to your repository, review and merge or decline it!

**Your PR/MR Links & Descriptions**

* GitHub PR: *paste URL and a one-sentence summary*
* GitLab MR: *paste URL and a one-sentence summary*

---

**Remember:** Stop working after **90 minutes** and record where you stopped!
Updated by Lu21k09as
