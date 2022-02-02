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
git commit -a
```

You can also create a `.gitignore` file if there are any files which you wish to omit from the repository. For example, if you want to ignore mac's `.DS_Store` files, then in `.gitignore` you would write,

```git
*.DS_Store
```

The `*` acts as a wildcard.

Finally, when you ar ready to commit, you can use

```git
git commit -m "your message describing the commit"
```

## Git Ignore

As mentioned above, the `.gitignore` file allows you to tell Git what files to ignore. There are many handy tricks you can use to make specific rules in these files. Here are a few useful ones,

- Asterisks (`*`) are wild cards, meaning they match zero or more characters
- Two asterisks match nested directories, *e.g.* `a/**/z` matches `a/z`, `a/b/z`, `a/b/c/z` *etc.*
- Square brackets, *e.g.* [abc] match anything inside the brackets
- A slash (`/`) indicates a directory

GitHub offers a large list of [template `.gitignore`.](https://github.com/github/gitignore) files for many languages.

## Branching

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

Switching branches changes the files in the working directory.

Note that `git log` only shows the commit history below the branch you are currently checked out on

Another option is to use `git switch`. Switch is specifically designed for branched, whereas checkout can also restore files when used as a command on a file

Don’t forge to delete the old branch after you have merged it with another. To do this, you can use,

```git
git branch -d <branch>
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

### Uploading and Existing Repository to GitHub

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

## Quick Reference to Common and Useful Git Commands

### `status`

Displays the status of working tree. Use `-s` or `--short` to display a condensed version

### `config`

Show configuration settings and locations

```git
git config --list --show-origin
```
