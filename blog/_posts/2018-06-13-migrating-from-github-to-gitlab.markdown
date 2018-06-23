---
layout: post
title:  Migrating my blog site from Github to Gitlab
date:   2018-06-23 14:43:23
categories: gitlab, devops
author: dave
---

now I won't say that the _only_ reason I'm migrating to Gitlab from Github is because of the recent Microsoft acquisition, but I reckon it's in there as one of the reason why I decided to look a little further into what gitlab offers. It's been on my radar for a while, as for years now I've used Bitbuckets' services for my own, personal, private projects, and Github I've always used for the open source and Commercial offerings. Having a service that blends the two, whilst also offering a smattering of other DevOps functionality seemed like a big win, so I started looking ito how easy (or difficult) it would be to migrate. 

One of my favourite features abut github, though admittedly I don't use it often :D is how it handles the Git pipeline for this blog. So it seemed like good sense to start there, and I figured I could document the journey along the way.

Ok, my first step was to actually create a [Gitlab account](https://gitlab.com/).

Next thing to do was have a look and see if there's anything in their documentation that would help me in my quest.
I created a New Project and followed the instructions as per the documentation in swapping out my current github config for theirs: 

```
cd existing_repo
git remote rename origin old-origin
git remote add origin 
git@gitlab.com:dyatesupnorth/dyatesupnorth.gitlab.io.git
git push -u origin --all
git push -u origin --tags
```

I also needed to add a `.gitlab-ci.yml` file which consisted of the following which I nicked from their Jekyll demo:

```
image: ruby:2.3

variables:
  JEKYLL_ENV: production

before_script:
  - bundle install

test:
  stage: test
  script:
  - bundle exec jekyll build -d test
  artifacts:
    paths:
    - test
  except:
  - master

pages:
  stage: deploy
  script:
  - bundle exec jekyll build -d public
  artifacts:
    paths:
    - public
  only:
  - master
```

Now the last thing, and one bit which I was stuck on for tooo long was why Gitlab wasn't deploying my site. Everything I read up on seemed to just suggest the steps above, and Gitlab would handle the rest. After umpteen attempts at getting the pipeline to run, I eventually twigged what was going on (see: read the bloody error!) and as it turns out all I had to do was add a Gemfile to the project! 


```
source "https://rubygems.org"
ruby RUBY_VERSION

# This will help ensure the proper Jekyll version is running.
gem "jekyll", "3.4.0"

# Windows does not include zoneinfo files, so bundle the tzinfo-data gem
gem 'tzinfo-data', platforms: [:mingw, :mswin, :x64_mingw, :jruby]

```

Looking at the example project it was the one piece that was missing from my install. I added that and now my blog lives on!
