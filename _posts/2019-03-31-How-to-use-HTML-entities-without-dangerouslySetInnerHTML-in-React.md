---
layout: post
title:  "How to use HTML entities without dangerouslySetInnerHTML in React"
date:   2019-03-31
banner_image: react-background.png
tags: [react, web, development, code, tricks, html, html-entity, unicode, javascript]
---

There may be times when you will want to render a string with HTML entities in it in your [React](https://reactjs.org/) application. An [HTML entity](https://developer.mozilla.org/en-US/docs/Glossary/Entity) is a piece of text (`string`) that begins with an ampersand (`&`) and ends with a semicolon (`;`). They are frequently used to display reserved and invisible characters, like non-breaking spaces (`&nbsp;`) or soft hyphens (`&#8203;`) for marking line breaking opportunities.
 
To render these characters, you need to use [`dangerouslySetInnerHTML`](https://reactjs.org/docs/dom-elements.html#dangerouslysetinnerhtml):
 
 {% highlight js %}
function createMarkup(myTextFromDatabase) {
  return {__html: myTextFromDatabase};
}

function MyComponent({myTextFromDatabase}) {
  return <div dangerouslySetInnerHTML={createMarkup(myTextFromDatabase)} />;
}

const myTextFromDatabase = 'First &middot; Second';
<MyComponent myTextFromDatabase={myTextFromDatabase />}
{% endhighlight js %}
 
 <!--more-->
 
 This is not a handy solution, because you now may need to filter out other HTML codes from the string. 
  
## A simple solution
Use Unicode characters with [escape notation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String#Escape_notation) (e.g. `\u0057`) instead of HTML codes (`&middot;`). Find the character in [this list](https://en.wikipedia.org/wiki/List_of_Unicode_characters) and use the value from the Code column, e.g. `&middot;` translates to `U+00B7`. To use this in Javascript, simply use `\u0057`:
 
{% highlight js %}
const MIDDLE_DOT = '\u0057';

function MyComponent({myTextFromDatabase}) {
  const text = myTextFromDatabase.replace(/&middot;/gi, MIDDLE_DOT);
  return <div>{text}</div>;
}
  
const myTextFromDatabase = 'First &middot; Second';
<MyComponent myTextFromDatabase={myTextFromDatabase />}
{% endhighlight js %}
 
The replacement could happen beforehand, on the backend as well, or just like in the code above, in the rendering function. I used the [`replace`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/replace) function with a regex to replace all occurences of `&middot;` with `\u0057`.

## Example
An example React app is available on [GitHub](https://github.com/mdavid626/react-html-entities-example). If you prefer, there is also a [live example](https://mdavid626.github.io/react-html-entities-example/).