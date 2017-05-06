Published: 2017-05-06T13:00:00.000Z
Author: Greg Tyler <greg@gregtyler.co.uk>
Standfirst: My blog is a (fairly) recent creation which involved some new tools and techniques, as well as a significant change to the way that I write.

# Building gregtyler.co.uk

At the start of 2017, I decided to completely rebuild my blog from scratch in Node.js. My old blog was hosted on WordPress but over the years I'd got tired of the framework's complexity and speed issues, particularly because I didn't use the majority of the features.

I wanted to build something that was simple, lean, nicely designed and usable on all devices by all viewers. I was also inspired by the work Nicolás Bevacqua did on [Pony Foo](https://ponyfoo.com/articles/two-way-synchronization-for-a-web-app-and-git) to track his articles through Git and make it easy for anyone to suggest edits through GitHub.

In this post, I want to go through some of the decisions I made in redesigning [gregtyler.co.uk](https://gregtyler.co.uk/) and the tools I used to do so.

## Building a blog
Let's start with the technical bits. This website is written bespoke in Node, without even a application framework like Express (the notable modules I use are [marked](https://www.npmjs.com/package/marked) for Markdown parsing, [highlight.js](https://highlightjs.org/) for code display, and [nunjucks](https://mozilla.github.io/nunjucks/) for templating). Not using an application framework might seem like a silly idea and, in general, it is. But this project was as much about learning how to build a Node application as it was about having a new blog, so I used the opportunity to learn properly about how Node handles HTTP requests and responses by handling them all myself.

In development I focused on a couple of major goals. One was to ensure the site is performant, which not having an application framework helps with because I can see everything happening end-to-end between a request and response. Another was to build an application that would be robust for the future. I've got no plans to roll out the application (which I've called "Palomar") to any other websites, but designed it as if I did intend to. I also designed it to be extensible in the future so that adding new features won't require rewriting the whole application.

The application is hosted on [DigitalOcean](https://www.digitalocean.com/), which is new for me. I switched from my old host because I was having performance issues, bad customer support and paying too much. So far DigitalOcean has been cheaper, faster and, whilst I haven't had to experience customer support yet, I've been impressed by the wealth of [tutorials](https://www.digitalocean.com/community/tutorials) on their site documenting how to install and manage all sort of software on their servers.

On the server, I use [nginx](https://www.nginx.com/) as a server and, thanks to [Let's Encrypt](https://letsencrypt.org/), I'm using HTTPS everywhere.

You might wonder what database I'm using, and be surprised to find that I'm not. See "Blogging with Git" below to find out more.

# Designing a blog
Anyone who visited my old blog will be familiar with the new design. The colour scheme, fonts and general layout are all very familiar, and I'm continuing to use "card" structures on the home page.

There are a couple of significant changes. One is that every post has a "series". These work similar to categories in other blogging platforms, except that every post only gets one, and it's used to determine where the post is stored in the Git repository. I'm not sure this is the best idea, but so far it's working out quite well as a way to section off particular kinds of content (friends may not interested in my [Web development](/webdev), colleagues might not want to read about [Christmas films](/christmas-2014)).

Another big change is the addition of "linked articles". These display alongside normal articles on index and archive pages, but are actually links out to articles I've written on other sites. This means that my blog is now the index page for _everything_ I write online rather than just the things I've written here.

The CSS for the site is quite simple. There's [one CSS file](https://gregtyler.co.uk/main.css), which uses no frameworks and sits at a tidy 1.9KB. I've used the patterns of [BEM](https://en.bem.info/methodology/quick-start/) and [ITCSS](http://itcss.io/), mostly inspired by the work of [Harry Roberts](https://csswizardry.com/) and [BBC Sport](https://medium.com/@shaunbent/css-at-bbc-sport-part-1-bab546184e66).

There's only one JavaScript file and that's Google Analytics, which I'm planning to remove for something more ethical.

# Blogging with Git
By far the biggest decision in this development was moving all of the blog writing to [Git](https://git-scm.com/). Git is a version control system, which means it keeps track of all of the changes ever made to a bunch of files, can give detailed history of each and restore to any point in time. It's a much more involved, powerful version of track changes.

The benefits of having Git support writing should be obvious, but the implementation of doing so certainly is slightly involved. I have a [repository of all of my articles](https://github.com/gregtyler/gregtyler-pichon) which is mirrored on the blog server. The application then uses its copy of the files to render and display pages as they are requested. This means that changes can be made either on my computer, or on GitHub, and then need to be pushed onto the server before they are live.

As explained in the [article from Nicolás Bevacqua](https://ponyfoo.com/articles/two-way-synchronization-for-a-web-app-and-git), a key benefit of this is that readers can identify mistakes or improvements and fix them themselves in GitHub. It also means that, when not at home, I can write drafts and articles through GitHub's interface rather than on my computer.

One regret I have about the current set-up that I would like to change is that it relies on a push to the application server. In the future, I'd like the server to automatically take any new updates directly from GitHub without needing a push. This would enable to handle my entire editing and publishing process through GitHub rather than needing my PC to actually put the new posts on the server.
