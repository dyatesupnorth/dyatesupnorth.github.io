---
layout: post
title:  Reskinning a portfolio site using Bootstrap 4
date:   2018-04-09 21:59:28
categories: general web design
author: dave
---
At some point you're browsing through old boxes or whatever and you stumble across something that makes you think, "oh yeah, I always meant to do that". This is a bit like that.I've spent te last (3 years?) working on so many projects that little things like updating my portfolio site just never got the time of day. In that time we've had a whole plethora of new suff come out to make use of. Something I've been meaning to do is to finally start moving stuff over to Bootstrap 4. A good start for all that I thought would be to reskin my existing theme. Now I'm not starting from scratch, I don't have time for that, so this is more of an 'update and overwrite' kind of deal, which means a lot of my (bleurgh) legacy stuff will remain in here. Without further ado, lets begin.

On first glance there's not much difference between Bootstrap 3 and 4. Nevertheless lets have a look, first thing we'll do is replace the navbar...

Heres the basic markup modified from my existing navbar to use Bootstrap 4's new markup,

```
<nav class="navbar navbar-light navbar-expand-md bg-light justify-content-center fixed-top">
    <button class="navbar-toggler ml-1" type="button" data-toggle="collapse" data-target="#navbarCollapse">
        <span class="navbar-toggler-icon"></span>
    </button>
    <div class="navbar-collapse collapse justify-content-between align-items-center w-100" id="navbarCollapse">

        <ul class="navbar-nav mx-auto text-center">
            <li class="nav-item"><a href="{{ site.baseurl }}/" class="navbar-brand nav-link mr-0">{{site.title}} : </a></li>
            {% for p in pages %}
                <li class="nav-item {% if p.url == page.url %}active{% endif %}">
                    <a class="nav-link " href="{{ p.url }}">
                        {{ p.title }}
                    </a>
                </li>
            {% endfor %}
        </ul>
        <ul class="nav navbar-nav flex-row justify-content-center flex-nowrap">
            <li class="nav-item"><a class="nav-link" href=""><i class="fa fa-facebook mr-1"></i></a> </li>
            <li class="nav-item"><a class="nav-link" href=""><i class="fa fa-twitter"></i></a> </li>
        </ul>
    </div>
</nav>
```

The results nearly there. Not sure about the icons on the right, but I've got a bigger problem. The way I'm generating a navbar has thrown up a glaring error I hadnt noticed when I first made this blog. I'm including some extra pages I didn't intend on. Lets get rid of them now and code the menu properly.

The solution is to create a `yaml` file and then loop over the values you srt in there. I created `_data/navbar.yaml` and filled it with the following:

```
pages:
  - title: code
    url: /code
  - title: work
    url: /work
  - title: blog
    url: /blog
  - title: about
    url: /about
```

Next I modified my `header.html` file to include the following:

```
<ul class="navbar-nav mx-auto text-center">
            <li class="nav-item"><a href="{{ site.baseurl }}/" class="navbar-brand nav-link mr-0 {% if page.url == '/' %}active{% endif %}">{{site.title}} : </a></li>
            {% for item in site.data.navbar.pages %}
                {% assign class = nil %}
                {% if page.url contains item.url %}
                  {% assign class = 'active' %}
                {% endif %}
                <li class="nav-item {{ class }}">
                    <a class="nav-link " href="{{ item.url }}">
                        {{ item.title }}
                    </a>
                </li>
            {% endfor %}
        </ul>
```

Ok, Looking good for now, I'll decide wether to keep those icons while I work on the rest.
The layout a this point is looking quite boring. I know I said I was gonig for a minimalist theme, but there at least needs to be something for a visitor to look at and since I'm short on hundreds of epic posts I need a solution. If in doubt, throw out an epic stock photo. Everyone loves an epi stock photo. I found this bad boy over on unsplash: https://unsplash.com/photos/Xft-JdC-Jbc.

Using a little CSS trick I learnt back in the day lets make it full width. In my `_base.scss` file I added this snippet:

```
.bg-image {
    padding-top:56px;
    background-image: url("../img/adrian-226109-unsplash.jpg");
    height: 100%;
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
}
```


Ok, it's looking fairly epic but yeah,definitely getting rid of those icons. They were causing the layout to not-be-centred. It was messing with my ki. Away with them.

I quite like the text effect going on here so I'll keep it for now. Plus I've got literally nothing else to repalce it, and i'm not that desperate I'm going to start including cat gifs. Yet. So let's keep it, add some stuff to it and make it snazzier.

I need to position that text halfway down the page, here's the CSS to do it:

```
#ww{
  -webkit-transform: translate(-50%,-50%);
  transform: translate(-50%,-50%);
  position: absolute;
  top: 40%;
  left: 50%;
}
```

So, I target to `#ww` div and using some _absolute_ trickery ( ;) ) It now appears where I want it to. I've taken 10% off as it looked a bit weird being positioned 50% away from the very top.

Looking good. Ok, lets work on that footer.

I needed my footer to be sticky. In the old days we'd get the ol' `position:absolute` trick out and start applying it with mania. Mobile devices be damned. Fortunately for us though the world has moved on, and we're able to use things like flexbox to solve these kinds of problems for us. As of writing there's an even better solution, though browser support isn't up to scratch yet so I've left it off here for now. Anyway, here's my markup for my footer...

```
<footer class="footer">
    <div class="container-fluid">
        <div class="row">
            <div class="col-sm text-md-left">
                <p>
                    Homepage photo by <a href="https://unsplash.com/@aows?utm_medium=referral&amp;utm_campaign=photographer-credit&amp;utm_content=creditBadge" target="_blank" rel="noopener noreferrer" title="Download free do whatever you want high-resolution photos from adrian">adrian</a> on <a href="http://www.unsplash.com" target="_blank">Unsplash</a>
                </p>
            </div>
            <div class="col-sm">
                <ul class="text-center list-inline">
                    <li class="list-inline-item">
                        <a href="http://www.github.com/dyatesupnorth" class="text-muted" target="_blank">
                        <i class="fa fa-github"></i>
                    </a>
                    </li>
                    <li class="list-inline-item">
                        <a href="http://www.twitter.com/mahmehtdave" class="text-muted" target="_blank"> <i class="fa fa-twitter"></i></a>
                    </li>
                    <li class="list-inline-item">
                        <a href="http://stackoverflow.com/users/1532114/dyatesupnorth" class="text-muted" target="_blank"> <i class="fa fa-stack-overflow"></i></a>
                    </li>
                </ul>
            </div>
            <div class="col-sm text-md-right">
                <p>Family | Gym | Code |
                    <a href="/contact">
                        Contact me
                    </a>
                </p>
            </div>
        </div>
    </div>
</footer>
```

My page template markup is now looking like this:

```
<div class="container-fluid content__wrapper bg-image">
       ...code
</div>
```

 and here's the magic:

 ```
 .content__wrapper {
    display: flex;
    min-height: 100vh;
    flex-direction: column;
    padding-top:56px;
}

 .bg-image {
    padding-top:56px;
    background-image: url("../img/adrian-226109-unsplash.jpg");
    height: 100%;
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
}

.content {
  flex: 1;
}
.footer {
    .col-sm{
      text-align: center;
    }
    p {
        font-size: 80%;
        color: white;
    }
}
```

It's beginning to look alright! Couple of extra bits to finish it off and we can start looking at the mobile issues.

Fonts. I used https://fontpair.co/ to pick a font pairing. this time I settled on Nunito and Lora. Here's the markup for adding those CSS fonts to the site:

```
@import url('https://fonts.googleapis.com/css?family=Lora|Nunito');

body,
html {
    height: 100%;
    font-family: 'Lora', serif;
}

h1,
h1,
h3,
h4,
h5 {
    font-family: 'Nunito', sans-serif;
}

.navbar {
    font-family: 'Nunito', sans-serif;
}

h1.banner-main {
    margin: 0;
}

```

Let's talk mobile. I've noticed first off that it's actually looking pretty sweet all the way down to mobile. The only big issue I've noticed is with the mobile menu. Well, there are two issues, one being that the button is at the top of the screen. It woudl be nice if that button was at the bottom on mobile. Ya know, UX and all. first things first though we either need to sort out the push function of the navbar so it pushes out content down. ~~Or we can think outside the box a little and add a simple background colour to menu on mobile. We probably lose a little on design points here, but it's worth it so we dont have to go hacking a push solution together.~~

I just modified the `header.html` file to switch the class depending on the page. Seeing as users will only scroll on pages other than the home page, this makes sense.

```
<nav class="navbar navbar-light navbar-expand-md {% if page.url != '/' %}fixed-top bg-light{% endif %} justify-content-center">
```
Note the `fixed-top` bit. I also had to change the CSS a little bit:
```
#ww {
    position:relative;
    margin-top:10%;
}
```
I mean, it's not exactly vertically centred, but I wasn't really going for that anyway, it just had to look like I had some content.

The home page is looking quite good. For the other pages, it was mostly a case of removing unneeded stuff more than anything. I had to add a couple of text-align classes in there, but overall the conversion went well. A couple of hours work and the site is completely redesigned.

Not bad, bootstrap. not bad at all.



