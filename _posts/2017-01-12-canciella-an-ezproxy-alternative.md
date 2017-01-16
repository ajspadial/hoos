---
layout: post
title:  "Canciella - an EZProxy alternative 1/n"
categories: canciella ezproxy
date:   2017-01-12 12:46:00 +0100
lang: en
ref: canciella
---

Last year I worked a little on an #FOOS alternative to EZProxy. My first naïve tentative was coded in PHP and you can't find it at [http://github.com/inia-es/canciella](http://github.com/inia-es/canciella). *Canciella* is the asturian for gate, gateway.

It lacks lots of details to be useful, but it gave me a glance about what we needed for a functional system. It was a prototype in the literal sense of the term.

Yesterday I started to work again on this project, and I took some notes about how EZProxy works, and what would my alternative would need.

# How does EZProxy work?

EZProxy is a rewriting proxy server. Those articles explain how it works.

[https://www.oclc.org/support/services/ezproxy/documentation/learn/overview.en.html](https://www.oclc.org/support/services/ezproxy/documentation/learn/overview.en.html)

[https://www.oclc.org/support/services/ezproxy/documentation/rewrite.en.html
](https://www.oclc.org/support/services/ezproxy/documentation/rewrite.en.html
)

[https://www.oclc.org/ezproxy/features.en.html](https://www.oclc.org/ezproxy/features.en.html)

[https://www.oclc.org/support/services/ezproxy/documentation/cfg/proxybyhostname.en.html](https://www.oclc.org/support/services/ezproxy/documentation/cfg/proxybyhostname.en.html)

I think OCLC is quite generous with all those technical details.

Here there are some more articles I explored in order to understand better what I wanted.

[https://en.wikipedia.org/wiki/EZproxy](https://en.wikipedia.org/wiki/EZproxy)

[https://en.wikipedia.org/wiki/Proxy_server](https://en.wikipedia.org/wiki/Proxy_server)

[https://en.wikipedia.org/wiki/Reverse_proxy](https://en.wikipedia.org/wiki/Reverse_proxy)

TL;DR; EZProxy is a rewriting proxy server with mixed features from forward and reverse proxies. I couldn't find a name for that, but [stone skipping](https://en.wikipedia.org/wiki/Stone_skipping) comes to my mind to explain it.

# My requirements

**Technical requirements**
* URL rewriting
* Content rewriting
* Domain cookies forwarding
* LDAP auth (other auths may be welcomed too)

**Non functional requirements**

* Easy installation and configuration

Requirements were quite clear, and I was thinking about what language to work with. Non functional requirements were the main point to take this decision.

After reading more and more about proxies, I changed my mind and decided to work on an Apache based proxy instead of writing my own module.

# The Apache approach

These is a list of Apache web server that provide the required features:
* URL rewriting
  * `mod_proxy`
  * `mod_rewrite`
  * `mod_proxy_http`
  * `mod_proxy_ftp`
  * `mod_proxy_connect`
* Authentication
  * `mod_authnz_ldap`
* Content rewriting
  * `mod_proxy_html`

I also wrote a small prototype to proxy domains the way EZProxy does. I know it's a naïve approach too, but it shows me how the full system may work. Future work will use Apache ENVVARS.
{% highlight apache %}
<VirtualHost *.canciella.net:80>
  RewriteEngine On

  RewriteCond ${SERVER_PROTOCOL} ^http$
  RewriteCond %{HTTP_HOST} ^(.*).canciella.net$
  RewriteRule ^(.*)$ http://%1/$0 [P]

  RewriteCond ${SERVER_PROTOCOL} ^https$
  RewriteCond %{HTTP_HOST} ^(.*).canciella.net$
  RewriteRule ^(.*)$ https://%1/$0 [P]

</VirtualHost>
{% endhighlight %}

Lastly those are the hand-writted notes I took during my research. I used a mix of English and Spanish, and probably they are useless for anyone else but my ownself of yesterday.
![EZProxy notes 1]({{ base.url }}/assets/img/alt-ezproxy-1.jpg)

![EZProxy notes 2]({{ base.url }}/assets/img/alt-ezproxy-2.jpg)
