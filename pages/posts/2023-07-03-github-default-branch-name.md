---
title: Updating Github Default Branch Name
date: 2023-07-03T13:37:00.000Z
description: A quick guide on how to change the default branch name in Github and Git.
tag: git
author: Isaac
---

I think it's a good idea to change the default branch name used in github and git from master to main. Here's a simple guide on how to do that. 


## Easy change in github setting page. 

For a repo that already exists in github, here are some screenshots. Of course you can always refer to the [Github docs ](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-branches-in-your-repository/renaming-a-branch) for the latest tips.

First you open the repo you want to change, navigate to the branches page. You can get there by clicking the link on the main repo page that tells you how many branches you have

![git-repo-branches](/images/git-repo-branches.png "git-repo-branches")

From here, you can find your default branch and on the right hand side there should be an edit button. You can simply rename to main branch there, it can take a few moments for the changes to be updated on Github.

![git-rename-branch](/images/git-rename-branch.png "git-rename-branch")

As you can see from this image, there are somethings to take into consideration. Github pages will become unpublished until a new commit is made to the default branch. 

And of course, everyone that has this repository on their local machines, they will not receive any changes automatically, instead they will need to run these Git CLI commands in order to update their repository. (They could always just delete and re-clone if all else fails)

Here are the commands they need to run to update their repo tot he new default branch name: 

```sh
git branch -m master main
git fetch origin
git branch -u origin/main main
git remote set-head origin -a
```

### Change Git Config Default Branch Name

One more thing I like to change on my local machine is the default branch name when you initialize a new git branch.

`git config --global init.defaultBranch main`

This makes it so that if you ever initialize a new git repo on your machine, ie `git init`, it will use `main` as the new default branch name automatically.


## Conclusion

You should be all set and ready to go. Now your repo has been updated, and any new repos you make locally should be updated as well. I hope this helps you find the commands and pages you need, refer to the docs if any updates are made since the time of writing. Thanks!
