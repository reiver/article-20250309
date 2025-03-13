# A Lesson Learned From Hosting The Fediverse: A SpaceHost Story

NOTE: This article is a written adaptation of the presentation I delivered at the **Fediverse House** during **SXSW 2025**.

Hello everyone.

I only have **15 minutes** for _this presentation_ (including questions) —  so, let's get started.

**Thank you** for attending the **Developer Meetup** at the **Fediverse House** at **SXSW 2025**.

And, thank you **Evan Prodromou** for letting me present.

-----

I think — most _good_ presentations _tell a story_.
So, I am going to _tell a story_.

This is an **exciting story** about —

Our experience with **hosting the Fediverse** at [SpaceHost](https://spacehost.one/).

* What we first tried.
* How & why that failed.
* How we solved this problem.
* And, how we are going to solve this _even better_.

If **you** _care_ about the Fediverse, then – **this is _a story for you_**.

But — a story needs a _beginning_.

So, I will start with an _introduction_.

-----

I am Charles Iliya Krempeaux.

I have been:

* a **product** leader,
* an **engineering** leader, and
* a **founder**.

Because we a short on time – _here is_ just one _highlight_ from my career:

I was **one of the first engineers** at the **social-media** company **Hootsuite**.
Hootsuite was at one time **the most popular Twitter app** in the world.
Later, it _also_ became a Facebook, Instagram, Google+, YouTube, LinkedIn, and everything else social-media app.

I have _been in Tech_ for — a long time.
Depending on _how you count it_ — _more-than_ 30 years.
And, I have **a lot** of **experience** with **social-media** from an **engineering**, **product**, **enterprise**, and **company** point-of-view.

-----

_Some of you_ might know _me_ from …

-----

… The Fediverse!

This is my `@reiver@mastodon.social` account

Where I talk **a lot** about:

(...you guessed it…)

* **The Fediverse**

I ALSO talk about:

* other **decentralized social-media**

And, I talk about **the Fediverse related projects** I work on, too.

For example…

-----

… GreatApe!

**GreatApe** is a conversations platform for the Fediverse, and decentralized social-media.

-----

Here is an _example_ of _myself_ and `atomicpoet` (Chris Trottier) using Great Ape back in October 2023.

Here, we were using GreatApe to do a **live video podcast**.

Now, you don't see it in this image, but —

We can also _invite_ people _watching_ in the _audience_ to _join the video conversation_.

-----

_Another thing_ some people _might know me from_ is — [SpaceHost](https://spacehost.one/).

And, for _this story_ — **SpaceHost** is probably the _more important thing_ —

As it _partially motivates_ what I am _soon_ going to show you.

-----

**But, what is SpaceHost** —

We need to know this for the story.

**What is SpaceHost** —

To _regular people_, I tend to **describe SpaceHost as** —

> **SpaceHost is an _app-directory_ for the _Fediverse_**

Or maybe –-

> **SpaceHost is an _app-directory_ for the _decentralized social-media_**

To people who are a little more _tech savvy_ — I might describe SpaceHost as —

> **SpaceHost is _fully-managed hosting_ for _all the Fediverse_**

As far as I know –

* SpaceHost was **the second hosting-company in the Fediverse**, after Masto.Host, and
* SpaceHost is **the first hosting-company in the Fediverse to _try to_ offer _all the (other) Fediverse software other than Mastodon_** –  although, we _also offer Mastodon_.

-----

We _learned_ a number of things from _our experience_ with hosting so many people’s _Fediverse servers_

Here is **_one thing_ we learned** —

-----

We learned what _seems to be the **number 1 cause** of Fediverse servers crashing_.

Before you read what that is – take a guess at what you think it might be.
(Scroll down once you have your answer.)

.

.

.

.

.

.

.

.

.

.


Here is the answer —

**caching**

And, in particular —

**The _storage drive_ of _Fedivere servers filling-up_ – due to _continued caching_**.

-----

Some of you might ask — 

* What is being CACHED?
* Some of you might even be ask, WHAT IS CACHING?

Those are both _good questions_ 🙂

**Caching** is a _technical term_ — in _computer science_, _computer hardware engineering_, and _software engineering_.
It basically means — **temporarily storing things**.

So _what_ is being _temporarily stored_?

-----

With _Fediverse servers_, they _temporarily store_ **user-data from other servers**.

* posts,
* media from posts,
* user-profile text,
* avatar images,
* header images,
* _and more_.

Now, _temporarily storing_ things (_caching_) is normal.

It is a _core technique_ with _computer programming_ & (other) _engineering_ –

Everything from **the CPU** to **the Web**, to **applications** all cache.
And, would _not_ work without caching.

So –

* _caching_ is _important_.
* _caching_ makes things _work_.

But –

* _caching_ is a _difficult_ to _do well_.

So – it is _not_ surprising that _caching_ is _challenging_ for _Fediverse servers_ to do well.

-----

At SpaceHost we wrestled with this problem.

Should we _just automatically clear the cache_ for our customers?

Or, should we _tell them_ their _storage drive_ is filling up – and, _let them decide_.

The challenge is – _clearing the cache_ affects _user-experience_.
It can “break” search.
It can "break" the home-feed.

So –

-----

At first – we decided to just _e-mail_ our _customers_ to _tell them_ that _their storage drives_ were _filling-up_ and _let then decide_.

What we found-out was that –

Most customers _seemed to never notice_ the _e-mail_ we sent them.

In hindsight, that _was not_ a good strategy.

So –

-----

This was a problem!

It created a _ba experience_.

Their server got SLOW.
And sometimes crashed.

It doesn't matter if we sent them an e-mail or not.
It wasn't being noticed.
And, they were _unhappy_.

Which made me unhappy.
So –

-----

We changed _our strategy_.

We started _automatically clearing_ our customers _caches_.

This is _better-than_ _servers crashing_, but – there is still a problem –

-----

Search is _sort of_ _broken_ for them.

So –

-----

We need to _separate_ **search** from the **back-end server**.

We need to make it so **accumulating user-data** doesn’t **crash** the **back-end**. 

In fact – multiple **back-end servers** could **share** the same **search server** to _reduce costs_.

We also need a **_Fediverse API_ for _search_**.

Here is the thing – **we already built a lot of it**.

-----

We started working on this back in August 2024.

In fact – we start working on **search** plus **custom feeds** back in AUGUST 2024.

I didn’t mentioned **custom feeds** yet, BUT I am mentioning it now.

But back to **search** –

Because no **Fediverse software** uses this **search API** yet –

We created a **real-time search-engine** so you can see it _in action_.


You can try it for yourself at:

https://robin.live/

-----

Now, although RobinLive (https://robin.live/) exists –

The idea is that there would be _multiple **search servers**.

And, not just RobinLive.

That is right – **let's decentralize them**.

RobinLive will be _one of many_.

-----

If you were looking closely at the _previous_ RobinLive screen, you might have noticed that – in addition to showing results from the Fediverse – we were also showing results from Bluesky.

We on the Fediverse have more in common with those on _other decentralized social-networks_ than the _centralized ones_.
I don't think we are enemies.
I think we are all fellow-travelers.
We are all reacting to the same problems (with the Internet, the Web, and social-media) in a similar way — We are just choosing different technologies.

I have my own opinions about the Tech.
I have my own preferences.
But –

I want **the user** to **_not_ have to care about** _these differences_.
