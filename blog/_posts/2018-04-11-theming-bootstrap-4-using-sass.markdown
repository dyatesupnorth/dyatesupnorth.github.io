---
layout: post
title:  Theming Bootstrap 4 using Sass
date:   2018-04-10 09:49:23
categories: general web design
author: dave
---
The time came for me to begin adding colour to this grayscale site I call home.

I wasn't loading in Bootstrap via npm, rather I was just using the cdn version. Doing it this way does mean I will have to commit the `node_modules` folder to Github. Normally this is fairly bad practice as it means uploading quite a lot of files, not to mention it renders the whole "package management" aspect of npm quite moot. Nonetheless it's what the Bootstrap website says so that's what we're going to do.

First things first then, open up a terminal and type the following:

`npm init && npm install bootstrap`

(If you've already got npm on your project, drop the init.)

Next thing to do is remove all instances of the old way of getting Bootstrap from the site.

Once thats done, add this to your `_main.scss` file:

`@import "../node_modules/bootstrap/scss/bootstrap";`

We'll probably have to tweak that file path when we push it live. I have a hunch about it.

Ok, now we should be in a position to be able to modify our Bootstrap theme. Lets have a look. I'll start by using the official documentations example, lets see if we can change the `body-bg` variable. Typically when starting out doing CSS I'll pick something really obvious, like changing the whole background to blue or something. It needs to be easy verifiable that the CSS we're modifying is actually getting applied.

```
$body-bg: blue;
```

With that working, lets remove that line and work on adding some proper colours to the mix. Apparently colors can go in and out of fashion, so with a quick Google search I went and found an 'en vogue' colour scheme for my site. I decided on [this one](http://www.fashiontrendsetter.com/v2/2017/05/26/ispo-color-palette-springsummer-2018/) by a site called "Fashion Trend Setter", can't really go wrong here can I? There's tons of color palette websites out there, find one and grab a color palette that gives you a color for most of the behaviour classes: primary, secondary, warning, danger etc..

Lets add these bad boys to our `$theme-colors` map, as per the Bootstrap documentation:

```
$theme-colors: (
  "primary": #4762AB, //Amparo Blue
  "secondary": #DDCCA4, //Reed Yellow
  "tertiary": #67655A, //Dusty Olive
  "success": #1C7E4B, //Jolly Green
  "warning": #E48429, //Dark Cheddar
  "danger": #FFFEFE, //Poppy Red
  "info": #2D3743 //Blueberry
);
```

Make sure you add that _before_ the call to the Booststrap .scss file. To use these variables, call them like this:

`background:theme-color("primary");`

And that's all there is to it. I also made myself a `variables.scss` file to start adding these into. Once these steps are done though you're ready to start creating a bootstrap theme the proper way. Happy theming!

