---
layout: post
title:  Migrating my blog site from github to Gitlab
date:   2018-06-13 09:49:23
categories: gitlab, devops
author: dave
---

now I won't say that the _only_ reason I'm migrating to Gitlab from Github is because of the recent Microsoft acquisition, but I reckon it's in there as one of the reason why I decided to look a little further into what gitlab offers. It's been on my radar for a while, as for years now I've used Bitbuckets' services for my own, personal, private projects, and Github I've always used for the open source and Commercial offerings. Having a service that blends the two, whilst also aoffering a smattering of other DevOps functionality seemed like a big win, so I started looking ito how easy (or difficult) it would be to migrate. 

One of my favourite features abut github, though admittedly I don't use it often :D is how it handles the Git pipeline for this blog. So it seemed like good sense to start there, and I figured I could document the journey along the way.

Ok, my first step was to actually create a [Gitlab account](https://gitlab.com/).

Next thing to do was have a look and see if there's anything in their documentation that would help me in my quest.
I created a New Project and followed the instructions as per the documentation in swapping out my current github config for theirs.: 

```
cd existing_repo
git remote rename origin old-origin
git remote add origin 
git@gitlab.com:dyatesupnorth/dyatesupnorth.gitlab.io.git
git push -u origin --all
git push -u origin --tags
```