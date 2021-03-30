---
layout: post
title: What is Github
subtitle: A brief talk on Github
date: 2021-01-27 03:45:00
background: /images/github/github.png
---
**What is Git?**

Git is a free and open source distributed version control system which was started by Linus Torvalds and designed to handle software projects with speed and efficiency.

**What is a Version Control System?**

Version control systems are a category of software tools that help a software team manage changes to source code over time. Version control software keeps track of every modification to the code in a special kind of database. If a mistake is made, developers can turn back the clock and compare earlier versions of the code to help fix the mistake while minimizing disruption to all team members.

There are other Version Control Systems out there actually, some distributed, some centralized, but Git is the most widely used these days because it is distributed, optimized for fast commits and checkouts, and has a non-destructive updates through use of an immutable log. Although, Git could seem a bit complex with rather terse beginnings, it is the version control tool of choice for everyone from web designers to kernel developers.

Other examples of Version Control Systems include Mercurial, SVN, CVS, Subversion, Perforce etc.

**What the heck is Github then???**

GitHub is a Git repository hosting service, but it adds many of its own features. While Git is a command line tool, GitHub provides a Web-based graphical interface. It also provides access control and several collaboration features, such as a wikis and basic task management tools for every project. Git, therefore is the software that runs at the heart of Github.

A repository is simply a directory or storage space where your projects can live. Sometimes GitHub users shorten this to “repo.” It can be local to a folder on your computer, or it can be a storage space on GitHub or another online host. You can keep code files, text files, image files, you name it, inside a repository.

In summary, Github is simply a hosting service, it allows users and teams to host software projects for collaborative work on it and version control, and at the heart of Github is the Git version control system. In other words, Github simplifies the process of using Git.

To use Git, therefore, one has two options: either to Download the Git bash on your PC and use the command line tool directly or to head on to Github website and rock with the fancy GUI.

**Some Terminologies**

Here are some very useful and important and useful terminologies one should really understand while working with Github...

**Repository:**&nbsp;A repository is a storage space where your project lives. It can be local to a folder on your computer, or it can be a storage space on GitHub or another online host. You can keep code files, text files, images or any kind of a file in a repository. You need a GitHub repository when you have done some changes and are ready to be uploaded.

**Branching:**&nbsp;Branches help you to work on different versions of a repository at one time. Let’s say you want to add a new feature (which is in the development phase), and you are afraid at the same time whether to make changes to your main project or not. This is where git branching comes to rescue. Branches allow you to move back and forth between the different states/versions of a project. In the above scenario, you can create a new branch and test the new feature without affecting the main branch. Once you are done with it, you can merge the changes from new branch to the main branch. Here the main branch is the master branch, which is there in your repository by default.

**Commit:**&nbsp;This is simply an operation that helps you to save the changes in your file. It is good practice to always provide the message, just to keep in the mind the changes done by you.

**Pull Request:**&nbsp;This is a command that tells the changes done in the file and request other contributors to view it as well as merge it with the master branch. Once the commit is done, anyone can pull the file and can start a discussion over it. Once its all done, you can merge the file. Pull command compares the changes which are done in the file and if there are any conflicts, you can manually resolve it.

**Merge:**&nbsp;Apparently, the merge command simply merges changes into the main master branch.

**Cloning:**&nbsp;Simply means downloading. Suppose you want to use some code which is present in a public repository, you can directly copy the contents by cloning or downloading.

**Forking:**&nbsp;Suppose, you need some code which is present in a public repository, under your repository and GitHub account. For this, we need to fork the public repository. It is worth noting that changes made in the original repository will be reflected back to the forked repository. If you make a change in forked repository, it will not be reflected to the original repository until and unless you have made a pull request.

That’s all for this post, I hope someone finds it useful.
