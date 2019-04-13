---
layout: post
title: "Building this site"
excerpt: >
    This is a standalone post logging my building adventures with this site.
    Nifty widgets I've made or praise-worthy plugins I've found will be mentioned here.
    Hopefully it will be useful for those hopping into Github/Jekyll blogging.
disqus_id: 20
---
I spent a long time deciding between using GitHub/Jekyll or WordPress for my blog.
The former is fast, customizable, and gives hacker-cred, while the latter is easy to set up and offers non-static site features.
As you can see: I ended up going with the GitHub/Jekyll combo.
This first post will serve as a record of my experiences building this blog without WordPress magic.
Because I want the blog to be focused on less-front-end-type things, there will be no follow-ups to this post.
As I build the blog, the updates will appear here.

I want to establish I'm not some elite hacker web developer.
The folks that make the amazing tools deserve all the credit.
I'm basically just figuring out how to use them and giving more praise.

### MathJax

$$\LaTeX$$ is beautiful.
It's probably half the reason I got into math and CS theory.
I use LaTeX everywhere I can.
I even had a double-space document class for my undergraduate liberal arts classes.
There's no way I could bear to have a blog (which I intend to be technical) without LaTeX.

[MathJax](http://www.mathjax.org/) is incredible.
It makes me almost amazed at the power of JavaScript.
Installing LaTeX normally takes a hefty amount of time due to all the packages, libraries, etc.
Somehow the MathJax team managed to condense a substantial portion into one script:

~~~
<script src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>
~~~

In my initial research online I saw a lot of warnings about difficulties with working MathJax into Markdown syntax.
Luckily (praise) the Kramdown engine in Jekyll makes everything easy.
In-line math is as simple as `$$x_1 \lt x_2 \leq x_3$$`, which produces $$x_1 \lt x_2 \leq x_3$$.
Display math involves simply putting the double dollar signs on their own line.
The following code

~~~
$$
x_1 \lt x_2 \leq x_3
$$
~~~

results in:

$$
x_1 \lt x_2 \leq x_3
$$

**Note:**
MathJax fails to display properly on mobile IE for Windows Phone.
If you are one of the few, you can remedy this by telling IE to view the desktop versions of sites using MathJax.
IE does not let you apply this setting for on a per-site basis, so I recommend setting up desktop mode on a different WP browser such as *UC Browser* and then using it when viewing MathJax sites.
Hopefully Edge will fix these woes.

### Pure CSS hamburger menu

What is a hamburger menu?
It's that $$\equiv$$ sign in the top-corner of mobile sites that stows away all the links that cannot fit on a small screen.
If you're reading this in a browser, resize it so you can see what I'm talking about.
Normally I'd be ranting about the terrible reachability/obscurity implications, but that post is saved for later.
My site includes a hamburger menu because it's conformist and exploring other options is too difficult (especially for a non-native app).

The default [Jekyll-new](https://github.com/jglovier/jekyll-new) theme provides a pure CSS hamburger menu that opens by *hovering*.
So unless you're using an ancient Blackberry click-ball or Microsoft's canceled McLaren phone, there's no way to navigate the site!
Changing the behavior to be click-based is not hard.
It's basically the Hello World program of jQuery:

~~~ javascript
$(document).ready(function(){
    $("#hamburger").click(function(){
        $("#ham-menu").toggle();
    });
});
~~~

Why go back to pure CSS?

*   Speed. One less HTTP call is one less millisecond.
*   Elegance. It's called *Pure* CSS for a reason.
*   Functionality. I actually had some trouble getting the jQuery to cooperate with the media-queries that were revealing/hiding the hamburger menu.
    Toggling off the menu in the hamburger meant that the menu would no longer appear when viewing the site in wide-screen.

The key to the pure CSS hamburger is to use a checkbox input.
It will store the state of the menu, which can be referenced via CSS.
The checkbox is hidden (because it looks nothing like a hamburger) and instead activated via a label.

~~~ html
<style>
.menu-toggle {
    display: none;
}
.menu-dropdown {
    display: none;
}
.menu-toggle:checked ~ .menu-dropdown {
    display: block;
}
</style>
<div>
    <label class="menu-icon" for="ham">
        <div></div>
        <div></div>
        <div></div>
    </label>
    <input type="checkbox" id="ham" class=".menu-toggle">
    <ul class="menu-dropdown">
        <li><a></a></li>
        <li><a></a></li>
        <li><a></a></li>
    </ul>
</div>

~~~

The approach is however limited.
There's nothing show-stopping, but a few things arise from CSS's limitations:

*   VimFx cannot see the menu icon.
    There are no links in the icon because they interfere with the checkbox, and the checkbox itself is hidden.
    Thus the icon evades the scanning of VimFx (and Vimium).
    This of course is not an issue if you only intend for your menu to be used on mobile.
*   The menu icon must be tapped again in order to collapse the menu.
    Ideally tapping on the article should switch the focus back.
    Mobile sites rarely have this feature but it is very common on native apps.
