---
title: 'Building a fast and secure website for free'
# For SEO:
description: How I built a fast, simple and highly secure website which cost nothing more than the fee required to register the domain
keywords: [cyber security, jekyll, static sites]
#Allows Jekyll to group related posts under a subfolder:
category:

layout: page
---

_Last updated: 08 February 2021_

**_Many websites are slower, more complex and less secure than they need to be. It's possible, however, to build a fast, simple and highly secure website which costs nothing more than the fee required to register your domain. This article is a fairly non-technical walkthrough of what I learned in building the Cloud Explore website and why you may want to consider a similar approach for your own page._**

---

Part of the ethos of Cloud Explore, which inspired the name itself, is the value of security that is strong and light. Having worked on security for some really large organisations, I've seen first-hand how complexity creates major challenges. That's a blog for another day, but the key idea is that one of the best things you can do from a security perspective is to simplify your systems as much as possible.

With that in mind, I set out to create a website that was as clean, lightweight and secure as possible - ideally at minimal cost. After some research, and putting the question to a group of penetration tester friends who hack websites (among other things) for a living, I had a solution that sounded ideal: Build a static website using Jekyll, host it for free on GitHub Pages and then increase performance and security using Cloudflare's free-tier services.

If that makes absolutely no sense to you at this stage, please don’t worry. I was quite new to this as well! This post is all about sharing the lessons I learned along the way.

# Why use a static website?

Static websites are simple, lightweight and fast. They exist as pre-generated code, which your browser can read directly and display to you as a website. The opposite of a static website, in more ways than one, is a _dynamic website_. Dynamic websites create code for your browser using what's called a web application. The web application runs on an operating system, which in turn runs on a web server connected to a database and often other different systems as well. Each of these components introduces significant complexity, dependencies, and maintenance requirements. It also adds a large amount of  _attack surface_: opportunities for attackers to find and exploit vulnerabilities.

> In simple terms, dynamic websites are harder to secure and easier to hack. Static websites, especially simple ones, don't really give hackers much to work with at all.

This simplicity also makes static websites seriously fast. This improves user experience, as pages load almost instantly, and helps your [search rankings](https://developers.google.com/search/blog/2010/04/using-site-speed-in-web-search-ranking) as well.

Static sites are great for use cases like ours, where the objective is to inform people about the business and provide a means of getting in touch. Static sites are not just for blogs or small businesses, either: [Jekyll](https://jekyllrb.com/) alone is used by organisations including [Netflix, Spotify, AWS, multiple governments, and the UN](https://jekyllrb.com/showcase/) to create pages for projects and documentation. Jekyll also has built-in support for [GitHub Pages](https://docs.github.com/en/github-ae@latest/github/working-with-github-pages/about-github-pages-and-jekyll), which will host your site for the low, low price of free.

# What about Wordpress?

Wordpress is hugely popular, making up around [39.9%](https://w3techs.com/technologies/details/cm-wordpress) of all websites on the internet. Wordpress offers a commercial version ([wordpress.com](https://wordpress.com/)) which they host for a fee, and an open source version ([wordpress.org](https://wordpress.org/)) which you can host on your own server.

Wordpress, Wix and similar offerings make it really simple to create and customise new websites. The problem is that they also come with the complexity and problems associated with dynamic sites. Wordpress also has a huge ecosystem of plugins, which add functionality but can be a [security nightmare](https://www.zdnet.com/article/pirated-themes-and-plugins-are-the-most-widespread-threat-to-wordpress-sites/). The site for [Wordfence](https://www.wordfence.com/), a popular Wordpress security plugin, is a helpful illustration of the challenges involved in securing Wordpress properly. Even if you go to the effort of keeping your site and systems up to date, there is also no escaping the increased exposure inherent in the larger attack surface.

I decided to stay the course and to start building with Jekyll.

# Meeting Mr Hyde

Jekyll, I found, is in many ways the opposite of Wordpress: Structurally simple but not as friendly for less technical users. Though much easier and faster than writing the web page's code from scratch, it was still a steeper technical curve than most would choose to climb. Even making use of some of the helpful [step-by-step guides](https://jekyllrb.com/docs/step-by-step/01-setup/) available (another [here](http://jmcglone.com/guides/github-pages/)), the DIY route required some comfort with the Linux command line, a basic understanding of [GitHub](https://github.com/), and some ability to navigate and edit the code itself. The learning curve also becomes much steeper again if you want to make substantive changes to the template you've chosen as the basis for the page.

This doesn’t mean less technical people should be deterred from embracing Jekyll and its [Jamstack](https://jamstack.org/what-is-jamstack/) relatives. Far from it. If you can get a web developer to do the initial setup for you, it's not too hard to then add and modify your own content. When you create a new piece of content, you just need to create a file in a format called [Markdown](https://www.markdownguide.org/) - which is really quite simple and intuitive to use - and then upload it to your site.

Though it does involve adding some additional steps and components, there is also a [growing field of Content Management System (CMS) platforms](https://jamstack.org/headless-cms/). I didn't find a free option that suited my needs, but I can see them working well for users of a website that has already been set up.

# More speed (and even more security)

After a challenging few days getting the website into a state I was happy with, getting the site online with GitHub Pages was actually quite easy. While it's possible to stop there and have a perfectly functional site, I wanted to take the next step to make it faster and more secure.

As mentioned earlier, static sites are just code that your browser reads. This provides an inherent speed advantage, and you can make them even faster and more resilient using a Content Delivery Network (CDN). CDNs perform a few different functions, but the main thing is they have servers all over the world where they will save a copy of your website. That way, a user's computer doesn't have to connect to a server on the other side of the globe, it just grabs the nearest copy and loads it. It also means that you can handle large amounts of traffic efficiently, which is great if you have a post that gets a lot of attention - or if someone tries to perform a [Distributed Denial of Service attack](https://www.cyber.gov.au/acsc/view-all-content/threats/denial-service) against the site.

By following their [documentation](https://blog.cloudflare.com/secure-and-fast-github-pages-with-cloudflare/), it was fairly simple to configure my GitHub Pages site to run through Cloudflare's free-tier CDN service.* Though there are also some great paid CDN options from providers like [Netlify](https://www.netlify.com/) and [Fastly](https://www.fastly.com/), a simple page like ours works well within the limitations of the Cloudflare free plan, and it allows me to configure a range of useful security options.

# The end result

While it was a much more challenging experience than setting up a Wordpress or Wix site, I learned a lot from the process and I'm really happy with the result. The site's small data requirements make it fast and responsive, while also reducing its overall resource footprint. The technical simplicity of the site also minimises maintenance requirements and enables me to focus on other aspects of running the business. Finally, it's nice to have an online presence without any cost overheads aside from a fee for my domain name every few years.

If you're starting a new website, or considering a refresh of your existing one, it's definitely worth looking into creating a static site. If you're running a Wordpress site or similar, it's probably also a good time to check that its various components are up to date and configured securely.


---

_James Williams is the Founder of [Cloud Explore](https://cloudexplore.it), a Melbourne-based company founded with the objective of bringing tier-one cyber security consulting to organisations that make the world a better place. ([LinkedIn](https://www.linkedin.com/company/68947302), [Twitter](https://twitter.com/graphenesec))_

---

_*I have to mention that Cloudflare have previously been involved in controversies where they have failed to withdraw their services from sites hosting objectionable content. Though I understand they have since made changes to their policies, I would take a close look at Cloudflare's ethical record before paying for their services._