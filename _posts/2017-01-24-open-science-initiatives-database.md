---
layout: post
title: "Open Science initiatives database"
date:   2017-01-24 14:10:52 +0100
categories: business  database non-profit tools
lang: en
ref: open-science-initiatives-database
---

Today I read [this article](http://www.forbes.com/sites/drsarahbond/2017/01/23/dear-scholars-delete-your-account-at-academia-edu/#25df017f2ee0) about quiting Academia.edu. I started to think what makes different Academia.edu from other profit driven companies like Github - encouraged as an advantage of Zenodo in the same article. Later in the day I learn PaperHive was a thing (a company, in fact). Lurking their site I wondered how they were different from Hypothes.is (a non-profit). That drove me to discover the Annotating All Knowledge coalition. And I moved on to start this database.

This database is a work in progress. I wanted to map the open science ecosystem for a time. This is still very biased, though I don't know how. I just took the list of participants in the [Annotating All Knowledge coalition](https://hypothes.is/annotating-all-knowledge/) and added some information to some of them. You can contribute at [@ajspadial/open-sicence-initiatives](https://github.com/ajspadial/open-science-initatives), if you feel like it.

Disclaimer: I'm especially interested in tools and services, so maybe this database will drift towards them, or prioritize them, in the future.

<table style="border:1px solid; border-collapse: collapse; border-spacing: 0;">
  <tr>
    <th style="border: 1px solid;">Name</th>
    <th style="border: 1px solid;">Type</th>
    <th style="border: 1px solid;">Scope</th>
    <th style="border: 1px solid;">url</th>
    <th style="border: 1px solid;">Focus</th>
  </tr>
{% for initiative in site.data.initiatives %}
<tr>
  <td style="border: 1px solid;">{{ initiative.name }}</td>
  <td style="border: 1px solid;">{{ initiative.type }}</td>
  <td style="border: 1px solid;">{{ initiative.scope }}</td>
  <td style="border: 1px solid;" ><a href = "{{ initiative.url }}">{{ initiative.url }}</a> </td>
  <td style="border: 1px solid;">{{ initiative.focus }}</td>
</tr>
{% endfor %}
</table>
