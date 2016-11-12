Published: 2016-08-25T19:56:10.000Z
Author: Greg Tyler <greg@gregtyler.co.uk>
Standfirst: I came across an ENOENT error in Node, which was hard to decipher. Because explanations and advice across the Internet and sparsely laid out, I tried to compile all the reasons in one place.   \n  \nIncludes fixes and example code to regenerate each scenario.

Node.js ENOENT error explanations

Recently when using the `saveScreenshot` function of WebdriverIO, I came across the following Node error:   

    ENOENT: no such file or directory, open '{filepath}'

There are a lot of reasons this error could occur, all of which I looked at when trying to solve the problem. Because they are widely spread across the internet, and I couldn't find anyone addressing the problem I actually had, I thought I would enumerate them here.   

I've also given some [example code][1] for you to look at and play with. Reproducing the errors may help you figure out what causes them.   


## 1\. You're trying to read a file that doesn't exist


As the error message suggests, the file you're trying to read isn't there.   

**To fix:** Use the first parameter of the (e.g. `readFile`) function to catch the error. Perhaps use `fs.stat` or `fs.access` to check for access first.   


## 2\. You're trying to create a file in a _directory_ that doesn't exist


Node won't create your intermediary directories. So if you try to create a file `logs/pushout.log` and `logs` directory doesn't exist, you'll see this error.   

**To fix:** Create the `logs` directory first with `fs.mkdir`.   

## 3\. You're using a relative path incorrectly


This often is related to Issue 2, but without the developer's knowledge. Paths specified in `fs` functions are relative to the _currently executing script location_, not the file where the code is called from. So if `index.js` calls `processes/makeLogFile.js`, then the path used is relative to `index.js`.   

**To fix:** Either use `__dirname` to get the path that the code is being written in, and add to that, or add subdirectories as necessary.   

## 4\. You're trying to create a file that _can't_ exist


This was my problem. I had the following, fairly self-explanatory code:   

    driver.saveScreenshot('./screens/error-'   (new Date()).toISOString()   '.png');

This was supposed to create a unique screenshot in the `screens` directory but I got the ENOENT error instead.   

What I didn't account for is that `toISOString()` creates a time format with colons in it, and Windows will not allow colons in file names. So the error wasn't really saying that the file _doesn't_ exist, but that it simply _couldn't_.   

**To fix:** My fix was just using `replace(/:/g, '-')` to turn all the colons into hyphens. But, generally, fix this by making sure there are no disallowed characters in the file name.   


* * *



I hope these explanations help you. If you've got any questions, corrections or additions, please [open an issue][2] on the GitHub repository containing the example code.

[1]: https://github.com/gregtyler/enoent
[2]: https://github.com/gregtyler/enoent/issues
