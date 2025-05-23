---
layout: post
title:  "Improving trust in government websites on the open Web"
date:   2025-05-11 18:08:22 +0200
categories:
---

Impersonating governments is unfortunately a common scam on the internet. Scammers might do it to get people to pay bogus fines, get some sensitive personal information, or even to sell access to otherwise free public services.

It is currently a rather easy scam to run: all they need to do is to set up a website that re-uses the design system of the government they're imitating, host it with a somewhat official-sounding domain name, and they're good to go. These sites might eventually be taken down or added to the [Safe Browsing](https://safebrowsing.google.com/) blocklist, but they can still do some damage.

This can result in people being less trusting of government websites, and some official communication being misunderstood as phishing attempts.

In turn, governments can be discouraged from communicating with their citizens through the open web, and try to find channels of communications that are deemed more trustworthy.

On the other hand, native mobile apps can sometimes provide more security.

As an example, here's what the website and the Play store pages for the French government service France Identités look like:
[screenshots of web page and play store page]

These screenshots are for an Android phone using Mozilla Firefox. Different phones and browsers will have slight variations but the main differences between web pages and app stores will be the same.

The app store does offer a more trustworthy interface for the end user: the app is labelled by Google as a government app, and the reviews on the app help make sure it's not a scam.

I believe that it doesn't have to be this way, and that with a few simple design changes, we could make government websites and services easier to identify reliably on the open web, thus making them more trustworthy.

## Disclaimer

At this point, I should disclose that I do have a horse in this race, since I am working on a web app for the French government as an independent contractor. My work is open source and publicly available on my Github profile, as is the norm for the agency I work with. However, I am writing this article as a private citizen and open source contributor, on my own time. The ideas and opinions expressed here are my own, and are all based on publicly available information.

## URL conventions and limitations

Most national governments tend to publish websites and services using subdomains of their main domain, which is usually in a format similar to `.gov.uk`.
From a technical perspective, this is great because it is indeed very hard for scammers to spoof DNS. This URL pattern is even cited as the best way to identify an official site on a [page from the French government about spotting scammers](https://www.economie.gouv.fr/particuliers/faux-sites-administratifs).

For citizens with some level of tech savvyness, this provides a reliable way of identifying official websites. But this is not enough, since governments need to communicate to every citizen, not just tech savvy ones. URLs are great for many things, but they're not easy to parse for most humans.

Let's take the example of `https://www.ncsc.gov.uk/collection/phishing-scams/spot-scams` : the most important part of this url, the `.gov.uk` is hidden in the middle, after all the dots and before the first forward slash.

This doesn't make it easy to spot, as Tim Berners-Lee himself famously says in his [FAQ on the World Wide Web Consortium website](https://www.w3.org/People/Berners-Lee/FAQ.html#etc) :

> I have to say that now I regret that the syntax is so clumsy. I would like http://www.example.com/foo/bar/baz to be just written http:com/example/foo/bar/baz where the client would figure out that www.example.com existed and was the server to contact.


This also makes things more complicated on mobile, when the screen isn't wide enough to display more than the subdomain:
[screenshot of rendezvouspasseport.anct.gouv.fr]

On this legitimate government website, it is impossible to know at first glance if it is a scam or not.

This doesn't mean that we should try to hide urls, but just like they do for SSL certificates, browsers could explain the URL by highlighting the key parts in them.

As an example, here's how Firefox displays the url of a government site on the desktop:

[desktop screenshot of rendezvouspasseport.anct.gouv.fr]

How about we take this idea even further?

## Building upon URLs

Firefox already displays a padlock for websites using SSL properly, which is a good thing, but here's what going the extra mile could look like:
[insert 3 screenshots]

Here's how it would work :
- The browser would have a list of the different root domains used by national governments
- When browsing a website using one of these domains or a subdomain, and proper SSL, the browser would display the generic government icon instead of the padlock
- By clicking on the icon, the usual menu would be displayed, with additional information about why this can be trusted as a government website.

These screenshots are just a first draft of what this feature could look like. I think it could be interesting to have the `.gouv.fr` part of the url in bold in the detailed menu, and the wording could probably be tweaked.

The nice part about this interface is that it explains rather than hides the complexity of the URL. It makes explicit the convention about government root domains, and hopefully it could even help people identify trustworthy government URLs outside of their browser address bar.


## What's next?

If you find this idea interesting, please feel free to participate in the conversation on this feature request on Mozilla Connect. I think that Mozilla Firefox is a great place to start implementing this, and then encourage other browsers to follow their lead.

If you're curious to see how it could be implemented, you can check out [this proof of concept](https://github.com/mozilla-firefox/firefox/compare/main...victormours:firefox:government) on Github.


## Additional notes

- The US government has added this banner on top of most of their official websites:
[screenshot of the banner]
- There are quite a few government websites that don't follow the .gov.tld convention, so there will be quite a few "false negatives" with this system, meaning official government websites that won't be flagged as such. These websites should still be displayed normally, and maybe the text for recognized website should aknowledge that not all websites will be properly tagged. For this kind of issue, it's better to have false negatives rather than false positives.
- I've started building a list of government domains, and there are a few edge cases, but I think it's still worth improving the experience of the overwhelming majority of citizens around the world.
