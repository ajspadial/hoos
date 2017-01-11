---
layout: post
title:  "HOWTO: add a Zotero link to a Jekyll blog"
date:   2017-01-03 16:47:52 +0100
categories: hoos meta jekyll
lang: en
ref: add-zotero-link
---

*This is a guide for Jekyll v3.3.1 and later. It may work on other Jekyll v3, but I haven't tested it.*

This a short recipe telling how to add a zotero link (or whatever you want) to a Jekyll blog.
For those who don't know Jekyll is a blog engine, you can learn more about it in [its website](https://jekyllrb.com/)
and have a free Jekyll site [using github](https://help.github.com/articles/using-jekyll-as-a-static-site-generator-with-github-pages/).

If you take a look at the footer of this blog, you'll see a set of links like this one.  
![The HOOS footer link]({{site.url}}/assets/img/jekyll-links.png)

The standard jekyll blog provides links for twitter and/or github accounts, but you can easily customize it. Follow these steps:

## Find your theme

Take a look to your `_config.yml`. There you'll find a `theme` tag. This is the name of your theme (mansplaining here?). The standard theme
for jekyll is `minima`.

## Find your theme path

Once we know our theme, we have to find where in our system it is. In a system console, go to your blog folder a use this command `bundle show minima`. Change `minima` if you discovered other theme in your `_config.yml` (mansplaining again?). Bundle will answer with a sytem path, for example:

{% highlight windows %}
  c:/tools/ruby23/lib/ruby/gems/2.3.0/gems/minima-2.1.0
{% endhighlight %}

<small>Yes I'm on Windows 10. Don't judge me by this, please.</small>

## Analize your template

On that theme folder, there are several templates jekyll uses for creating your blog. The one we need now is in ```_layouts/default.html```. It's used as template for most Jekyll pages. If you want to modify something that appears in every page in your site, like the footer, probably you'll find it in your `default.html`

<pre>

    {% include footer.html %}

</pre>

## Modify your footer template

## Create a zotero template
