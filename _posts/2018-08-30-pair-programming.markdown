---
layout: epic
title: "The Hows and Whys of Pair Programming"
date: 2018-08-30
author: [yuki, orta]
categories: [pairing, culture]
---

Why pair program? As new engineers join Artsy we've been experimenting with different programming cultures - Yuki
came from Pivotal Labs where they have a strong pair programming culture and introduced it at Artsy - it's been
about a year and a half and we're all really loving the changes he's introduced.

I asked Yuki if he'd pair program with me on a blog, post on Pair Programming, and this is it. So, we're going to
dive into what pair programming is, why you should do it, what are good mental models to think about, the techniques
you can use to make it work, what hardware you might need and how Yuki persuaded so many of us to start doing it
more often.

<!-- more -->

## Why pair program?

<!-- - Insta-reviewing cycles, co-reviewing is basic idea -->
<!-- - A brief history of pairing? -->

The idea of pair programming came from a very popular book called [Extreme Programming Explained: Embrace
Change][extreme-explained]. Code reviewing has been a good practice in software development. Many organizations have
adopted it, but XP (Extreme Programming) literally takes this **more extremely** - what if the engineer sitting next
to you is reviewing your code as soon as you write it? This requires two engineers to simultaneously pay attention
to the code that's being written, discuss implementation details, and sometimes socialize. That's how pair
programming was born.

Pair programming seems as easy as it sounds, and to some extent that's true. However, with just a few key points
you'll be able to make your pairing session much more valuable.

<!-- - Using for Teaching/Learning -->

To think about when pairing is most valuable, let's think about code review first. Modern software organizations
have implemented a process where engineers send pull requests to get reviews on GitHub (or whatever tool your
organization uses for reviewing code). This is a very powerful process, but most of us have probably experienced a
situation where a pull request with a very simple change created a very long discussion. Sometimes
that's because of your lack of context in the work you are doing. Sometimes it's because you are working on a
system you are unfamiliar with. Your co-worker left a lot of comments on your pull request, and you had to push a lot of extra commits, or even re-wrote the entire pull request. That's when pairing becomes most valuable to your team.

I joined Artsy back in February 2017. Coming from an agile consustancy and a photo-product company, I was nowhere close to an Art expert when I actually started working here. This was the time I wanted to question not just technical questions, but also general questions about the art industry. How do people find and purchase artworks? Who actually sells artworks? What is an art fair? And auctions? On the other hand, Christina Thompson, also a software engineer at Artsy, had been at Artsy for more than two years.

<!-- wrire more about my first experience on pairing at Artsy -->

### When not to pair program?

While pairing is a useful tool, it's not the silver bullet we can utilize to solve all software problems. As explained
above, pair programming originals from the culture of code review. As complex, long-standing pull requests exist,
there are also simple changes that don't require a lot of disucssions. Occasionally, your pull request is very long with a
full of deprecated method names, or you

- Do we do it as much as we'd want?

<!-- - Value in productivity -->

- Mental model
  - Remind your pair of what to work on
  - Speak up while pairing
  - Take breaks often
  - Show appreciation

* Techniques

  - driver and navigator
  - ping-pong pairing

<!-- - What companies provides a good best examples? -->

## What You'll Need to Pair Program

The minimum you need is a computer and the ability to communicate, but let's look at what an optimal pair
programming setup looks like.

### Offline

If you can have physical access to the other engineer, then you should aim to have:

- One computer set up as a workstation.
- Two sets of keyboards, mice and monitors attached.
- A spare computer for researching on the side.

This gives you the ability to iterate and switch responsibilities at the speed of thought. If you have the resources
and space, then setting up a place where any 2 engineers can drop a laptop down and be productive instantly will
reduce a lot of the setup friction.

### Remote

The minimum you would need in this case is a video chat system like Skype, Google Hangouts or Slack Calls. Given
that all of these support screen sharing too, then you can easily replicate two people sitting next to each other
with one computer.

It's worth noting that remote pairing requires stable internet, and with high bandwidth. We've both had situations
in the past where we've had to abort pairing sessions due to internet un-reliability.

We used to use ScreenHero a lot, to support multiple mice and keyboards, but [ScreenHero was bought by slack][sh]
and that feature still isn't available for everyone. So, a lot of our pairing is done via screen sharing.

There's a newcomer to the scene though, [VS Code's LiveShare][ls] gives you the ability to share an IDE, do voice
chat, server ports and terminal sessions with a very low amount of setup. We wrote the initial draft of this post
in-person, in aN Artsy meeting room writing and talking in real-time. If you've not seen Live Share, we posted a
video of a [workshop we ran][ls-yt] at Artsy on YouTube.

If you're looking to find more resources on pair programming, Joe Moore's: [Remote Pair Programming][rpp] is a great
place to start. He's been working at Pivotal Labs for over a decade.

### Attribution

One way to encourage pair programming is by providing insight to others about when you're working as a pair. A great
technique for this is to use [`git-standup`][git-standup].

<!-- on TLDR git stand -->

<!--

- Hardware
  - assume offline next to each other (2 keyboards, 2 mice, 2 monitors, 1 computer)
  - optional things (extra computer for researching etc)

* Remote
  - Hardware (headset, iPad, network bandwidth)
  - online, screensharing
  - (briefly mention live share)
  - Tips: http://remotepairprogramming.com/ -->

- Ways in which you can encourage more pairing?
  - Techniques for introducing it into your team
  - Good resources? Further reading

* not sure where they should go

[extreme-explained]: https://www.goodreads.com/book/show/67833.Extreme_Programming_Explained
[sh]: https://slack.com/screenhero
[ls]: https://visualstudio.microsoft.com/services/live-share
[ls-yt]: https://twitter.com/ArtsyOpenSource/status/1034555778210910209
[rpp]: http://remotepairprogramming.com/
[git-standup]: https://github.com/kamranahmedse/git-standup

Notes:

- http://www.extremeprogramming.org/rules/pair.html
