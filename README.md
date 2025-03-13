# Hosting the Fediverse: The Unexpected Lesson from SpaceHost

The best presentations _tell a story_ — this is a story of our journey **hosting the Fediverse** at [SpaceHost](https://spacehost.one):

* What we tried first.
* How & why that failed.
* How we solved the problem.
* And, an unexpected _invention_ that could _reshape the Social Web_.

If you care about the Fediverse, then _this is a story for you_.

<mark>NOTE: This article is a written adaptation of the presentation I delivered at the **Fediverse House** during **SXSW 2025**.</mark>

But — a story needs a _beginning_.
So, I will start with an _introduction_.

## Who Am I

<img src="charles-intro.png" style="width:400px;" />

I am **Charles Iliya Krempeaux**.

I have been a **product leader**, an **engineering leader**, and a **founder**.

But, let’s skip the long bio — here is _just one_ highlight from my career:

**I was one of the first engineers** at **Hootsuite**
—
a **social-media** company which at one time **the most popular Twitter app** in the world.
Over time, Hootsuite expanded to _also_ became a **Facebook**, **Google+**, **Instagram**, **LinkedIn**, **TikTok**, **YouTube**, **WhatsApp**, and _every other social-media platform_ app.
Everyone from
the U.S. White House,
to IBM,
to tens-of-millions of people all over the world,
and 80% of fortune 1,000 companies
have used the tool I created with others.

I have _been in Tech_ for **_more-than_ 30 years**.

And, from **engineering**, to **product**, to **enterprise**, and to **company** — I have **a lot** of **experience** with **social-media**.

## Me on the Fediverse

Some of you might know _me_ from …

<img src="reiver-mastodon-social.png" style="width:400px;" />

… The Fediverse!

This is my [`@reiver@mastodon.social`](https://mastodon.social/@reiver) account.

Where I talk **a lot** about — _you guessed it_ — **the Fediverse**.
I _also_ talk about — other **decentralized social-media** (**DeSo**) — including **Bluesky**, **Farcaster**, **Nostr**, and others.

And, I talk about **the Fediverse related projects** I work on, too.
For example…

## GreatApe

<img src="greatape-logo.png" style="width:200px;" />

… GreatApe!

**GreatApe** is a conversations platform for the Fediverse, and decentralized social-media.

<img src="greatape-screenshot.jpeg" style="width:400px;" />

Here is an _example_ of _myself_ and [`atomicpoet`](https://atomicpoet.org/@atomicpoet) (Chris Trottier) using GreatApe back in October 2023.

Here, we were using GreatApe to do a **live video podcast**.

Now, you don't see it in this image, but — we can also _invite_ people _watching_ in the _audience_ to _join the video conversation_.

## SpaceHost

<img src="spacehost.png" style="width:400px;" />

_Another thing_ some people _might know me from_ is — [SpaceHost](https://spacehost.one/).

And, for _this story_ — **SpaceHost** is probably the _more important thing_ —

As it _partially motivates_ what I am _soon_ going to show you.

## What Is SpaceHost

<img src="spacehost-2025.png" style="width:400px;" />

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

## What Crashes Fediverse Servers

We _learned_ a number of things from _our experience_ with hosting so many people’s _Fediverse servers_

Here is **_one thing_ we learned** —

We learned what _seems to be the **number 1 cause** of Fediverse servers crashing_ — including Mastodon, Misskey, Pixelfed, and every other type of Fediverse server.

Before you read what that is – guess to yourself what _you think_ it might be.

(**Scroll down once you have your guess.**)

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

**Caching**

And, in particular —

**The _storage drive_ of _Fedivere servers filling-up_ – due to _continued caching_**.

## Caching

Some of you might ask — 

* **What is being _cached_**?
* Some of you might even be ask, **what is _caching_**?

Those are both _good questions_ 🙂

**Caching** is a _technical term_ — in _computer science_, _computer hardware engineering_, and _software engineering_.

It (caching) basically means — **temporarily storing things**.

So, _what_ is being _temporarily stored_?

<img src="fediverse-caching.png" style="width:400px;" />

With _Fediverse servers_, they _temporarily store_ **user-data from other servers**.

* posts,
* media from posts,
* user-profile text,
* avatar images,
* header images,
* _and more_.

<img src="hard-problems-in-computer-programming.png" style="width:400px;" />

Now, _temporarily storing_ things (_caching_) is normal.

It (caching) is a _core technique_ with _computer programming_ & (other) _engineering_ –

Everything from **the CPU** to **the Web**, to **applications** all cache.
And, would _not_ work without caching.

So – _caching_ is _important_, _caching_ makes things _work_, but – _caching_ is a _difficult_ to _do well_.

So – it is _not_ surprising that _caching_ is _challenging_ for _Fediverse servers_ to do well.

## Round One

At SpaceHost we wrestled with this problem.

Should we _just automatically clear the cache_ for our customers?

Or, should we _tell them_ their _storage drive_ is filling up – and, _let them decide_.

The challenge is – _clearing the cache_ affects _user-experience_.
It can “break” search.
It can also "break" the home-feed.

So –

<img src="spacehost-email-alert.png" style="width:400px;" />

At first – we decided to just _e-mail_ our _customers_ to _tell them_ that _their storage drives_ were _filling-up_ and _let then decide_.

What we found-out was that –

**Most customers _seemed to never notice_ the _e-mail alert_ we sent them!**

In hindsight, that _was not_ a good strategy.

So –

## Round Two

This was a problem!

It created a _bad experience_.

Their server got _slow_.
And sometimes _crashed_.

It doesn't matter if we sent them an e-mail or not.
It wasn't being noticed.
And, they were _unhappy_.

Which made us unhappy.
We wanted to fix this.
So –

<img src="spacehost-chat-alert.png" style="width:400px;" />

We changed _our strategy_.

We started _automatically clearing_ our customers _caches_.

This is _better-than_ _servers crashing_, but – there is still a problem –

## Round Three

Search is _sort of_ _broken_ for them.

So –

<img src="search-server.png" style="width:400px;" />

We need to _separate_ **search** from the **back-end server**.

We need to make it so **accumulating user-data** doesn’t **crash** the **back-end**. 

In fact – multiple **back-end servers** could **share** the same **search server** to _reduce costs_.

We also need a **_Fediverse API_ for _search_**.

Here is the thing – **we already built a lot of it**.

We started working on this back in August 2024.

In fact – we start working on **search** plus **custom feeds** back in August 2024.

I didn’t mentioned **custom feeds** yet, but I am mentioning it now.

But back to **search** –

## RobinLive

Because no **Fediverse software** uses this **search API** yet –

We created a **real-time search-engine** so you can see it _in action_.

<img src="robinlive-example.png" style="width:400px;" />

You can try it for yourself at:

https://robin.live/

## Decentralized Search

<img src="decentralize-all-the-things.png" alt="Decentralize All The Things" style="width:400px;" />

Now, although [RobinLive](https://robin.live/) exists –

The idea is that there would be _multiple_ **search servers**.

And, not just RobinLive.

That is right – **let's decentralize them**.
**Let's decentralized search**.

RobinLive will be _one of many_.

## DeSo Search

<img src="robinlive-deso-search.png" style="width:400px;" />

If you were looking closely at the _previous_ RobinLive screen, you might have noticed that – in addition to showing results from the Fediverse – we were also showing results from Bluesky.

We on the Fediverse have more in common with those on _other decentralized social-networks_ than the _centralized ones_.
I don't think we are enemies.
I think we are all fellow-travelers.
We are all reacting to the same problems (with the Internet, the Web, and social-media) in a similar way — we are just choosing different technologies.

I have my own opinions about the Tech.
I have my own preferences.
But –

I want **the user** to **_not_ have to care about** _these differences_.

## All The DeSo Networks

I think [Danielle Foré](https://mastodon.online/@danirabbit) said it best –

When talking about **the Fediverse** – she didn’t say "_decentralized_", or "_open-source_", or "_server_", or even mention "_e-mail_".
She just said – you can _follow anyone_ from ANY _social-network_.

**I want to make that __as true__ as I can.**

Thus – users **should not care** about _the differences between_ – the Fediverse, Bluesky, Nostr, and others.

---

<mark>**Thank you** **Evan Prodromou** for letting me present at the **Developer Meetup** at the **Fediverse House** at **SXSW 2025**.</mark>
