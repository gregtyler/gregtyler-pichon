Published: 2016-08-09T08:34:53.000Z
Author: Greg Tyler <greg@gregtyler.co.uk>
Standfirst: I got this error when using WebdriverIO and Cucumber. It turned out to be because Selenium Grid wasn't running on the server.

"FATAL ERROR: Allocation failed" error with WebdriverIO and Cucumber

It feels a bit silly writing articles about handling very specific bugs, but [a similar article I wrote previously][1] is consistently one of my most-viewed articles and appears high in Google search results. So, assuming that's because it's useful, I'll do so again.   

Yesterday I wrote a WebdriverIO test in the Cucumber handler. When I ran it this morning, I got the following error:   

```
<--- Last few GCs --->
   96024 ms: Mark-sweep 1197.8 (1437.0) -> 1197.8 (1437.0) MB, 1806.3 / 0 ms [allocation failure] [GC in old space requested].
   97817 ms: Mark-sweep 1197.8 (1437.0) -> 1197.8 (1437.0) MB, 1793.4 / 0 ms [allocation failure] [GC in old space requested].
   99611 ms: Mark-sweep 1197.8 (1437.0) -> 1197.7 (1437.0) MB, 1794.2 / 0 ms [last resort gc].
  101388 ms: Mark-sweep 1197.7 (1437.0) -> 1197.7 (1437.0) MB, 1776.7 / 0 ms [last resort gc].
<--- JS stacktrace --->

==== JS stack trace =========================================

Security context: 00000329E79C9E79 <JS Object>
    2: create [C:websitssrccomponentsassessmenttestsnode_moduleswebdriveriobuildlibutilsRequestHandler.js:170] [pc=00000058FB2FCC0A] (this=00000362DEC984D1 <a RequestHandler with map 00000232920B51D9>,requestOptions=000002D782E76EB9 <String[30]: /session/:sessionId/screenshot>,data=00000329E7904189 <undefined>)
    3: arguments adaptor frame: 1->2
    4: screenshot [C:websitssr...

FATAL ERROR: CALL_AND_RETRY_LAST Allocation failed - JavaScript heap out of memory
```


The error message and some cursory Google searching pointed towards a memory problem, so I started looking at increasing the memory limit. However, this turned out to be a waste of time since the problem was quite simple:   

**Selenium Grid wasn't running on my server.** I started it up and everything worked fine.   

Bugs like this are frustrating because, if the error message had been "can't connect to Selenium Grid server", it wouldn't have taken any of my time to resolve. Hopefully though, now that I've documented it, other people can find this on Google and not waste _their_ time trying to fiddle with memory allocations.

[1]: https://gregtyler.co.uk/ssl-read-errno-10054/
