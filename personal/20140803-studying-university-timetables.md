Published: 2014-08-03T14:49:56.000Z
Author: Greg Tyler <greg@gregtyler.co.uk>
Standfirst: I recently worked on a project at work to bring course timetables more easily to students through a new course timetable browser website. This got me interested in a few different things to do with University timetables, including how events are distributed through the week. The result of that interest is a new website where you can explore how busy the University's timetable is under certain conditions.

Studying University timetables

I recently worked on [a project at work][1] to bring course timetables more easily to students through a new [course timetable browser][2] website. This got me interested in a few different things to do with University timetables, including how events are distributed through the week. The result of that interest is a new website where you can explore how busy the University's timetable is under certain conditions.   

**Data disclaimer:** The data used in this site is provided by a snapshot at a particular time. It wasn't 100% reliable at the time I pulled it and it certainly isn't reliable now. All the statistics here should be seen as indicators, not accurate values.   

If you want to get your hands dirty, you can click the button below to have a play for yourself. But keep reading for a few interesting results I found.   

[Explore the timetables yourself][3]   

## The global grid

![The global grid](/tt-default.png ":right The "global grid"")

The default grid (with no filters applied) already shows some interesting patterns. Firstly we can see that there's a clear lunch-break in the middle of the day from 1 'til 2. This must have stuck in my mind because still now I normally take my lunch-break in that hour. There's also a noticeable lack of courses on Wednesday afternoons. This seems to be [common at other universities too][5] and I've been under the impression it's for people engaged in sports. Also, a midweek break is probably good for morale.   

My favourite little caveat about the global grid is the drop in events on Friday afternoons, which I'm sure students will be very happy to acknowledge.   


## Optional classes


At the top of the Options section, you can toggle on and off "optional" classes. These are generally events where students get to pick a class from a selection of slots throughout the week to suit their timetable best. I haven't included them by default for a couple of reasons:   



* Under some filters they can quadruple the events.   
* Being optional, they're not designed to balance as well through the week. Some are more haphazard, so don't reflect the intentional timetabling design.   

I recommend playing with them though, it can yield some interesting results.   


## Specific schools

![Geosciences timetable](/tt-gesc.png ":left [School of Geosciences](http://play.gregtyler.co.uk/timetable/#filter=school,school=SU849)")
![Mathematics timetable](/tt-math.png ":right [School of Mathematics](http://play.gregtyler.co.uk/timetable/#filter=school,school=SU253)")

-----

Not all schools follow the global grid as well as others. Whilst the School of Geosciences provides a very good example of sticking to the default, the School of Mathematics bite completely against the curve having busier Friday afternoons than Tuesdays.   


## Harder courses are more often in the afternoon

![Level 10 timetable](/tt-level-10.png ":left [Level 10 courses](http://play.gregtyler.co.uk/timetable/#filter=credit_level,credit_level=10)")
![Level 11 timetable](/tt-level-11.png ":right [Level 11 courses](http://play.gregtyler.co.uk/timetable/#filter=credit_level,credit_level=11)")

-----

I'm not sure if there's really enough statistical significance to make this claim but I'm going to anyway. Looking at the charts above, you should be able to see that level 10 courses tend to occur more in the morning than the afternoon whilst level 11 courses (which are harder) occur more in the afternoon. I guess this makes sense, as then students will be progressively getting challenged more throughout the day rather than burning out earlier on.   

## Tutorials happen "later"

![Tutorials timetable](/tt-tutorials.png ":right [Tutorials](http://play.gregtyler.co.uk/timetable/#filter=type,type=Tutorial,optional=1)")

Perhaps the least surprising thing I noticed was that tutorials happen "later"; be that later in the day or later in the week, they tend to be towards the right and bottom edges of the grid (except that impressive outlier on Wednesday mornings). Again, this is totally believable because someone scheduling a class might like to keep it within the week, teaching content at the start and having a tutorial at the end. Of course, this wouldn't work if _every_ class had that setup, hence the rest of the grid still being fairly full throughout the week.



[Explore the timetables yourself][3]   


Did you find any interesting patterns? Let me know in the comments below!

[1]: http://www.appsdev.is.ed.ac.uk/blog/?p=163
[2]: https://browser.ted.is.ed.ac.uk/
[3]: http://play.gregtyler.co.uk/timetable/
[4]: http://play.gregtyler.co.uk/timetable/#
[5]: http://www.thestudentroom.co.uk/showthread.php?t=1720752
