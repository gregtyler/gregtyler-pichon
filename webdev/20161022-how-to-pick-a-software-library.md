Published: 2016-10-22T17:10:52.000Z
Author: Greg Tyler <greg@gregtyler.co.uk>
Standfirst: Lately, I've been in the business of picking libraries. I explain some of the key things that I look out for in a library, and why they're important.

How to pick a software library

Lately, I've been in the business of picking libraries. Barcodes, PDFs and automated testing suites have been particularly in my sights recently, but it's a topic that comes up regularly. With that in mind, I thought I'd provide a guide of things I look out for when picking what to use. A buying guide for software libraries, if you will.   

Picking the best library is an important decision. Moreover, selecting poorly has the potential to really hinder your project in the future. Unfortunately, there are a lot of complex considerations to factor in to your decision. I think all of the ones I list here are important, but the weight put on each will differ between projects, people and subject matter. I'd be really interested to hear how important you think each of them is, as well as anything else you take into consideration.   

I should note that, due to personal experience, this mainly comes from the point-of-view of picking JavaScript libraries, but I believe it's completely transferable to other languages too.   


## Functionality


I doubt you'll be surprised to see this high up in the list. If you're picking a barcode library and it doesn't produce [Code 39][1] then it's immediately out. Of course, not all functionality is as clearly nuanced as this so, if you can, it helps to identify up-front exactly what you need it to be able to do. I also try and think to the future, and what functionality we might need for the next iteration, or if we get funding to expand what we do with it.   

When you get into shortlisting territory, functionality is something I find it's worth experimenting with yourself. Creating a small mock-up of what you're going to do with it can highlight gaps which might not be clear from the documentation but could stop you dead in your tracks.   


## API


On the web we often think of APIs in terms of how services interact with each other, often through RESTful or GraphQL interfaces. In this context though, I'm thinking more locally of how your existing codebase interacts with the library that you're looking to use. If you're using an app which is implemented solely with HTML (examples in Lea Verou's [MarkApp][2]), this decision is likely to be quite straightforward.   

However, if your code is going to make calls to or reference the library then you need to ensure that they can interoperate in a way befitting your codebase, the library, and your sanity as a code author. I think a good thing to look out for is whether the design of the API matches its functionality. I expect a simple barcode library to have one function: `drawBarcode`. A more complex API may imply a tool that isn't well thought out, or is only a half-baked fork of another library.   

It's probably important to note that I don't think that a bad API means that a library is bad, but I've found it can be a good indicator of problems elsewhere. Plus, it's one of the few bits of the library you as a developer will see, so picking something you'll hate working with needs to facilitate some serious payoff.   


## Dependencies


If you can, I completely advise avoiding dependencies. I still work on projects which use a certain library purely because it's a dependency for something critical. You don't want to be adding jQuery to every page just because you wanted to add a filter to tables. Whilst you might use jQuery every day now, it's nice to know that you could drop it and wouldn't have to also find a new table filterer.   

Sometimes dependencies may be unavoidable. For example, it used to be hard to find a good multiselect or tablesorter plugin that didn't use jQuery, Mootools or Prototype. In that case, it's best to opt for something you already use. You certainly don't want to have to keep using both jQuery _and_ Prototype just because of legacy plugins you're still supporting. But these scenarios are far less common now.   

(No hate for jQuery, it's just a good example. I still use it on loads of projects.)   


## File size


Web pages are getting [ridiculously big][3], and a massive contributor is unnecessarily large JavaScript libraries. Users hate slow websites, and slow websites very often are caused by bloated libraries. So don't use them.   

Obviously, some libraries will be bigger than others. The difficult question is weighing size against functionality. In it's most basic form, if two libraries give you the exact same functionality and one is even 3 bytes bigger, choose the small one. With more nuanced decision making, consider what your budget is, what you're loading already, and what you can afford.   

If there's nothing that will fit into your page load budget, consider whether you can build it yourself. It may be more for you to support, but if it helps your users get snappy load time and encourages them to keep using your site, then the cost of that support is easily worth it.   


## Support


Support is always a _huge_ point of consideration for me. When I'm browsing libraries, I love being able to browse their issues on GitHub (or hosting platform of choice). Red flags for me include:   



* Lots of open issues (support not being actively provided)


* No issues at all, or only issues opened by the developer (no-one else is using this)


* Issues closed without resolution


* Issues which have been open a long time (typically hints that they may be fixing the easy, small things)



Whereas things I like to see include: active discussion involving the developers, newbie questions answered probably (instead of being told to Read the Manual), pull requests being accepted from others with sensible reviews.   

As with anything in this list, there are of course exceptions and you should be careful not to draw the wrong conclusion. Font Awesome has [3,718][4] unresolved issues at time of writing, but only 38 are bugs. If you care about your library choices, be sure to look deeper than just the big number at the top.   


> I had a great experience recently when I was trying out the [WebdriverIO library][5]. I found [a bug][6] with the library and reported it, tried and failed to fix it myself. A developer replied within 24 hours with a fix. That support was fantastic and it allowed me to freely get on with my job. I've been using WebdriverIO ever since, and can confidently state that support as one of the reasons why.



Also worth looking at: forum posts, Stack Overflow questions (and their answers), blog articles. You may well need support, and it's good to know it's going to be there.   


## Documentation


For even the most basic of libraries, documentation is essential for your new library. Without it, you won't be able to start. It's also your first point of support and perhaps your only opportunity to get an answer without having to wait for someone to reply. The best libraries have such good documentation that you don't ever need to ask for help. If you think about it, I'm sure you can pick out some choice libraries that you've never had to look further than the documentation to use. Perhaps not as many as you'd like though.   

If you've got time, looking through a history of the documentation can be a very good indicator of how the developers treat it. What looks like great documentation at first might not have been updated in two years of new versions. If documentation has only recently been introduced, this could mean it's a new important priority, or that it's not going to be kept up-to-date past this point.   


## Ownership


Is the library owned by a company, an individual or an organisation? All of them have pros and cons.   

I would say that something like the jQuery Foundation or Mozilla is the most preferable, because their strategy is to support developers like us to make great things.   

If a company owns the library, consider what their edge is. Many companies aren't going to support a library without a determined way to make money out of it. This might be by selling support, [by selling premium features][7], by [using it as a vehicle to promote other products][8]. Maybe they plan to hold future versions hostage. In many cases though, it's just to raise their company profile by getting their name out there. But you've still got to be aware that the rug could be [pulled from under your feet][9] if their business case stops adding up.   

If an individual owns it, then what's their motivation to keep supporting it? What plans do they have when they stop? Again, consider what would happen if you were to [lose it overnight][10].   


## Ability to edit


I think it's good to know if the library accepts pull requests. If you find bugs you want to fix or new functionality to add, you want to be able to do it at the source. The alternative is forking, which means you'll miss updates and have to support yourself. If you choose to do that, you'll be supporting legacy software in your project and might as well write your whole own library.   


## Price


I don't have much to say on price because, in this amazing world of open source, I haven't paid for a library in years. I would suggest that you have to re-evaluate almost everything in this list, weighing up the difference in price between each option against the functionality, support, documentation etc. that you'll gain.   

Paying can be worthwhile. [Highcharts][11] looks amazing, and I understand it's well worth the price tag if charts are a fundamental part of your application. If something is important enough to justify the price tag, don't just turn it down because you're cheap. Though equally, don't spend money on something with great flashy demos without evaluating it first (I've fallen foul of this many times in life).   


* * *



Over the years, I've picked some libraries that have turned out great. Tools that I've used for years since. But I've also picked some duds, even when I've been careful. In the real world, you can't account for everything and sometimes you'll get caught out. Yet you can mitigate that damage by choosing wisely and being aware of what you've got. Minimising dependencies, understanding the reality of support and ownership, and knowing how you'll use the library are all extremely valuable bits of information.

[1]: https://en.wikipedia.org/wiki/Code_39
[2]: http://markapp.io/
[3]: http://idlewords.com/talks/website_obesity.htm
[4]: https://github.com/FortAwesome/Font-Awesome/issues
[5]: http://webdriver.io/
[6]: https://github.com/webdriverio/webdriverio/issues/1354
[7]: http://themes.getbootstrap.com/
[8]: https://www.ampproject.org/
[9]: http://blog.parse.com/announcements/moving-on/
[10]: http://www.theregister.co.uk/2016/03/23/npm_left_pad_chaos/
[11]: http://www.highcharts.com/
