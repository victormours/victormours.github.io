---
layout: post
title:  "Making government URLs easier to understand on the open Web"
date:   2025-05-11 18:08:22 +0200
categories: open source
---

# Making government URLs easier to understand on the open Web

## The issue

On its official website, the French Government gives a clear way to determine wether or not you're looking at an official and trustworthy website: look for the ".gouv.fr" at the end of the domain name in the URL.

Lots of other countries have similar policies: the USA have .gov, Algeria has .gov.dz, India has .gov.in, and so on and so forth.

Impersonating governments is an efficient strategy for scammers, whether it is to sell access to a service that would normally be free, or by posing as the government asking for a fine.

For governments, the issue becomes how do we communicate with our citizens without being mistaken for scammers?

Domain names are a sensible solution, but they are seriously flawed, especially on mobile. For example, can you tell if this French website is legitimate?

[Insert screenshot of Rendez-vous passeport]

You can't, because the subdomain is long enough that the end of the domain with the .gouv.fr is not visible without selecting the url and scrolling to the right.

And to non-tech savy people, knowing how to parse a url to identify the top level domain name is impossible.

Some goverment agencies may turn to native mobile apps. On the Google Play Store for instance, government apps are clearly marked as such. [Insert Screenshot of France Identité on the Play Store].

But it doesn't have to be this way. After all, this is a simple design problem that has been solved elsewhere.


## A possible step forward

Here's what clearly identified official government sites might look like:
[3 screenshots]


This design builds upon what Firefox already does to show wether or not a connection is "secured" (meaning that it uses SSL).

It also builds upon URLs and how they are already used by making explicit the implicit knowledge that `.gouv.fr` is a website by the French government.

## FAQ

How would this be implemented?
- This would mean maintaining a list of countries and the domain names used by their government.

Should browsers cater to governments?
- This feature is in service of the citizens that need to be able to cldearly identify their communication with their government. I hope that this simple implementation would not lead to government agencies to pressure open source software developers. I believe that the open web and goverments for the people by the people are natural partners.
Full disclosure : I work as an independent contractor for the French government. My work for the government is open source and available on my Github profile. I am writing this proposal as a private citizen and a supporter of the open web.

How about local government?
- Maintaining a list of local govermnments does not seems feasible. This should only be for national governments.

What list of countries should we use?
- The question of what qualifies as a country can be a fraught one in some cases, and I am certainly not qualified to answer. However, I believe it is worth erring towards including rather than excluding the debated cases.
