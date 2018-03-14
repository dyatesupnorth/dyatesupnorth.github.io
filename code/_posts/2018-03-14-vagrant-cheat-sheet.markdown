---
layout: post
title:  Vagrant Cheat Sheet
date:   2018-03-14 00:01:13
categories: code
---
Below are some of my most used `Vagrant` commands. Also works aas a kind of how to I guess if you just enter each command one after the other.

Not sure what Vagrant is? [Check it out.](https://www.vagrantup.com/intro/index.html)


Set up a new Vagrant instance
```
vagrant init
```

Add a box to your new Vagrant instance
```
vagrant box add ubuntu/xenial64
```

Boot into Vagrant
```
vagrant up
```

Then SSH into it...
```
vagrant ssh
```
