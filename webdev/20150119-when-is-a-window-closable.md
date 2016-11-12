Published: 2015-01-19T14:40:18.000Z
Author: Greg Tyler <greg@gregtyler.co.uk>

When is a window closable?

JavaScript has a function `window.close()` which, under certain circumstances, will close the current window. However sometimes you'll run into an error like:   

> Scripts may close only the windows that were opened by it.

In this situation, your helpful "close this window" buttons don't work.   

We have exactly this in situation in a current project I work on, where we ask people to open a link in a new tab so that `window.close()` will take them back out of it.   

The problem we had was knowing when `window.close()` will work. If you open a new window with JavaScript (using `window.open()` no less) then it you're fine. But if you right click and open in a new tab, then submit a form, it won't be happy. So when is a window closable?   

My first thought was the `opener` property of `window` which presumably would hint at where the window came from and - hence - what can close it. So I made a table of various difference situations which I experimented with in each of the major desktop browsers (Chrome, Firefox, IE). Find the table below and some terminology explained beneath it.   

<table class="results-table">
<tbody><tr>
<th rowspan="2" style="width:25%"></th>
<th colspan="2" style="background-color:#DDD;">Chrome 39</th>
<th colspan="2" style="background-color:#F70;">Firefox 31</th>
<th colspan="2" style="background-color:#8DF;">Internet Explorer 11 \*</th>
</tr>
<tr>
<th>Click</th>
<th>New tab</th>
<th>Click</th>
<th>New tab</th>
<th>Click</th>
<th>New tab</th>
</tr>
<tr>
<th>Child</th>
<td class="bad">N</td>
<td>N</td>
<td class="bad">N</td>
<td class="bad">N</td>
<td>U</td>
<td>U</td>
</tr>
<tr>
<th>Child (\_blank)</th>
<td>W</td>
<td>W</td>
<td>W</td>
<td class="bad">N</td>
<td>W</td>
<td>U</td>
</tr>
<tr>
<th>Child (JS)</th>
<td colspan="2">W</td>
<td colspan="2">W</td>
<td colspan="2">W</td>
</tr>
<tr>
<th>Through form</th>
<td class="bad">N</td>
<td class="bad">N</td>
<td class="bad">N</td>
<td class="bad">N</td>
<td>U</td>
<td>U</td>
</tr>
<tr>
<th>Through form (\_blank)</th>
<td>W</td>
<td>W</td>
<td>W</td>
<td class="bad">N</td>
<td>W</td>
<td>U</td>
</tr>
<tr>
<th>Through form (JS)</th>
<td colspan="2">W</td>
<td colspan="2">W</td>
<td colspan="2">W</td>
</tr>
<tr>
<th>Through link</th>
<td class="bad">N</td>
<td class="bad">N</td>
<td class="bad">N</td>
<td class="bad">N</td>
<td>U</td>
<td>U</td>
</tr>
<tr>
<th>Through link (\_blank)</th>
<td>W</td>
<td>W</td>
<td>W</td>
<td class="bad">N</td>
<td>W</td>
<td>U</td>
</tr>
<tr>
<th>Through link (JS)</th>
<td colspan="2">W</td>
<td colspan="2">W</td>
<td colspan="2">W</td>
</tr>
</tbody></table>

**Notes:**   
"Child" means that the user was taken straight to a page with a close button on it. "Through form" means they were taken to a page which had a form submission before the close page. "Through link" means that they were taken to a page with a link to the close page.   

"(\_blank)" means that the window was opened using an `<a>` tag with the `target="_blank"` attribute. "(JS)" means that the window was opened with the `window.open` function. All other examples were `<a>` tags with no attributes.   

The colour of each cell is whether or not it could successfully be closed. The text denotes the value of `window.opener`. Where the text is "N", this value was `null`, where it is "W" it returned a `window` object. Where it is "U", it returned `undefined`.   

* Internet Explorer always prompts you to confirm the window closure.   




## What have we learnt?


Firstly, Internet Explorer is noticeably unusual. It returns `undefined` rather than `null` and then lets you close the window no matter what situation you're in (though with a prompt). Secondly, and important for my situation, asking people to open a new tab doesn't mean we'll be able to close it. As soon as they follow a link or submit a form, both Firefox and Internet Explorer lose control.   

In a goal to find some sort of check whether a window is closable, I can recommend the following from my results:   

```js
if( typeof window.opener === 'object' && window.opener instanceof Window ) {    // We can certainly use window.close} else {    // We can't be sure window.close will work}
```

This is (from the experience above) a cross-browser way to be certain that `window.close` will work, without any browser sniffing.   


Are my figures right? Any views on this? Comment below!

<style type="text/css">.results-table {
width:100%;
border-collapse:collapse;
table-layout:fixed;
}
.results-table th, .results-table td {
padding:.5em;
border:1px solid #CCC;
text-align:center;
}
.results-table td {
background-color: #9D9;
color: darkgreen;
font-weight: bold;
}
.results-table td.bad {
background-color: #FD6E6E;
color: darkred;
}</style>
