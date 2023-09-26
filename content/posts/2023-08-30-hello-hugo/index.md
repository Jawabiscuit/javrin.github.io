---
title: Hello Hugo
date: 2023-08-30T16:55:18-04:00
tags:
  - hello-world
categories:
  - hugo
  - loveit
draft: true
images:
  - page-speed-insights.png
  - hugo-large.png
featuredImage: hugo-large.png
---
# 👋 Hello Hugo!

This is my new site generated using Hugo!

Ahhhh ☺ -- a fresh start. A new chapter is beginning, and I've had my eye on Hugo for a while. Having started and abandoned SSG (static site generator) projects in the past, this might be *thee* one for a while. It feels stable, feature rich, and easy to work with--all characteristics that are crucial for consistently keeping up and growing a website. 

If you're looking for an SSG, the most popular ones seem to be:

- [**Jekyll**](https://jekyllrb.com/) - Ruby based static site generator.
- [**Hugo**](https://gohugo.io/) - Go based static site generator.
- [**Gatsby**](https://www.gatsbyjs.com/) - React based framework for building websites and apps.

In this post I'd like to briefly share a little bit about research I did and how I took the plunge and started using Hugo.
## Tl;dr
I used Jekyll to build my previous site and both liked/disliked certain things about it, so I wanted to investigate something new but here is the tl;dr. I found that Jekyll and Hugo are still very popular, so I tried to sum up all the information I gathered from googling for an afternoon.

*Jekyll* still seems to be preferred if you're looking for ease of initial **setup** which became a little more difficult for the beginner to deploy after Jekyll 3 which requires you to use GitHub Actions to deploy.

*Hugo* seems to be preferred, for those experienced with SSGs, for it's **performance** (just keep an eye on JS load). For example, it comes with Render Hooks for creating responsive images.
## Deployment
The argument for ease of setup of Jekyll is out-of-date. If you want to use the latest Jekyll, you'll have to use Actions, and if you don't then you're stuck with Jekyll 3 forever. Or, go with Hugo which is the same amount of setup, and for no reason are you locked to a specific version.

[Support for Jekyll 4.0 · Issue #651 · github/pages-gem · GitHub](https://github.com/github/pages-gem/issues/651)

{{< admonition type=quote title="Why GitHub chose Actions for deployment" open=true >}}
Using Actions to orchestrate Pages publishing provides many more options for choosing your authoring framework ([Next.js](https://nextjs.org/), [Hugo](https://gohugo.io/), [Gatsby](https://www.gatsbyjs.com/), [Jekyll](https://jekyllrb.com/), [NuxtJS](https://nuxtjs.org/) or other technologies, and the associated versions thereof) as well as giving you finer control over the publishing process, such as leveraging deployment gates.

~ [GitHub Pages: Custom GitHub Actions Workflows (beta) - The GitHub Blog](https://github.blog/changelog/2022-07-27-github-pages-custom-github-actions-workflows-beta/)
{{< /admonition >}}
## Performance
I'll just mention a couple of sources here that helped me. [PageSpeed Insights](https://pagespeed.web.dev/) is your friend or worst enemy here. Here's a great article explaining Google Lighthouse scores: [How to get a 100% Google Lighthouse score | Usecue web development](https://www.usecue.com/blog/how-to-get-a-100-google-lighthouse-score/)

{{< admonition type=quote title="Hugo for performance" >}}
I ditched Gatsby and migrated this site over to Hugo. Hugo is often viewed as the fastest static site generator… it is. 

~ [Goodbye Gatsby, Hello Hugo - Made Mistakes](https://mademistakes.com/notes/goodbye-gatsby-hello-hugo/)
{{< /admonition >}}

{{< admonition type=quote title="Render hooks" >}}
Then there’s Hugo, which lets you customize how Markdown outputs to HTML with what it calls [**render hooks**](https://gohugo.io/templates/render-hooks/). These render hook templates are standard HTML with the same [templating logic](https://gohugo.io/templates/introduction/) used to write shortcodes, partials, and layouts. Something I appreciate, as writing HTML comes more naturally to me than JavaScript or Ruby.

~ [Goodbye Gatsby, Hello Hugo - Made Mistakes](https://mademistakes.com/notes/goodbye-gatsby-hello-hugo/)
{{< /admonition >}}
## Sentiment
There's more to the story of course, but that is the summary of information I found in my brief research. There isn't a ton of new information out there. I also ran manual sentiment analysis on this dated but relevant GitHub conversation: [Is the Jekyll project dead? - Help - Jekyll Talk](https://talk.jekyllrb.com/t/is-the-jekyll-project-dead/6820/5)

|        | setup | complexity | scope | templating | build process | version | community | complete |
| ------ | ----- | ---------- | ----- | ---------- | ------------- | ------- | --------- | -------- |
| jekyll | 😐    | 😐         | 😐    | 🙂         | 🙂 (na)            | 🙂      | 🙂        | 🙂       |
| hugo   | 🙁    | 😵         | 🤔    | 🙁         | 🙁            | 🙁      | 🙁        | 🙁       |

In my opinion, people were more enthusiastic about Jekyll and more unenthused by the complexity of Hugo, however in practice I'd have to say that things must have changed quite a bit from 2021-2022 because Hugo, yeah, can be complex if you want it to be but it doesn't need to be. For instance, I the theme I'm using--if you don't know by now, [loveit](https://hugoloveit.com)--is great and has implemented just about every feature I can think of for a basic site.

I mentioned Hugo has a build/deploy process you have to maintain, but these days that problem has been worked out and it can take an hour or two *max* to set that up if you're unexperienced with Actions (see Resources below).
## Summing It Up
So no, Jekyll is not dead and there are some really nice websites still being created with it and I couldn't find substantive evidence for Gatsby.

Why I chose Hugo came down to what I mentioned in the beginning. On top of that, no more running `gem` as well as `bundle` commands, and keeping up with dependencies is much less of a hassle, non-existent as of yet. So far, I'm really impressed with local preview builds, how fast and responsive they are, and the site is an exact match locally as it is deployed. 

As for performance...

{{< image src="page-speed-insights.png" caption="I'll certainly be 👀 and 🔨ing my score, but it's fast!" src_l="page-speed-insights.png" >}}

&nbsp;

So here's to new beginnings, Hugo. 🥂

If you are wondering what to choose, check out the links and DYOR!

---
## 🔗 Resources 
### Discussions
- [Support for Jekyll 4.0 · Issue #651 · github/pages-gem · GitHub](https://github.com/github/pages-gem/issues/651)
- [GitHub Pages: Custom GitHub Actions Workflows (beta) - The GitHub Blog](https://github.blog/changelog/2022-07-27-github-pages-custom-github-actions-workflows-beta/)
### Actions
- [Hugo setup · Actions · GitHub Marketplace · GitHub](https://github.com/marketplace/actions/hugo-setup#%EF%B8%8F-use-hugo-extended)
- [GitHub - peaceiris/actions-gh-pages: GitHub Actions for GitHub Pages 🚀 Deploy static files and publish your site easily. Static-Site-Generators-friendly.](https://github.com/peaceiris/actions-gh-pages)
- [GitHub - peaceiris/actions-gh-pages: GitHub Actions for GitHub Pages 🚀 Deploy static files and publish your site easily. Static-Site-Generators-friendly.](https://github.com/peaceiris/actions-gh-pages#%EF%B8%8F-first-deployment-with-github_token)
### Pages
- [Managing a custom domain for your GitHub Pages site - GitHub Docs](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site)
- [Automatic token authentication - GitHub Docs](https://docs.github.com/en/actions/security-guides/automatic-token-authentication#permissions-for-the-github_token)
- [Creating a GitHub Pages site - GitHub Docs](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site)
### Theme
- [About LoveIt - LoveIt](https://hugoloveit.com/about/)
### Getting Started
- [Jekyll Codex](http://jekyllcodex.org/)
- [Hugo Codex](https://hugocodex.org/)