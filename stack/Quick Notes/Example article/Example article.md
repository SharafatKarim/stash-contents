---
tags:
  - Node.js
  - OSS
Published: 2018-03-07
Last Updated: 2022-11-25T12:04
Author: https://twitter.com/transitive_bs
Created: 2022-11-19T18:12
Description: The best techniques for sharing code snippets and screencasts that will help propel your open source projects to success.
Public: false
Featured: false
---
_The best techniques for sharing code snippets and screencasts that will help propel your open source projects to success._

  

# Intro

Creating your own open source projects can be extremely rewarding, but it can be hard to break through the noise and get other developers to trust and use your software. You can gain a lot of ground by following [common best practices](https://opensource.guide/) like including solid documentation, adding unit tests, integrating with a CI/CD oriented towards open-source projects (like [travis-ci](https://travis-ci.org/) or [circle-ci](https://circleci.com/)), and enforcing consistent style conventions.

One of the most effective and easiest ways I’ve found to make open source projects really stand out from the crowd is **adding quality screenshots or animated demos**. Whenever I see this attention to detail, not only does it prove to me that the author cares about the project, but it’s the absolute fastest way to convey what the project actually does.

![[css-coding.gif]]

Animation Credit: [CSS-only coding animation](http://chrisdermody.com/css-only-coding-animation/) by [Chris Dermody](http://chrisdermody.com/)

> A picture is worth a thousand words. — Cliche saying that’s totes relevant

Including quality screenshots and demos is becoming an increasingly important part of what I’d call **Developer UX**, that is the flow a prospective developer takes from considering adding your project as a dependency all the way through successful integration and future maintenance.

Towards that end, we’ll be looking at three common use cases for improving the developer UX of your open source projects with media:

- Static code snippets (images)
- Animated code demos (GIFs or animated SVGs)
- Project screencasts (videos)

# **Static Code Snippets**

Sharing small bits of static code is definitely the most common and important use case on this list. Every open source project’s readme should include some easily parseable _example usage_ snippet, so let’s start there.

## **GitHub-Flavored Markdown Snippets**

At the easiest end of the spectrum, GitHub allows [syntax highlighting](https://guides.github.com/features/mastering-markdown/) in markdown code snippets. Hopefully, this style of embedding is familiar to you, and if not, I would definitely recommend starting here.

```JavaScript
const pMap = require('p-map')
const got = require('got')

const sites = [
  getWebsiteFromUsername('sindresorhus'), //=> Promise
  'ava.li',
  'todomvc.com',
  'github.com'
]

const mapper = el => got.head(el).then(res => res.requestUrl)

pMap(sites, mapper, { concurrency: 2 })
  .then(result => {
    console.log(result)
    //=> ['http://sindresorhus.com/', 'http://ava.li/', 'http://todomvc.com/', 'http://github.com/']
  })
```

  

## **GitHub Gists**

The code snippet above also provides an example of an extremely popular way of sharing static code snippets via [GitHub Gists](https://help.github.com/articles/about-gists/), which have the following advantages:

- Linkable
- Support versioning
- Support discussion via comments
- Syntax highlighting

## **Carbon**

Markdown snippets and GitHub gists are both useful, but if you really want to make your code pop, then look no further than [Carbon](https://github.com/dawnlabs/carbon).

![[carbon.png]]

Image Credit: [Carbon](https://github.com/dawnlabs/carbon)

Carbon is a very popular open source project that allows you to easily create aesthetically pleasing code screenshots, along with a plethora of customization options and community plugins. It’s a great choice for making a hero image standout in your readme, increasing engagement on social media, or for writing engineering-related blog posts like this one 😛.

# **Animated Code Demos**

Including a high quality, inline demo that quickly demonstrates your project’s core use case is the single most important suggestion I have to give.

There are a ton of different ways to go about creating these types of demos, however, so I’d like to discuss what I’ve found to be the best approach here.

> Asciinema is a free tool that lets you record and share your terminal sessions, the right way.

[**Asciinema**](https://asciinema.org/) provides a lightweight, purely text-based approach to terminal recording, which allows you to make lossless recordings that can then be shared directly or rendered to animated SVG, animated GIF, or video. It surprised me just how many popular open source projects on GitHub make use of Asciinema — I would highly recommend checking it out.

![[crl.gif]]

Example Asciinema screencast converted to a GIF (credit: [create-react-library](https://github.com/transitive-bullshit/create-react-library)) Note that the quality of this embedded GIF is much lower than the animated SVG in the linked [readme](https://github.com/transitive-bullshit/create-react-library) as discussed below.

## **Animated SVG or GIFs?**

We all know GIFs are a horribly inefficient, lossy format, but let’s dig a little deeper into this particular use case.

Compare the above embedded screencast gif to the animated SVG of the same screencast from the [readme](https://github.com/transitive-bullshit/create-react-library). It’s difficult to embed an inline comparison side-by-side, but the animated SVG is **significantly sharper and smaller**, coming in at 73kb vs 4.4MB for the lower quality GIF.

Why is this even a discussion then? Well, you can’t exactly include custom HTML in a Medium blog post, now can you? And for that matter, there are a lot of places where using custom animated SVGs won’t fly, and for the foreseeable future, GIFs will live on as a fallback for those use cases. But open source authors, please consider using animated SVG versus GIFs for your GitHub projects!

There are some very popular open source projects on GitHub that have started using more efficient animated SVGs for their demos, such as [create-react-app](https://github.com/facebook/create-react-app), but in general, you’ll find GIFs to be much more common.

Here's a few examples of using the excellent [svg-term-cli](https://github.com/marionebl/svg-term-cli) to generate our lossless animated SVG.

```Bash
# generate animated SVG
svg-term --cast 'fxdtpprue51QZkeViQurqPg8V' --out demo.svg --window --width=80 --height=24 --term=iterm2 --profile=Snazzy

# generate single frame SVG at 20 seconds into the screencast
svg-term --cast 'fxdtpprue51QZkeViQurqPg8V' --out screenshot.svg --window --width=80 --height=24 --term=iterm2 --profile=Snazzy --at 20000
```

It’s important to note that when discussing animated SVGs, we’re really talking about embedding an HTML snippet into GitHub-flavored markdown that links to an SVG file encoded with each frame as an SVG group and the animation defined via CSS keyframes (example SVG source).

```HTML
<p align="center">
  <img width="600" src="https://cdn.rawgit.com/transitive-bullshit/create-react-library/master/media/demo.svg">
</p>
```

Insert this HTML snippet into any GitHub-flavored markdown file to embed the linked animated SVG with optimal sharpness and low size overhead compared with a comparable GIF.

For reference, here is the screencast from [create-react-library](https://github.com/transitive-bullshit/create-react-library) we’ve been using as an example in several different formats:

- Original [asciicast](https://asciinema.org/a/167645)
- High quality [animated SVG](https://camo.githubusercontent.com/3f38f2bacbc1a6b49a5172232e8a4ccb9f10173f/68747470733a2f2f63646e2e7261776769742e636f6d2f7472616e7369746976652d62756c6c736869742f6372656174652d72656163742d6c6962726172792f6d61737465722f6d656469612f64656d6f2e737667) created with [svg-term-cli](https://github.com/marionebl/svg-term-cli)
- Low quality [GIF](https://cdn-images-1.medium.com/max/1600/1*6XX4DHE0HSHrGjiLFxmigQ.gif) created with [asciicast2gif](https://github.com/asciinema/asciicast2gif)

## **Capturing and Optimizing GIFs**

Asciinema is great for terminal-based recording, but what if you want to record a UI component or website? Well, my first and foremost answer here is to always include a usable demo if possible alongside your project, especially if it’s a frontend web project. It’s really easy to get started with GitHub [Page’s](https://pages.github.com/) free hosting!

If you do want to include a GIF, I’d recommend using either [GIPHY Capture](https://giphy.com/apps/giphycapture) or [Kap](https://getkap.co/) to record your screen and output a GIF. Alternatively, if you have a video recorded from another source, I’d recommend using [Gifski](https://github.com/sindresorhus/gifski-app) to convert the video to an as-optimized-as-possible GIF for ease of embedding.

```Markdown
<!-- html snippet customizing embedded gif -->
<img src="https://cdn.rawgit.com/terkelg/prompts/master/media/number.gif" alt="example prompt" width="499" height="103" />

<!-- raw markdown can also be used to ambed a gif -->
![](https://cdn.rawgit.com/terkelg/prompts/master/media/number.gif)
```

  

![[prompts.gif]]

Quality demo GIF embedded in readme using the snippet above. (image credit: [prompts](https://github.com/terkelg/prompts) by [terkelg](https://github.com/terkelg))

# **Project Screencasts**

If your project is becoming more involved or you’re launching your project to a wider audience, including walkthrough video(s) can really help with user onboarding and support.

## **Screenflow**

My go-to screen recording software is [ScreenFlow](https://www.telestream.net/screenflow/overview.htm), which is not cheap at $129, but gives you a lot of powerful, quality tools for the price, including precise rectangular screen recording, video and audio track mixing, audio voiceovers, transition effects, and more. This type of screencast is quite a bit more complicated than the screenshots and terminal session recordings we were looking at earlier.

# **Conclusion**

Developer UX is important for promoting and marketing your work, which can in turn lead to very real consequences, as getting noticed for your open source contributions is definitely one of the best ways to gain notoriety and land big job opportunities as a software engineer.

I hope some of the techniques I’ve covered help you to promote your open source projects. If you’ve found this article useful and end up creating a snazzy screenshot or animated demo, add a comment linking to your project and let me know!

And as always, don’t forget to spread the ❤️… in the form of beautiful coding demos, of course!

  

---

  

> [!important]  
> Follow me on twitter for more awesome stuff like this @transitive_bs