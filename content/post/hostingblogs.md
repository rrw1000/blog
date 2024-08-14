+++
author = "rrw"
title = "Hosting blogs"
date = "2024-08-13"
description = "Hosting this blog"
tags = [ ]
weight = "2"
+++

So, I've used a bunch of blogging platforms over the years, and not
really liked most of them.

I used to host a website for software I'd written and my CV, but that
got overtaken by [github.com](https://github.com/rrw1000) quite a
while back, and it seemed like now was a good time to self-host.

[hugo](https://gohugo.io) seems worthy and so this site is developed
in it, by hacking the texify 2 theme to do a little more of what I
want - in particular, I prefer monospace to serif fonts.

The [CL-EM-SE supervision site](https://sup.rrw.me.uk/) runs on
[fly.io](https://fly.io) via GHCR GHAs
(https://github.com/rrw1000/wikijs-sup) .

So, now seems like a good time to look at hosting options:

 * Do it myself: would work (I have a VPS via [Mythic
   beasts](https://www.mythic-beasts.com/), who I strongly recommend),
   but it's a larger attack surface for that VPS, hosting containers
   is memory intensive, and TLS renewal is kinda tedious.

 * Cloud providers are kinda like fly.io, but more expensive, harder
   to work with, and slower. Unless you really enjoy spending your
   money on enterprise devops, just don't (at any scale these days,
   really).

 * [https://www.shuttle.rs/](https://www.shuttle.rs/) - nice, but this
   isn't a rust service and it seems like overkill to write one just
   for this (read: I'd enjoy it, but I have lecture notes to read ..)

 * Various others ([nhost.io](https://nhost.io)] who look vaguely
   interesting.

 * [fly.io](https://fly.io) and [render.com](https:://render.com) both
   seem to come decently recommended, so let's try render since I
   already have a service running on fly (who, btw, were always pretty
   good and do seem to be making quite a lot of progress -
   https://fly.io/blog/ is a good read, in the main)

This turns out to be moderately nifty - render is trying to be heroku
fairly hard, but does (ultimately) support IAC via
[blueprints](https://docs.render.com/blueprint-spec), and the trick of
putting a `render.yaml` in the same repo you're trying to ship seems
to work fine.

That said, both fly and render tend towards k8s as deployments get
more complex; I can't help thinking that this is a problem with the
way we write software rather than a problem with k8s - we end up
building more and more complex mechanisms for diminishing benefit
until we end up with something very marginally better than the last
thing in return for a great deal more effort.

But more of that in a future post ...
