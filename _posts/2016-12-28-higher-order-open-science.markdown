---
layout: post
title:  "Higher-order Open Science?"
date:   2016-12-28 12:47:52 +0100
categories: hoos meta
lang: en
ref: higher-order
---
Welcome to this blog. The main reason I'm writing it is to serve as an **open notebook** for my PhD. I'll write on its goals soon, but meanwhile let's say it's about tools for research data management plans.

But, what does Higher-order Open Science mean? Probably you guessed it's a pun. One for people with a background in Computer Science.

<blockquote class="twitter-tweet" data-lang="es"><p lang="en" dir="ltr">often, i wish there were a file in OSS called ORIGINSTORY.md, explaining why you named your project as such, what puns you tried to play on</p>&mdash; Aure Moser (@auremoser) <a href="https://twitter.com/auremoser/status/748326674572390400">30 de junio de 2016</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

OK [@auremoser](https://twitter.com/auremoser), here comes my explanation. In Computer Science, a higher-order function is one that returns a function as result, or can take one or more functions as arguments. Example:  
```javascript
function createMult(m) {
  return function (a) {
    return a * m;
  };
}

var mult2 = createMult(2);
mult2(3);  // result is 6
```

In this example, the `createMult()` function will return a diferent function for every given value of `m`.

My Higher-order Open Science is an open science effort (this blog/notebook) that will return (I expect) valuable results for open science.

This is the very first step of my trip. I wish you all enjoy it as much as I'll do. There's no place yet for comments in this notebook, but feel free to contact via [twitter](http://twitter.com/ajspadial), [email](hoos@spadial.com) or even try with a [github issue](https://github.com/ajspadial/hoos/issues).
