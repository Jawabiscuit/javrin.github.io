---
title: Hello Hugo
date: 2023-08-30T16:55:18-04:00
tags:
  - hello-world
categories:
  - hugo
  - loveit
draft: false
resources:
  - name: featured-image
    src: featured-image.jpg
  - name: featured-image-preview
    src: featured-image-preview.jpg
  - name: page-speed-insights
    src: page-speed-insights.png
---
Photo by [Chris Barbalis](https://unsplash.com/@cbarbalis?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash) on [Unsplash](https://unsplash.com/photos/doicC_ATzkQ?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash)
# 👋 Hello Hugo!

This is my new site generated using Hugo!

Ahhhh ☺ -- a fresh start. A new chapter is beginning, and I've had my eye on Hugo for a while. Having started and abandoned SSG (static site generator) projects in the past, this might be *thee* one for a while. It feels stable, feature rich, and easy to work with--all characteristics that are crucial for consistently keeping up and growing a website. 

If you're looking for an SSG, the most popular ones seem to be:

- [**Jekyll**](https://jekyllrb.com/) - Ruby based static site generator.
- [**Hugo**](https://gohugo.io/) - Go based static site generator.
- [**Gatsby**](https://www.gatsbyjs.com/) - React based framework for building websites and apps.

In this post I'd like to briefly share insights from my comparative analysis of SSGs and explain why I chose Hugo over Jekyll or Gatsby this time around. Information here is not intended to be used as persuasive arguments for using one or the other, but you might draw insights from my personal journey.
## 🌎 Overview
I'm coming from using Jekyll, a Ruby-based static site generator, to build my previous site and had mixed feelings about it's performance and ease-of-use. I decided to explore the current options and I found that Jekyll and Hugo are still very popular, so I'll try to focus on them primarily and sum up all the information I gathered from Googling for an afternoon.

*Jekyll* still seems to be preferred if you're looking for ease of initial **setup** which became a little more difficult for the beginner to deploy after Jekyll 3 which requires you to use GitHub Actions to deploy.

*Hugo* seems to be preferred, for those experienced with SSGs, for it's **performance** (just keep an eye on JS load). For example, it comes with Render Hooks for creating responsive images.
## 🚢 Deployment
The argument for ease of setup and deployment of Jekyll is outdated now. If you want to use the latest Jekyll, you'll have to use GitHub Actions, and if you don't you're stuck with using Jekyll 3 forever. Or, go with Hugo which is the same amount of setup, and for no reason are you locked to a specific version.

[Support for Jekyll 4.0 · Issue #651 · github/pages-gem · GitHub](https://github.com/github/pages-gem/issues/651)

{{< admonition type=quote title="Why GitHub chose Actions for deployment" open=true >}}
Using Actions to orchestrate Pages publishing provides many more options for choosing your authoring framework ([Next.js](https://nextjs.org/), [Hugo](https://gohugo.io/), [Gatsby](https://www.gatsbyjs.com/), [Jekyll](https://jekyllrb.com/), [NuxtJS](https://nuxtjs.org/) or other technologies, and the associated versions thereof) as well as giving you finer control over the publishing process, such as leveraging deployment gates.

~ [GitHub Pages: Custom GitHub Actions Workflows (beta) - The GitHub Blog](https://github.blog/changelog/2022-07-27-github-pages-custom-github-actions-workflows-beta/)
{{< /admonition >}}
## 🏇 Performance
When it comes to evaluating the performance of SSGs [PageSpeed Insights](https://pagespeed.web.dev/) is your friend or worst enemy here. Here's a great article explaining Google Lighthouse scores: [How to get a 100% Google Lighthouse score | Usecue web development](https://www.usecue.com/blog/how-to-get-a-100-google-lighthouse-score/)

{{< admonition type=quote title="Hugo for performance" >}}
I ditched Gatsby and migrated this site over to Hugo. Hugo is often viewed as the fastest static site generator… it is. 

~ [Goodbye Gatsby, Hello Hugo - Made Mistakes](https://mademistakes.com/notes/goodbye-gatsby-hello-hugo/)
{{< /admonition >}}

{{< admonition type=quote title="Render hooks" >}}
Then there’s Hugo, which lets you customize how Markdown outputs to HTML with what it calls [**render hooks**](https://gohugo.io/templates/render-hooks/). These render hook templates are standard HTML with the same [templating logic](https://gohugo.io/templates/introduction/) used to write shortcodes, partials, and layouts. Something I appreciate, as writing HTML comes more naturally to me than JavaScript or Ruby.

~ [Goodbye Gatsby, Hello Hugo - Made Mistakes](https://mademistakes.com/notes/goodbye-gatsby-hello-hugo/)
{{< /admonition >}}
## 🤔 Sentiment
There's certainly more depth when it comes to comparing SSGs like Hugo, Jekyll, and Gatsby. However, this summarizes what I discovered during my initial research. There isn't a ton of new information out there. I also ran manual sentiment analysis on this dated but relevant GitHub conversation: [Is the Jekyll project dead? - Help - Jekyll Talk](https://talk.jekyllrb.com/t/is-the-jekyll-project-dead/6820/5)

|        | setup | complexity | scope | templating | build process | version | community | complete |
| ------ | ----- | ---------- | ----- | ---------- | ------------- | ------- | --------- | -------- |
| jekyll | 😐    | 😐         | 😐    | 🙂         | 🙂 (na)            | 🙂      | 🙂        | 🙂       |
| hugo   | 🙁    | 😵         | 🤔    | 🙁         | 🙁            | 🙁      | 🙁        | 🙁       |

In my opinion, people were more enthusiastic about Jekyll and more unenthused by the complexity of Hugo, however in practice I'd have to say that things must have changed quite a bit from 2021-2022 because yeah Hugo can be complex if you want it to be but it doesn't need to be. For instance, in case it's not obvious, [loveit](https://hugoloveit.com), the theme I'm using looks great on mobile platforms and has implemented just about every feature I absolutely need for a basic site.

{{< admonition type=hint title=deployment open=true >}}
I mentioned Hugo has a build/deploy process you have to maintain, but these days that problem has been worked out and it can take an hour or two *max* to set that up if you're unexperienced with Actions (see Resources below).
{{< /admonition >}}
## 🎀 Summing It Up
While Jekyll is alive and well and continues to be used for creating impressive websites, my research didn't uncover substantial evidence favoring Jekyll over Gatsby or Hugo.

Why I chose Hugo came down to those key characteristics I mentioned in the beginning. On top of that, no more running `gem` as well as `bundle` commands, and keeping up with dependencies is much less of a hassle to non-existent as of yet. So far, I'm really impressed with local preview builds, how fast and responsive they are, and visually the site is an exact match locally as it is deployed. Finally, the project directory feels less cluttered (and you know what they say about cleanliness).

Every body likes lists, so here's my top 10 reasons for using Hugo in no particular order:

- Stability
- Features
- Ease-of-use
- Robust and easy to use command line
- Dependency management
- Clean project structure
- Performance
- Speedy preview builds
- Rapid deployment
- It's free!

&nbsp;

As for performance...

{{< image src="page-speed-insights.png" caption="I'll certainly be 👀 and 🔨ing my score, but it's fast!" src_l="page-speed-insights.png" >}}

&nbsp;

So here's to new beginnings, Hugo. 🥂 If you're still unsure about which static site generator is right for you, I encourage you to explore the links provided and do your own research (DYOR)! Please hit me up or share on social media if you found this content helpful or have suggestions and have a nice day!

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