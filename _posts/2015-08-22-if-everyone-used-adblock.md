---
layout: post
title: "If everyone used adblock"
excerpt: >
    Using adblock is almost a no-brain decision these days.
    What would happen to the Internet if all web-surfers realized its greatness?
    How can the companies that depend on advertising respond?
disqus_id: 30
---
Using adblock is almost a no-brain decision these days.
It does so much to improve the web-surfing experience of browsers:

*   First and foremost: adblock blocks ads and uncovers content.
    Many websites (almost all news sites) today are rendered unreadable due to ads.
    They interrupt your navigation telling you to "Click to continue", inflate across the whole browser when you accidentally hover over them, scream noise at you in a video player with a broken mute button, randomly collapse/expand, etc.
    Their goal is to steal your focus and put it on their product.
    Your goal is to read the headlines, so you install adblock.

*   Adblock gives you speed.
    Not surprisingly, making 50 less HTTP calls does allow a page to load faster.
    Not being forced to watch the same movie trailer for the 16th time means you don't have to wait for it to buffer for the 16th time too.
    There's not a single ad in the world that speeds up a webpage.
    Installing adblock is cheaper than getting more bandwidth from an ISP.

*   Security.
    Suppose you want to watch a sports game, but you can't find it in your cable subscription because none of the teams playing are local.
    There are some (very illegal) sites which allow you to (illegally) stream such games.
    These (deplorable) sites are supported by advertisers whose morals are often even lower.
    You might be smart enough to dodge their phishing attempts, but your browser will left all alone to fight off whatever malicious code is present.
    If you install adblock and navigate to one of these dirty corners of the web (for security research purposes), you're likely to come out unscathed.
    Since middle school I've been using adblock on regularly updated Windows (without the Norton virus).
    During this time I've never gotten a virus from web-browsing.
    (Of course, this is more due to the fact that I've *never* done anything illegal on the Internet.)

Given how overwhelmingly beneficial adblock is to web-browsing, I'm stunned at how often I find people who don't have it.
<!-- I guess it's not being advertised enough. -->
Somehow the same inexplicable forces keeping IE7 at a significant market share are suppressing adblock's popularity too.
However, I don't believe we'll this is a permanent fate.
Adblock will eventually achieve prevalence.
One of the following things will happen:

1.  Adblock continues to naturally grow in popularity.
    Eventually it reaches some critical point where a media outlet decides to run the story: "Could this free program bring down Google?"
    Boom! CNN, ABC, NBC, and CCTV find their pundits and scream it in everyone's ears.
    Maybe this is a bit too dramatic, but this is the media.

2.  A major browser builds in adblock to an update.
    Could this really happen? Definitely.
    This is how we eradicated pop-ups.
    Mozilla and Microsoft are already pushing Do Not Track into their browsers (with Google reluctantly following).
    Going from DNT to a basic adblock is a tiny jump.
    Firefox already [did it accidentally][accident] in their beta.
    Additionally, almost all browsers now feature a Reading Mode which oblitherates all parts of a website except the exact content to be read.

After that lengthy introduction we can finally raise the question:
How does the Internet respond if everyone uses adblock?
Ask this to someone, and their first thoughts will seem dismal:

>   Google is doomed.
>   The Internet relies on ads. Half of it can't survive with adblock.
>   The only things left would all cost money!

This is quite reasonable to think.
Most sites are simply never going to be worth a $5/month subscription or a Wikipedia-like fund-raiser; ads are essential to survival.
A recent New York Times [article][wrong-times] offers a less alarmist point of view:

>   If blocking becomes widespread, the ad industry will be pushed to produce ads that are simpler, less invasive and far more transparent about the way they’re handling our data

In order to agree with NYT, you must believe that the Internet will surrender to a less effective means of funding.
I do not see that happening.
The Internet doesn't have its back against a wall; it's standing in front of a bookshelf.
Adblock has weaknesses. It cannot call the shots.
In the rest of this post we'll look at some ways for content providers to circumvent adblock without losing their funding or going to paid tiers.
Many of the methods may seem obvious and almost all are already in the wild today.

### Adblock detection

Adblock detection most immediate fix to the adblock problem today.
Simply detect the use of adblock and deny serving any content if it's there.
Most users will cave in and allow the ads.
Hulu is a great example of this.

Adblock detection is not a long-term solution however.
Most of the detectors work by using a [canary in a coal mine][sentinel] approach:
Attempt to load something disguised to look like an ad and then check to see if it actually loaded.
This is an easily beatable strategy though.
An adblocker can just load a full webpage with ads in the background and only display the filtered contents to the user.
The adblocker loses the speed advantage we praised earlier, but it makes this blog-post a more worthwhile read.

### Apps

<!-- This first method might be the most prevalent solution. -->
Simply stated: There are no extensions for mobile apps, and therefore there is no adblock to worry about.
Developers decide exactly what is displayed in their apps.
Need an ad for funding? Done. There's nothing in the way.

Desktops are on the decline.
People love their phones, tablets, and all the apps on them.
Given a choice between a mobile website and a native app, everyone goes to the app.
Any speed and security that can be gained by using adblock in a browser is just outclassed by switching to native.
(Most mobile browsers don't even support extensions yet.)
Advertising from within apps is often enough to completely fund a company.
Some companies completely forgo having a web-app at all:
The average startup website is just a useless cookie-cutter jumbotron that links to its iOS and Android apps.

In the case of Google, Android can be seen as one giant app.
The Google Play phones are a direct connection to Google without any filters or blockers.
They can serve ads in searches and suggest restaurants in Google Now with ease.
Additionally, they get a cut out of all the ads running through their services on apps in the phone.

The app solution is far from perfect.
It is much cheaper to make a single web-app than to build/publish separate native apps on iOS, Android, Windows, OS X, Linux, etc.
For some business, it fundamentally doesn't make sense to have only native apps.
News sites and blogs need URLs in order to be shared and spread.
There is no equivalent to a hyperlink for apps.
The web needs solutions too.

<!--
### Subscriptions and donations

This is the least interesting of the proposals, so I don't feel too bad if you skip ahead.
We should start off by fixing the definition of donation: A donation is a gift of money with no intention to bias or own a product.
If we don't say this, it can be argued that advertising or subscribing are forms of donation.

Donations aren't for every site, but they're not as bad of an option as many think.
People do donate.
Before the advent of "Acceptable Ads", Adblock Pro used to be wholly funded via PayPal.
(This is still true for the majority of other browser extensions.)
Wikipedia, a top 10 most visited site in the world, runs off of donations with zero advertisements.
People on Kickstarter provided $55,000 to fund a [potato salad][potato]!

The concept of *micropayments* is also starting to gain traction.
Micropayments aren't meant to fund large efforts, but instead can be seen as tipping the Internet.
Bloggers could add a PayPal button right next to the sharing icons for their posts.
Hosting a static website could easily be covered by small $0.50 payments here and there.
If you doubt that people would ever do such tipping on the Internet, watch a [Twitch](http://www.twitch.tv/) stream.
Bitcoin and other cryptocurrencies are also great candidates for micropayments (which is the real reason this whole section exists).
-->

### Native advertising

Watch this [clip][john-oliver]. It's a good laugh, and you deserve it after all my wordiness so far.

Nowadays it's very common for news agencies to have sponsored articles (a.k.a. native advertising).
These are stories whose content is biased to the views of a paying sponsor.
Native advertising can be very effective. People read biased stories and then believe that they can make an informed decision afterwards.
This is so much the case that consumer protection laws require such articles to be labeled "sponsored."

Again assuming a perfectly law-abiding society, an adblocker can easily detect stories with "sponsored" tags.
What can it do with them?
The content is the ad! The whole webpage would have to be hidden.
To make matters worse remove the law-abiding assuming (to include most of the media).
Lacking labels, now we have to use non-existent advanced NLP to figure out if we're in the same conundrum.
The adblocker is powerless.

Google let's a small fraction of its search results be sponsored and labels them as such.
One could expect that adblock could win in this type of situation by blocking the sponsored links and still leaving plenty of content behind.
That's not the case.
Google has offshore account; it knows how to use loopholes.
Why not just do something to the effect of labeling everything as an ad?
Say their sorting is the function of relevance and amount paid.
All of a sudden adblock needs its NLP oracle again.

### CAPTCHA ads

I saved the greatest evil for last.

CAPTCHA advertisements function exactly as you would expect them to.
Take an ordinary CAPTCHA, replace the obfuscated text with a banner ad, and set the challenge to be something of the sort: "How much money could you save by switching to Geico?"
Block access to a piece of content until the correct response to the challenge is given.

Just like a regular CAPTCHA, unless there is a huge advancement in AI, only a human can complete the challenge.
The user must *study* the ad, find the message the sponsor wants to get across, and *repeat* the message back to the ad.
Instead of having the option to hide or look away from them, users are forced to pay attention to the ads they despise.
It's the most effective form of advertising possible without knocking on someone's door.
Adblock is powerless.

The wickedness doesn't stop there though.
Advertisers can set their challenges such that users must actually click on their ad and enter their site in order to find the answers.
This is a 100% click-through rate!
Advertisers and websites are going to win big while consumers get a middle finger on their computer screen.

Don't blame me if CAPTCHA ads become widespread.
I'm not the only one to have thought of them.
There [are](http://www.nlpcaptcha.in/en/index.html) [already](http://www.adaptcha.com/) [companies](http://solvemedia.com/) out there with CAPTCHA ad platforms.
None of them are as big-name as Google or Facebook yet, and they're also not nearly as exploitive as what we've discussed above.
However they are waiting. The infrastructure is there.
If adblock pushes the Internet to these companies, we're in trouble.

### Conclusion

I don't feel guilty about using adblock.
In the short-term, it makes life wonderful.
In the long-term, the Internet will be content with it too.
Go out and download adblock. Join me in continuing the fun thought experiment on how to break it.


[accident]: http://www.geek.com/apps/mozilla-just-built-an-ad-blocker-into-firefox-1631245/
[john-oliver]: https://www.youtube.com/watch?v=E_F5GxCwizc
[potato]: https://www.kickstarter.com/projects/zackdangerbrown/potato-salad
[sentinel]: https://en.wikipedia.org/wiki/Animal_sentinel
[simple-detect]: http://stackoverflow.com/questions/4869154/how-to-detect-adblock-on-my-website
[wrong-times]: http://www.nytimes.com/2015/08/20/technology/personaltech/ad-blockers-and-the-nuisance-at-the-heart-of-the-modern-web.html
