---
layout: post
title:  "How to delete all local branches except master in git"
date:   2019-11-17
banner_image: master-git.jpg
tags: [git, windows, linux, mac, command-prompt, command-line, version-control, how-to]
---

The idea is to list the local branches using `git branch`, filter the results and apply `git branch -d` for each line.

## Linux/MacOS
{% highlight shell %}
git branch | grep -v master | xargs git branch -d
{% endhighlight shell %}

`git branch` lists all available local branches. With `grep -v` the `master` branch is filtered out. Then each line is passed to `git branch -D` using `xargs`.
 
## Windows
{% highlight shell %}
FOR /f "tokens=*" %%G IN ('git branch ^| findstr /v master') DO git branch -d %%G
{% endhighlight shell %}

The same idea here, but with different tools. Instead of `grep -v` we'll use `findstr /v`. Unfortunately `xargs` has no alternative, the only way is to use a [`for`](https://ss64.com/nt/for_f.html) loop. 

<!--more-->

## PowerShell
{% highlight powershell %}
git branch --format '%(refname:lstrip=2)' | Where-Object { $_ -ne 'master' } | ForEach-Object { git branch -d $_ }
{% endhighlight powershell %}

Here we output the branches without leading spaces and in quotes(`--format '%(refname:lstrip=2)'`). The `grep -v` alternative in `PowerShell` is `Where-Object` with the `-ne` (not equals) operator. Then for each line `git branch -d` is applied with `ForEach-Object`, which is the `xargs` alternative.