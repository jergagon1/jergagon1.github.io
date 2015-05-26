---
layout: post
title:  "Rebasing in Git"
date:   2015-05-25 21:00:00
categories: technical
tags:
- git
- rebase
---
There are powerful commands in Git that give you precise control over your workflow and commit history. One such command is `git rebase`. It offers some clear benefits over a standard merge.

A common workflow in git is to create a branch to develop and test a new application feature. For the sake of this post, let's say that your main development branch is master. Your feature branch is forked off of master at a particular commit. You then work on the feature branch until you are ready to submit your changes back to master for review and incorporation.

While you are working on your feature branch, commits might also be occurring on the master branch. These commits move the HEAD of the master branch past the originating commit of your branch. When you merge your changes into master, you potentially introduce merge conflicts as your branch is out-of-date with master.

Additionally, the commit history becomes jumbled because there are two parallel workflows that are being merged together. The result is a non-linear commit history that is hard to follow.

Git rebase is a way to address these issues. It basically snips your feature branch off of the master branch from the originating commit and reattaches it to a later commit on master. All of the current changes from master are incorporated into your feature branch commits.

To use rebase, you checkout your feature branch and type the following command:

{% highlight bash %}
git rebase <commit reference>
{% endhighlight %}

You can provide a commit reference in multiple ways including a \*SHA, a branch name or a version tag.

One side effect of this is that all of the commits on your feature branch will change in terms of the SHA and potentially the code content.

So what are the potential pitfalls of rebasing?

When you rebase, you are essentially removing one or more commits from the commit history of the project and replacing them with new commits.

If someone forked your repo and was working from one of the commits that you removed, you would be creating a complicated upstream problem for them. The parent commit of their fork would be gone.

For this reason, rebasing in public repos is discouraged and considered bad practice.

\*Interesting side note: The "SHA" mentioned above refers to [SHA-1](http://en.wikipedia.org/wiki/SHA-1 "Link to wikipedia article on SHA-1") which is a "Secure Hash Algorithm". It is sometimes used for hashing data in security, but Git uses it to create a unique identifier that guarantees the uniqueness and consistency of the data snapshot in the commit.