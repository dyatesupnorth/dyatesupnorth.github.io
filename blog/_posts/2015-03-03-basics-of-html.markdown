---
layout: post
title:  Beginners Series 1 - The Basics of HTML5
date:   2015-03-03 01:23:28
categories: general, beginners tutorials
author: dave
---
So I thought I would write a little series on web development starting from the very beginning. If you have no clue how a web page is put together or how websites are made and you would like to know more then start here. I will be aiming to be as clear and as concise as possible, if you need anything clearing up or you would like to know more information then just email me at the usual places.


At this point, you're probably wondering, what is HTML?

Well, HTML stands for "Hyper Text Markup Language" and is the standard markup language used to create web pages.  HTML is written using `<tags>` like `<these>`.

Of course, you can't use any old tags you like, the current standard of HTML, "HTML5" has a [concise list of currently available tags available here](https://developer.mozilla.org/en/docs/Web/HTML/Element). Each tag has its own meaning, and provide a way for the browser you are using to know exactly how to render the content it has been given.

If you're looking into web development, maybe you are wanting to make your own site, maybe you just want to learn some stuff for fun, then you probably want to start by learning how to code HTML.

Why? You might be asking, well, young grasshopper, my reasons are given handily below:

1. Without HTML there is no internet, it is the foundation of every single website you know and love. Begin at the bottom.
2. It is by far the easiest of the web tools to pick up, but does come with it's own set of nuances. Personally I would rather know HTML like the back of my hand so I can spend less time figuring out why something basic doesnt work and I can spend more time debugging and coding the harder stuff.
3. It is usually the first thing employers look for when they are recruiting for web developers, yet is probably the most overlooked skill in the field. Everyone in the industry will know the basics of it, but mastering it will give you an edge.


HTML, or more specifically HTML5 is more than likely the first thing you will come to when making a web site or web app. So you need to learn or at least know the basics of HTML if you are wanting to do anything even close to web development.

HTML can run on any half decent web browser, chances are you are running some variant of either Internet Explorer, Google Chrome or Mozilla Firefox on your computer. To write HTML all you need is a notepad application and a web browser.

With your notepad application fired up, copy and paste the below code into it.


    <!doctype html>
    <html class="no-js" lang="">
        <head>
            <meta charset="utf-8">
            <meta http-equiv="X-UA-Compatible" content="IE=edge">
            <title></title>
            <meta name="description" content="">
            <meta name="viewport" content="width=device-width, initial-scale=1">

        </head>
        <body>

            <h1>Hello world!</h1>

        </body>
    </html>

Now save your file as `index.html` and then either drag the file into your browser window or right click the file and choose to open it in a browser of your choice.

With any luck, you should see the following screen:

![alt text][logo]

[logo]: /img/blogImages/htmlbasics1png.png "Logo Title Text 2"

Conratulations, you just published your first web page. Now lets break those weird tags down so we can see wht they do.