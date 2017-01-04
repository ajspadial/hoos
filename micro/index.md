---
layout: page
title: Fast notes
---

AKA tweets
  <ul class="tweets-list">
    {% assign tweets = site.micro | sort: "date" | reverse %}
    {% for tweet in tweets %}
      <li {% if tweet.twitter-id %} id="{{tweet.twitter-id}}" {% endif %}>
        <span class="post-meta">
          {% if tweet.twitter-id %}
            <a href="https://twitter.com/ajspadial/status/{{ tweet.twitter-id }}">{{ tweet.date | date: "%b %-d, %Y"}}</a>
          {% else %}
            {{ tweet.date | date: "%b %-d, %Y"}}
          {% endif %}
        </span>

        <blockquote>{{tweet.content}} </blockquote>
      </li>
    {% endfor %}
  </ul>
