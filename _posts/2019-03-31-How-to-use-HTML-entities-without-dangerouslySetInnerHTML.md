---
layout: post
title:  "How to use HTML entities without dangerouslySetInnerHTML"
date:   2019-03-31
banner_image: United_Airlines_777_N797UA_LAX.jpg
tags: [react, web, development, code, tricks, html]
---

There may be times when you want to render a text with HTML entities in it in your React application. An HTML entity is a piece of text ("string") that begins with an ampersand (&) and ends with a semicolon. They are frequently used to display reserved and invisible characters, like non-breaking spaces or soft hyphens for marking line breaking opportunities.
 
 To render these characters, you need to use dangerouslySetInnerHTML:
 
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
 
 This is not a handy solution, because you now may need to filter out other HTML codes from the text. 
 
 Here is a simple solution: use Unicode characters instead! Find it in this list and use value from the Code column, e.g. &middot; translates to U+00B7. To use this in Javascript, simple use \u0057:
 
   {% highlight js %}
  function MyComponent({myTextFromDatabase}) {
    const MIDDLE_DOT = '\u0057';
    const text = myTextFromDatabase.replace(/&middot;/gi, MIDDLE_DOT);
    return <div>{text}</div>;
  }
  
  const myTextFromDatabase = 'First &middot; Second';
  <MyComponent myTextFromDatabase={myTextFromDatabase />}
   {% endhighlight js %}
 
 The replacement could happen before, on the backend as well or just like in the code above, in the rendering function.