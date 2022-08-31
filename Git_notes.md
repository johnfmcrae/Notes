# Git

## Git Fundamentals

Here is a quick summary of what you need to do to create a Git repository in a local directory and add its contents.

First, initialize a Git repository using `init`,

```git
git init
```

Now, you can add files or directories one at a time with,

```git
git add <file>
```

or you can add all files of a specific type using the unix wildcard character, `*`, such as `*.c` for all C files. You can add all files with the `-A` or `--all` flag.

```bash
# add all files in the current directory
git add -A 
# add all C files in the current directory 
git add *.c
```

Next, you can check the status of the files that have been staged with

```git
git status
```

If there are any files you accidentally added, you can remove them from the staging area with,

```git
git rm --cached <file>
```

If you want to add files even more quickly, you can skip the staging area and commit all of the untracked files with,

```git
git commit -a -m <commit message>
```

You can also create a `.gitignore` file (see below) if there are any files which you wish to omit from the repository. For example, if you want to ignore mac's `.DS_Store` files, then in `.gitignore` you would write,

```git
*.DS_Store
```

The `*` acts as a wildcard.

Finally, when you ar ready to commit, you can use

```git
git commit -m "your message describing the commit"
```

If you messed up your commit message and need to edit it, you can use,

```git
git commit --amend
```

## Customizing the Log Output

To view the names and status of changed files,

```git
git log --name-status
```

## Stashing Work

You can use the **stashing** to hold onto them changes in your project that you'd like to save but that aren't ready to commit. To start, use the command,

```git
git stash push
```

This will save your changes on the stack in a work in progress (WIP) area. You can stash more than once, so if you want to see the stashes you've made, you can use

```git
git stash list
```

Once you're ready to restore the stashed changes, run

```git
git stash apply
```

In the case where you have more than one stash, Git will assume that you want the most recent stash. If you need to specify a different stash, you can add specify that stash as an input to the apply, for example,

```git
git stash apply 1
```

Once you have applied, you need to clean up your old stash with,

```git
git stash drop
```

Alternatively, you can apply and remove a stash in one go with,

```git
git stash pop
```

## Restoring Changes

Discarding or restoring changes to a specific file will depend on whether that file has been committed or not. If it is still in the staging area, you can discard changes with,

```git
git restore <file>
```

If the file has already been committed, then you can checkout that particular file at an older commit,

```git
git checkout <revision key> -- <path to file>
```

### Reset

`git rest` essentially moves the head pointer. If you use the `--hard` option, it also resets all of the contents in your working directory. For example, using,

```git
git reset [<commit>] --hard
```

will reset all of the files in your working directory to the commit you specified, regardless of whether you have staged or committed any changes. Be careful with this power as it is easy to loose work this way.

## Git Ignore

As mentioned above, the `.gitignore` file allows you to tell Git what files to ignore. There are many handy tricks you can use to make specific rules in these files. Here are a few useful ones,

- Asterisks (`*`) are wild cards, meaning they match zero or more characters
- Two asterisks match nested directories, *e.g.* `a/**/z` matches `a/z`, `a/b/z`, `a/b/c/z` *etc.*
- Square brackets, *e.g.* [abc] match anything inside the brackets
- A slash (`/`) indicates a directory

GitHub offers a large list of [template `.gitignore`.](https://github.com/github/gitignore) files for many languages.

## Branching and Merging

Create a new [branch](https://git-scm.com/docs/git-branch)

```git
git branch <branch name>
```

Then switch to the desired branch with [checkout](https://git-scm.com/docs/git-checkout)

```git
git checkout <branch name>
```

Alternatively, you can use the -b specifier to create a new branch and switch to it directly,

```git
git checkout -b <branch name>
```

If you need to rename a local branch, you can use `git branch --move <old branch name>  <new branch name>`. If you are working on a remote repository, you can push the new branch onto the remote,

```git
git push --set-upstream origin <new branch name>
```

You will then need to remove the old branch from the remote using,

```git
git push origin --delete <old branch>
```

Switching branches changes the files in the working directory.

If you want to see all of your branches, you can use `git branch` without any arguments.

Note that `git log` only shows the commit history below the branch you are currently checked out on. If you want to see the log for all branches, use `git log --all`.

Another option is to use `git switch`. Switch is specifically designed for branches, whereas checkout can also restore files when used as a command on a file

Don’t forge to delete the old branch after you have merged it with another. To do this, you can use,

```git
git branch -d <branch>
```

If you are unsure whether a branch can be deleted, you can use,

```git
git branch --merged
```

Branches that are listed without `*` in front of them have been merged and are safe to delete. Furthermore, `git branch -d <branch>` will fail if you have unmerged changes and give you an error.

## Remote Branches

You can get the information from a remote branch by using the infamous `git clone` command. Remote branches take the form of `<remote>/<branch>`. By default, this is named as `origin/master`, but you can rename the origin locally when you clone the repository by using,

```git
git clone -o <remote name>
```

Putting changes into the remote requires you to run the `git push` command. The default push command either expects you to be pushing from a local branch to a remote branch which have the same name, or in the event where the branch does not exist in the remote repository, it will create the branch on the remote with the same name as the local branch. If you want to rename  a new branch on the remote repo, or push from a branch that has a different name on the local repo into the remote repo, you can use,

```git
git push origin <local name>:<remote name>
```

## Rebasing

A rebase can provide the same result as a merge: taking one branch and bringing it into another. But whereas a merge simply combines the pointers from two branches, a rebase will apply the changes themselves and create a new commit. In the simplest case, performing a rebase will result in a linear history. As an example, if you were to have a `master` and an `experiment` branch, you could rebase he experiment onto the master with,

```git
git checkout experiment
git rebase master
```

then do a merge to re-assign the master pointer to the most recent commit, created by the rebase,

```git
git checkout master
git merge experiment
```

## Working with GitHub

[GitHub](https://github.com/) is a great place to upload your repositories and share them with others. To interact with GitHub, you can either go to your profile in your web browser, or use the command line version, [GitHub CLI](https://cli.github.com/), directly in terminal. I will be using GitHub CLI here.

### Cloning from GitHub

**Cloning** means making a copy of a repository on GitHub into your local directory. Cloning is done with the `clone` command. For example,

```git
git clone https://github.com/johnfmcrae/Notes
```

will copy my [notes repo](https://github.com/johnfmcrae/Notes). You can also rename your local copy of the cloned directory by adding the name you want to call it after the url,

```git
git clone https://github.com/johnfmcrae/Notes localNotes
```

### Uploading an Existing Repository to GitHub

Let's say you've created a local repository on your computer and you are ready to upload it to GitHub. This is quite simple with GitHub CLI. You can either create a new repository interactively, or you can create it manually. To enter interactive mode,

```git
gh repo create
```

To manually create a public GitHub repo, enter

```git
gh repo create --public --source . --push
```

Source expects an input, so I if you are in the directory you want to push you can use a period, `.`

### Pushing to a Remote Repository Using Git

First, you can check the remote url with,

```git
git remote -v
```

If this is correct, you can push to the remote repository using,

```git
git push -u origin head
```

## Combining Commits

If you have many local commits in your Git repository, you can go into the log and combine multiple commits into one so that you can provide a single commit to the remote instead of adding all of your individual commits. The easiest way to do this is to do a soft reset on the head pointer,

```bash
git reset --soft HEAD~2 
git commit -m "new commit message"
```

However, this will overwrite the old commit messages and will require you to write a new message. If you want to combine the messages you already wrote, you can use `git rebase` in interactive mode,

```git
git rebase -i HEAD~2
```

This will launch a window with a bunch of options of how to squash your commits. You will need to choose one commit with `pick` and then squash the other commits into that chosen commit with `squash`. Git will want you to "squash upwards", so you will need to pick the *older* commit. Pay attention to the order in which the commits are given in the interactive rebase editor, it should list the commits oldest to newest. If you squash the commits correctly, you will be prompted with a second editor which will let you edit the combined commit message. For more info, see [this Stack Overflow post](https://stackoverflow.com/questions/2563632/how-can-i-merge-two-commits-into-one-if-i-already-started-rebase)

Lastly, you can also reset based on a commit hash, if you don't want to have to count how many commits you're merging,

```git
git rebase -i <commit hash>
```

You will need to specify the hash *before* the one you want to squash at. You can either just enter the hash of the commit before or you can use the `^` character on the hash you want to squash at, which means the same thing \[[source](https://stackoverflow.com/questions/41464752/git-rebase-interactive-the-last-n-commits)\].

## Quick Reference to Common and Useful Git Commands

### `status`

Displays the status of working tree. Use `-s` or `--short` to display a condensed version

### `config`

Show configuration settings and locations

```git
git config --list --show-origin
```
