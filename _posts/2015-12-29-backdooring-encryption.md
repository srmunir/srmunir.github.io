---
layout: post
title: "Backdooring encryption"
excerpt: >
    The "Freedom vs. Security" debate is alive and kicking again.
    The tech-world wants to ensure strong privacy for ordinary citizens, while the government wants the ability to break such privacy controls in the name of national security.
    Both sides have valid concerns.
    What sort of compromise can be achieved?
disqus_id: 50
---
It's election season in the United States.
Due to the unfortunate existence of terror groups like ISIS, national security is once again taking center stage in the debates.
A specific topic that has risen up in this broad security category is the question of whether or not we should have *backdoor encryption*.

I expect that everyone reading this is familiar with the said debate, but I'll quickly reiterate it here to establish a good basis.
Software companies are putting strong privacy controls into their communication apps.
In many instances (iMessage, WhatApps) these apps use end-to-end encryption, in which companies are unable to decrypt communications going through their own servers.
The government is unhappy about this.
Law enforcement wants to spy on the communications of suspected criminals/terrorists but cannot because the software makers say that even they cannot break their own protocols.
In response, members of the government (and some citizens too) are calling for tech companies to somehow "weaken" their privacy controls for surveillance purposes.

What can be done to meet the goals of both sides? Are they indeed inconsistent?
Let's try to formalize them first and imagine we were designing a secure chat application.

### Security goals

#### Threat analysis

We've got a trifecta of adversaries here:

1.  **Thieves** want to steal consumer data.
    They can range from novice to advanced.
    In addition to operating independently, they could reside in government or software developer.

2.  **Terrorists** want to communicate in secret about their terrorism plots.
    We must assume they lack an IT department capable of building its own secure chat app.
    It also needs to be assumed that terrorists have been identified so that warrants may be issued.
    (I strongly doubt that any popular chat applications have the anonymity controls to make this infeasible.)

3.  **Law-enforcement spies** want to conduct mass surveillance.
    Thanks to Edward Snowden, we know they will do so wherever they see an opportunity, disregarding laws/warrants.

#### Security requirements

The requirements for the secure chat application have been shouted all over the news and should be pretty obvious.
Software companies want:

1.  Innocent citizens
    Alice and Bob should be able to send messages with a maximal level of privacy.
    Thieves stay out and spies are limited by Constitution.
    State-of-the-art end-to-end encryption is needed.

The government demands:

2.  Terrorists should not be able to communicate online with secrecy.
    Alice and Bob might lose their lives instead of their credit card if intelligence agencies cannot read terrorist communications

#### Feasibility analysis

Here is where the debate starts.

Outsiders of the tech community don't write down the above threats/requirements.
They already believe the problem is feasible and have suggested all sorts of measures:

*   Have companies use encryption that can be brute-forced
*   Replace end-to-end encryption with a more HTTPS like system
*   Request that the government get special keys that unlock everything
*   Ban all strong cryptography from public use

It's easy to see the flaws in each of their proposals.
We can't blame them however because this is outside their expertise.
[Some][clinton-coop] realize this and are asking Silicon Valley for help.
What's the tech community's answer?
Every blog, Tweet, and Apple [CEO][tim-cook] is saying the same thing.

>   Nope. Infeasible. Zero compromise possible.
>   We're the experts.
>   Any system with a backdoor is an insecure system.

This really annoys me. (Am I reading the wrong articles?)
It seems like the people with the most applicable knowledge are giving the least amount of thought.
Cool research areas like predicate/functional encryption aren't even being entertained as possible future solutions.
The very idea of a backdoor is causing dismissal faster than a baby presented with broccoli.


### It's feasible

Yup.
Please challenge me where I go wrong.
I really just want to see a more in depth analysis in general.

For simplicity, this section will focus on Apple and iMessage.

***Backdoors already exist!***
The whole conversation of whether or not we should cripple iMessage's encryption all resides on the assumption that Apple has the ability to update iMessage on its phones.
Is this not a backdoor?
Tim Cook is acting like his hands are tied behind his back, and that's simply not true.
He has control over the entire iPhone, including the iMessage app.

Here's what Apple and the NSA can do with Apple's pre-existing backdoor without sacrificing security for innocent consumers:

1.  NSA identifies suspect.
    This can be done through all the usual investigation techniques and not mass-surveillance.

2.  NSA issues a warrant and shows warrant to Apple.
    This step is important because I'm writing from America.

3.  Apple receives warrant and agrees to comply.
    
4.  Apple pushes an individual update to the subject of the warrant's iMessage app.
    This update forces the app to use a NSA-issued encryption key for communications instead of whatever ephemeral or TPM key end-to-end encryption uses.

    Like any other update, this must be signed by Apple.
    Ideally it should also be installed when the phone is not typically in use so that the suspect is not alerted.
    (The update could instead easily be a signed command telling the app to enable backdoor, which would avoid interrupting the app's execution.
    However we want to make a point of using the update system.)

5.  Apple shares iMessage traffic with NSA. for the given user.

If you review the threats/requirements established earlier, the above steps comply with everything there.
To be fair however, I went out of my way to emphasize in the company's security requirement that "state-of-the-art *end-to-end encryption* is needed."
This is what weakened the requirement to allow the backdoor.
If I didn't want to compromise I would have said:

*   End-to-end encryption
*   Open source
*   Updates are delivered by pulling in new source code and recompiling

Ironically, the last two bullets are things Apple will never allow into its products.
The champion of the "zero compromise" attitude needs to quit pandering to libertarians and work to make the United States secure.



[clinton-coop]: http://www.engadget.com/2015/11/20/hillary-clinton-encryption-debate/
[tim-cook]: http://www.cbsnews.com/news/60-minutes-apple-tim-cook-charlie-rose/
