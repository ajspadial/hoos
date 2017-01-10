---
title: HOWTO start, stop, debug CKAN
layout: post
lang: en
ref: start-stop-ckan
categories: ckan sysadmin
---
<small><em>
:es: Breves instrucciones para arrancar y deterner un servidor CKAN, especialmente en modo `DEBUG`.  
</em></small>

## Start a production environment
A CKAN production environment is served through a web server. This site [http://docs.ckan.org/en/latest/maintaining/installing/deployment.html#install-apache-modwsgi-modrpaf](http://docs.ckan.org/en/latest/maintaining/installing/deployment.html#install-apache-modwsgi-modrpaf) includes detailed instructions for configuring Apache as the web server provinding access to your CKAN installation.

You can avoid usging the `nginx` server, by making the apache site to listen to any connection on port 80.

{% highlight apache %}
<VirtualHost *:80>
  # ...
</VirtualHost>
{% endhighlight %}

## Stopping a production environment

To stop a production environment you can:
* stop the Apache/Nginx server (the one woring at port 80, and listening to connections from everywhere),  
{% highlight bash %}
  $ sudo service apache2 stop
{% endhighlight %}
* or, disable the ckan site
{% highlight bash %}
  $ sudo a2dissite ckan
  $ sudo service apache2 reload
{% endhighlight %}

## Starting a debug environment

Days ago I twitted on how to start CKAN in debug mode.

<blockquote class="twitter-tweet" data-lang="es"><p lang="en" dir="ltr">TYL HOWTO run <a href="https://twitter.com/hashtag/CKAN?src=hash">#CKAN</a> on debug mode: `paster plugin=ckan serve &lt;ckan_conf.ini&gt;` <a href="https://t.co/5ppEsajSvh">pic.twitter.com/5ppEsajSvh</a></p>&mdash; Antonio Sánchez-Pad. (@ajspadial) <a href="https://twitter.com/ajspadial/status/790947600769900544">25 de octubre de 2016</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

After doing so, your test CKAN will be available at `http://localhost:5000`

You'll have to activate your CKAN development environment before running `paster`. This site [http://docs.ckan.org/en/latest/maintaining/installing/install-from-source.html](http://docs.ckan.org/en/latest/maintaining/installing/install-from-source.html) includes detailed instructions.

These are the needed steps:
{% highlight bash %}
$ source pyenv/bin/activate
(pyenv)$ paster serve /etc/ckan/default/production.ini &
{% endhighlight %}

## Stopping a debug environment

You may kill the paster serve process.

{% highlight bash %}
$ ps -a | grep paster
$ kill -9 <paster_id>
{% endhighlight %}

If you need to restart you can try `paster serve --reload <settings.ini>`
