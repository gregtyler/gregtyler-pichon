Published: 2013-11-09T16:38:34.000Z
Author: Greg Tyler <greg@gregtyler.co.uk>
Standfirst: Recently I've been getting a lot of people posting links to Upworthy articles on Facebook. I realised their headlines often followed a similar style so decided to make a little application to generate them.

Upworthy Headline Generator

Recently I've been getting a lot of people posting links to [Upworthy][1] articles on Facebook. I realised their headlines often followed a similar style so decided to make a little application to generate them.   

You can check out the generator at the link below:   

<http://play.gregtyler.co.uk/upworthy/>


![Screenshot of Upworthy Headline Generator](/upworthy.png "The generator at work")


## Technical stuff


A quick technical note: The code that pulls out random terms is weighted in this (which is why some people and events show up more or less regularly than others). To do this, every term is an object with a label and a weight. I take the sum of all the weights then generate a random number, `rand`, between 0 and that. The code then iterates through the array of objects and subtracts the weight of each one from the `rand`. When `rand` falls below 0, we're at the object we want.   

I actually had the code for this sitting around already for another project I'm working on, which was timely.   


To learn something new, why not visit [upworthy.com][1]?

[1]: https://www.upworthy.com/
