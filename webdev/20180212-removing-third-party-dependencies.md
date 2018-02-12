Published: 2018-02-12T22:00:00.000Z
Author: Greg Tyler <greg@gregtyler.co.uk>
Standfirst: An explanation of how—and why—I removed third-party dependencies on fonts and analytics from this website
Keywords: matomo,google analytics,analytics,third-party,piwik

Removing third-party dependencies

I recently decided to remove all third-party dependencies from most of my websites. That is, all scripts, CSS and fonts that are loaded from a server other than \*.gregtyler.co.uk

My primary concern is user privacy. Whenever you visit a site with a third-party dependency, that third-party is aware of your visit. So even if you don't click "like" on a page that features the Facebook button its mere presence—and the network request to load it—inform Facebook that you're there.

This site and others I run, like [Talk Like a Poirot Day](https://talklikeapoirotday.co.uk/), might not feature the sort of content you'd be too worried about third-parties knowing about your visit to; but the cumulative knowledge of visitors' viewing habits is the stuff of dystopian science fiction.

## Analytics
Facebook is an easy target here, but the real threat on my sites is Google through its [analytics tools](https://www.google.com/analytics/).

Analytics is the process of tracking users' visits to a website and then assessing them en masse to determine meaningful patterns which can help inform website development. For example, I'm aware that my articles on [an SSL error][article-ssl] and on [using Vue with Browersify and Grunt][article-vue] are much more popular than other content I've produced, so I might focus more on those fields in the future to improve my impact.

Google Analytics is the industry standard for analytics. It's a powerful, optimised product which makes it easy to analyse very small and very large sites. It's easy to setup, easy to use, and completely free.

However, every visit tracked by Google Analytics is sent to and stored on Google's servers. And, with an [estimated market share of nearly two thirds][ga-market-share], Google can realistically track people's movement across most of the web.

**Important disclaimer:** Google somewhat anonymises visitors, and you're treated as a different person on each website you visit. However, if they wanted to, Google could still easily fingerprint you between sessions and track you as a single entity.

**Important disclaimer 2:** Even if Google _were_ doing this (which they may or may not be), there's no reason to believe they're doing anything nefarious with the information.

Disclaimers aside though, the mere possibility is a troubling prospect to me.

## Attack vector
As well as notifying hosts of user activity, third-party dependencies produce a significant attack vector because they can change. Whilst a table-sorting script might do the job perfectly when you include it, a bad actor could in the future change that code to steal your users' data, redirect them to a phishing site, or mine BitCoin using their computer.

In fact that last event happened [just yesterday](https://www.theregister.co.uk/2018/02/11/browsealoud_compromised_coinhive/) on thousands of government, healthcare and educational sites when a third-party script to aid accessibility was compromised ([Troy Hunt](https://www.troyhunt.com/the-javascript-supply-chain-paradox-sri-csp-and-trust-in-third-party-libraries/) and [Scott Helme](https://scotthelme.co.uk/protect-site-from-cryptojacking-csp-sri/) give this an excellent in-depth technical write-up).

Again, I should caveat that the chance of this happening to third-party juggernauts like Google or Facebook is extremely low. And that it's quite easily avoided with [sub-resource integrity](https://developer.mozilla.org/en-US/docs/Web/Security/Subresource_Integrity) or [content security policy](https://scotthelme.co.uk/content-security-policy-an-introduction/). But it's worth being aware the threats.

## Matomo
Enter [Matomo](https://matomo.org/) (formerly Piwik). Matomo is an independent, open-source, self-hosted analytics platform. It works in the same way as Google Analytics but is not quite as polished and charges for many of the features that Google doesn't. Most importantly though, you can host your own instance.

And so it is that my Matomo installation is on [analytics.gregtyler.co.uk](https://analytics.gregtyler.co.uk/) so every time you visit this or one of my other sites, a notification is sent there and anonymously stored, and I can analyse trends to guide future content.

When I say anonymously, I mean this: Matomo tracks the pages you visit, and the city you're in, but otherwise it tracks and I know nothing more about your identity. Your IP address is trimmed in half before being saved (like with credit card numbers on receipts), so I couldn't try and trace you backwards even if I wanted to (whereas Google, Facebook etc. could).

Matomo also supports [Do Not Track](https://www.eff.org/issues/do-not-track), a setting you can turn on in your browser to opt out of these sort of automated tracking processes. If you don't want to be counted amongst these kind of statistics, I _highly_ recommend turning it on ([you can find instructions here](http://donottrack.us/)), though know that websites can freely ignore it.

I'd be ignorant to not note the trade-off here. Whilst your browsing habits are now free of Google, your localised ones have fallen to me. And their security, once kept by a tech giant with teams dedicated to it, is now in my hands.

That said, nothing has ever been stopping me, or any other random website, from tracking you privately anyway. Dropping Google Analytics at least gives you respite from one source. And with the isolated nature of your data (i.e. only tracking my own site) and the anonymity provided by Matomo, I see this as a much better solution for privacy rights.

### Installing Matomo
For those interested more in the technical side of using Matomo, let me briefly note that it's pretty easy as long as you're running a LAMP server. The documentation on the website provides an [easy install guide](https://matomo.org/docs/installation/), followed by a step-by-step wizard to connect things up.

At the end you get a script similar to the one Google Analytics provides which is an easy drop in replacement, as you can see from [the commit](https://github.com/gregtyler/Palomar/commit/056c6fb9cda969eb60008ab4a2da93f46d8e7238) that switched this website around.

However, setting up geolocation for Matomo is more difficult. It's quite a manual process, particularly if using PHP7 because you then need to compile the PECL extension yourself. I had a few stumbling blocks here, and I wouldn't feel qualified providing much advice to anyone else struggling. But I would note that you need geoip-beta, a piece of information I found squirreled away on a mailing list.

If you can live without geolocation, Matomo will do you proud from the off. If you can't, I recommend making sure you're comfortable with the command line, devops and your server. It's not a casual install, and getting it wrong has potential to signficantly break your server.

## Fonts
The other major third-party dependency I purged was fonts. This website previously used [Open Sans](http://www.opensans.com/) and [Titillium Web](https://www.fontsquirrel.com/fonts/Titillium), both loaded from [Google Fonts](https://fonts.google.com/about). Again, I had concerns with every visitor letting Google know of their presence here by loading the font.

Like Google Analytics, Google Fonts is an excellent service. It's fast, easy-to-use and free. Font loading is a difficult topic in web development and Google's service really makes it a breeze. With the complexity ahead, I balked slightly at having to figuring out a replacement for myself.

However, there's a [growing](https://medium.design/system-shock-6b1dc6d6596f) [trend](http://markdotto.com/2018/02/07/github-system-fonts/) recently of using [system fonts](https://css-tricks.com/snippets/css/system-font-stack/). That is, the default fonts that come with your computer or phone. This approach makes website look more native, improves performance (by removing the font-loading overhead), and protects against browser bugs (again, by simply removing the opportunity).

Mostly the system font approach is used by sites which want to seem like "apps". They want to lose the shackles of looking like a web interface and feel natural and at home on a user's computer or, more likely, phone.

Admittedly, gregtyler.co.uk does not want to appear like an app. You can't even comment. Or search. There isn't an input box on the site. But for that performance boost, and to stop me worrying about fonts, I took the leap and I think it looks pretty good.

As I continue to remove third-party dependencies from other sites, this choice won't last. I love the pleasure that custom fonts add to [my CV](https://cv.gregtyler.co.uk/), and [Talk Like a Poirot Day](https://talklikeapoirotday.co.uk/) simply wouldn't look the same in Segoe UI or Helvetica. Watch this space for details on how I choose to deal with those.

## Conclusion
Turning off third-party dependencies feels a bit like "going dark". This website is now an island, free of connections to the outside internet. Whether visitors notice it or not, _I_ feel more comfortable knowing that their browsing habits aren't being shared elsewhere.

Switching to Matomo has been really easy, and so far the information coming out is exactly what I need. And whilst switching to system fonts was a bit of a cop out, I'm really happy with how that has turned out.

Now I've just got to go back to every other site I've developed or hosted and continue the switch.

[article-ssl]: http://localhost:4141/webdev/ssl-read-errno-10054
[article-vue]: http://localhost:4141/webdev/vuejs-browserify-grunt
[ga-market-share]: https://www.similartech.com/categories/analytics
