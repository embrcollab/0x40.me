---
author:
  name: "Curriculum Vitae"
date: 2014-03-10
linktitle: About
title: 
type:
- post
- posts
weight: 10
series:
- poopernet
aliases:
- /blog/about/
---

## About me

Hi there,

My name is Cam.

Here's a stream of consciousness and a little about what lead me to IT.

I spent a lot of time doing very hard manual labour in some pretty average places, the best being a stint in a heat treatment plant. I was tasked, with my friend Tomas, to restore an old steel quenching furnace. This is the process of cooking steel at 900 degrees, and then dropping it into hot oil. You can imagine the factory - with 4 of them running 24/7 - being a hot, smokey place. The things I learnt were fun, lots of fabrication and gas plumbing, but holy moly was the place too hot.

I've always tinkered with computers, from building them at a young age, and then breaking them, only to fix them right up again. I started my first IT job just over a year ago and I realised then and there, exactly what I wanted to do.

Instead of standing next to hot furnaces trying to fasten a pipe, I get to manage a CentOS server in an air-conditioned office - stark difference!

I went into the job with a general understanding of some parts of IT, but exposing myself to a fleet of several hundred cPanel/WHM servers, allowed me to foster my passion, and gain skills in managing real infrastructure.

-----

Getting real world experience with Linux inspired me to try managing a server of my own, a cute little home lab. I've dabbled in spinning up Azure VM's, creating EC2 machines that do one thing for an hour and then gracefully disappear, reverse proxying everything and creating my own private networks, spanning all of Australia. I never thought I would spend so much of my time creating this projects, but it's why I love IT, and it's why I want to work in it forever. It changes fast and I love it.

-----

Now, about the domain.

`pooper.net.au`

I'm glad it was available, because it's silly enough to be rememberable. There's more DNS records attached to it than I would like to admit (did somebody say subdomain?). It has a link to every service I have running, everything private is kept behind SSO through Azure AD, that was a fun one to get up and running - seamless authentication is very satisfying.

Azure AD provides the authentication layer, NGINX passes an auth request to a [Vouch](https://github.com/vouch/vouch-proxy) container, that then passes the request the Azure App Registration. I can sign in with my Microsoft 365 account to most of my services. Linking my own ADDS Virtual Machine to Azure was also a nice touch, adding users to my domain that can also use my SSO stack allows for other privileged users (friends, maybe) to get access to the services.

Mixing the cloud into my infrastructure has opened my eyes to the possibility and power of modern service providers.

-----

The technology available consistently amazes me, I want to expose myself to everything, picking up as much as I can along the way, and using my Google-fu for the rest.

Linux and Windows CAN work together, you just need to tell them to play nice in a language they understand.

I've never been good at blogging, or writing, or anything that involves introspection, but talking about the tech comes easy.

Cheers :)

Thanks for reading.


