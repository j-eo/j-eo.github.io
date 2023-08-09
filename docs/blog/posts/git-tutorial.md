---
date: 2023-08-08
authors:
  - Jake
categories:
  - Guide
tags:
  - git
comments: true
---

# How to get started with Git

[:material-git: Git](https://git-scm.com/) is a free and open-source distributed VCS (version control system) designed for programmers to collaborate together on projects. Understanding Git is essential for anyone interested in contributing to open-source, and this tutorial will help you get started.
<!-- more -->
??? warning "Do not confuse Git with GitHub or GitLab"
    Git is a VCS (version control system), while GitHub and GitLab are web-based Git repository hosting services. They are used to host Git repositories, and provide additional features like issue tracking, pull requests, etc.

## More about Git

Git was originally authored by [Linus Torvalds](https://en.wikipedia.org/wiki/Linus_Torvalds) in 2005 for the development of the [Linux kernel](https://kernel.org/). It is used by millions of developers worldwide, and is the most popular VCS in the world. It is performant and feature-rich, and is extensively used by almost all major tech companies.

??? tip "Random Git trivia"
    Here's what Linus had to say about its name:

    <blockquote>I'm an egotistical bastard, and I name all my projects after myself. First 'Linux', now 'Git'.</blockquote>

    Git is a British slang for *a silly, incompetent, stupid or annoying person*.[^1] According to him, Git can mean anything according to your mood[^2]:

    1. Random three-letter combination that is pronounceable, and not actually used by any common UNIX command. The fact that it is a mispronunciation of "get" may or may not be relevant.
    2. Stupid. Contemptible and despicable. Simple. Take your pick from the dictionary of slang.
    3. "Global information tracker": you're in a good mood, and it actually works for you. Angels sing and light suddenly fills the room.
    4. "Goddamn idiotic truckload of sh*t": when it breaks.

## Installing Git

Git usually comes installed by default on most Mac and Linux machines. If your machine does not come with Git, grab an appropriate download from the [official website](https://git-scm.com/downloads).

### Windows

By default, Git does not come with Windows. If you have [winget](https://docs.microsoft.com/en-us/windows/package-manager/winget), run the following command to install Git:

``` bash
winget install --id Git.Git -e --source winget
```

### Verify installation

To check if Git is installed on your machine, run the following command:

``` bash
$ git --version
git version 2.40.0
```

## Getting started

<!-- image wasn't rendering in admonition, workaround -->
<details class="tip inline end" markdown><summary>Relevant comic to scare you</summary>
<figure markdown>
![Relevant XKCD](https://imgs.xkcd.com/comics/git.png){ loading=lazy width=200px }
<figcaption markdown>
:material-magnify-plus-outline: Click to enlarge. Source: [XKCD 1597](https://xkcd.com/1597).</figcaption>
</figure>
</details>

The first thing you do after installing Git is to set up your identity. Your username and email will be used to identify your commits. Use the following commands to set up your identity.

``` bash
git config --global user.name "your-username"
git config --global user.email "youremail@domain.tld"
```

Replace `your-username` and `youremail@domain.tld` with your username and email respectively.

??? tip "Global vs local configuration"
    You can use the `--global` flag to set your identity globally, or you can omit it to set your identity for the current repository only.

### Creating a repository

Let's start by creating a Git repository. Create a folder for your project, and run the following command inside it:

``` bash
git init
```

This will create a `.git` folder inside your project folder. This folder contains all the information about your repository, including the history of all the changes made to your files. Congratulations, you have created your own Git repository!

??? danger "Deleting the repository"
    If you want to delete your Git repository, simply delete the `.git` folder. This will delete all the history of your repository, and you will not be able to recover it.

### Adding files

Let's add some files to our repository. Create a file called `README.md`.

``` bash
echo "# My first Git repository" > README.md
```

??? question "What is `README.md`?"
    `README.md` is a Markdown file that contains information about your project. It is usually present in most repositories, and is used to provide information about the project.

    Markdown is a lightweight markup language which is used to format text. It is human readable and is easy to learn. Markdown files end with `*.md`. Fun fact, this blog is written in Markdown!

Now that the file is created, let's add this file to our repository. Run the following command:

``` bash
git add README.md
```

This will add `README.md` to a temporary staging area which Git calls the *index*. The index is used to store all the files that you want to commit (save) to the repository.

??? tip "Staging multiple files"
    You can stage multiple files by running `git add` multiple times, or by adding a list of files separated by spaces.

    ``` bash
    git add file1 file2 file3
    ```

    or you can add all the files in the current directory by running:

    ``` bash
    git add .
    ```

Whenever we complete a task, we stage them to the index. Staged files are ready to be committed to the repository. Let's commit our changes to the repository.

### Committing files

Our files are now waiting to be committed (permanently saved) to the repository. Run the following command to commit the staged files:

``` bash
git commit -m "commit message"
```

You should add an appropriate commit message to indicate the changes in the commit.

<!-- image wasn't rendering in admonition, workaround -->
<details class="warning" markdown><summary>Commit messages are important</summary>
<figure markdown>
![Relevant XKCD](https://imgs.xkcd.com/comics/git_commit.png){ loading=lazy align=right }
<figcaption markdown>:material-magnify-plus-outline: Click to enlarge. Source: [XKCD 1296](https://xkcd.com/1296).</figcaption>
</figure>
Commit messages help you and others understand the changes made in the commit. A good commit message should be short and descriptive. It should be in the imperative mood, and should not end with a period. For example, a good commit message would be `Add README.md` or `Fix typo in README.md` instead of `Added README.md` or `fixed typo in README.md.`.
</details>

### Viewing commit history

To view the commit history of your repository, run the following command:

``` bash
git log
```

Use the `--oneline` flag to view the commit history in a single line:

``` bash
git log --oneline
```

Use ++q++ to exit.

!!! info "To push your local commits to a remote repository"
    To push your local repository to a remote (like GitHub), run the following command:

    ``` bash
    git push
    ```

    You will be prompted to enter your username and password. After entering them, your local repository will be synced with the remote repository.

## There you go

You have successfully created your first Git repository, and have learned the bare basics of Git. This should help you get started with Git. I will post more tutorials on Git in the future, like working with branches, merging, etc. Stay tuned!

!!! abstract ""
    This is my first tutorial post. Please leave your feedback on the comments below. Thank you!

<!-- markdownlint-disable link-image-reference-definitions -->
[^1]: According to [Wiktionary](https://en.wiktionary.org/wiki/git#Noun).
[^2]: Linus himself wrote this in the [initial README file](https://github.com/git/git/blob/e83c5163316f89bfbde7d9ab23ca2e25604af290/README) for Git.
<!-- markdownlint-enable link-image-reference-definitions -->