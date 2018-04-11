---
layout: post
title:  Creating a timeline using CSS
date:   2018-04-10 09:49:23
categories: general web design
author: dave
---
Timelines are pretty cool but for some reason they remind me of museums. No, it's not because they're archaic or they belong in one. I think it's because I always enjoyed being able to step through the history. Timelines provide a really visual way of displaying data chronologically that lets your users know immeditatly what happened when. That's a good thing.

If you're looking to find the steps needed to create a timeline using CSS then look no further.

Paste the following HTML:

<script src="https://gist.github.com/dyatesupnorth/03850bd95b0cf405bdb742e459e29551.js"></script>

I'm currently using Bootstrap, so you'll notice a couple of helper classes such as `rounded-circle` that come from that framework.

Next step is the CSS. I'm using SCSS to compile my CSS, which is included here:

<script src="https://gist.github.com/dyatesupnorth/b34e41f1a4dca13aebbf806b27e40f6b.js"></script>

Depending on your screen size and div width's etc. You might need to tweak the positioning of the `.line:before` class in each of the even / odd panels.

... and that's all there is to it. Here's the Codepen to see it all in action:

<p data-height="265" data-theme-id="dark" data-slug-hash="geqXXp" data-default-tab="css,result" data-user="dyatesupnorth" data-embed-version="2" data-pen-title="Bootstrap 4 Portfolio Timeline" class="codepen">See the Pen <a href="https://codepen.io/dyatesupnorth/pen/geqXXp/">Bootstrap 4 Portfolio Timeline</a> by Dave Yates (<a href="https://codepen.io/dyatesupnorth">@dyatesupnorth</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>
