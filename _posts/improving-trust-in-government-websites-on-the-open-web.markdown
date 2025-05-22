---
layout: post
title:  "Improving trust in government websites on the open Web"
date:   2025-05-11 18:08:22 +0200
categories: open source
---

Impersonating governments is unfortunately a common scam on the internet. Scammers might do it to get people to pay bogus fines, to get some sensitive information, or sometimes even to sell access to otherwise free public services.

This can result in people being less trusting of goverment websites, while native apps can sometimes provide a better experience.

As an example, here's what it looks like to visit the website and the Play store pages for the French government service France Identités:
[screenshots of web page and play store page]

These screenshots are for an Android phone using Mozilla Firefox. Different phones ands browsers will have slight variations but I believe the core different between web pages and app stores will be the same.

It is true that the app store offers a more trustworthy interface for the end user: the app is labelled by Google as a government app, and the reviews on the app help making sure it's not a scam.

On the web however, any scammer can use the French government's design system, and there is little additional information provided to authenticate the website.

In turn, government can be discouraged from communicating with their citizens through the open web, and try to find channels of communications that are deemed more trustworthy, which could drive them to native apps rather than being on the open web.

I believe that it doesn't have to be this way, and that with a few simple design changes, we could make government websites and services easier to identify reliably on the open web, thus making them more trustworthy.

## Disclaimer

At this point, I should disclose that I do have a horse in this race, since I am working on a web app for the French government as an independent contractor. My work is open source and publicly available on my Github profile, as is the norm for the agency I work with. However, I am writing this article as a private citizen and open source contributor, on my own time. The ideas and opinions expressed here are my own, and are all based on publicly available information.

## URL conventions and limitations

Most national governments tend to publish websites and services using subdomains of their main domain, which is usually in a format similar to `.gov.uk`.
From a technical perspective, this is great because it is indeed very hard for scammers to spoof DNS. This URL pattern in cited as the best way to identify an official site on a page from the French government about spotting scammers(https://www.economie.gouv.fr/particuliers/faux-sites-administratifs).

For citizens with some level of tech savyness, this provides a reliable way of identifying them. But this is not enough, since governments need to communicate to every citizen, not just tech savy ones.
Let's face it, URLs are great for many things, but they're not easy to parse for humans.
Let's take the example of https://www.ncsc.gov.uk/collection/phishing-scams/spot-scams#section_1 : the most important part of this url, the `.gov.uk` is hidden in the middle, after all the dots and before the first forward slash.


This doesn't make it easy to spot, as Tim Berners-Lee himself famously says so in his [FAQ on the World Wide Web Consortium website](https://www.w3.org/People/Berners-Lee/FAQ.html#etc) :

> I have to say that now I regret that the syntax is so clumsy. I would like http://www.example.com/foo/bar/baz to be just written http:com/example/foo/bar/baz where the client would figure out that www.example.com existed and was the server to contact.


This also makes things more complicated on mobile, when the screen isn't wide enough to display more than the subdomain:
[screenshot of rendezvouspasseport.anct.gouv.fr]
On this legitimate government website, it is impossible to know at first glance if it is a scam or not.


This doesn't mean that we should try to hide urls, but just like they do for SSL certificates, browsers could explain the URL by highlighting the key parts in them.

As an example, here's how Firefox displays the url of a government site on the desktop :

[desktop screenshot of rendezvouspasseport.anct.gouv.fr]

Let's see what happens if we take that idea even further.

## Building upon URLs

Firefox already displays a padlock for websites using SSL properly, which is a good thing, but we could take it even further :
[insert 3 screenshots]

Here's how it would work :
- The browser would have a list of the different root domains used by national goverments
- When browsing a website using one of these domains or a subdomain, and proper SSL, the browser would display the generic goverment icon instead of the padlock
- By clicking on the icon, the usual menu would be displayed, with additionnal information about why this can be trusted as a government website.

These screenshots are just a first draft of what this feature could look like. I think it could be interesting to have the `.gouv.fr` part of the url in bold in the detailed menu, and the wording could probably be tweaked.

The nice part about this interface is that it explains rather than hides the complexity of the URL. It makes explicit the convention about gouvernment root domains, and hopefully it could even help people identify trustworthy government URLs outside of their browser address bar.


## What's next?

If you find this idea interesting, please feel free to participate in the conversation on the feature request for this on Mozilla Connect. I think that Mozilla Firefox is a great place to start implementing this, and then encourage other browsers to follow their lead.

If you're curious to see how it could be implemented, you can check out a proof of concept here on Github.
