---
layout: default
title: papers
---

<img class="icon" src="assets/icons8-report-card-100.png"/>
<h2>Practice Papers</h2>

A selection of past papers and their answers.

{% assign paper_answers = site.static_files | where: "exam", true %}

<ul>
  {% for a in paper_answers %}
    {% assign paper_questions = a.basename | replace: '-answers', '' | replace: '-', ' ' %}
    {% assign paper_questions_path = a.name | replace: '-answers', '' %}
    <li><a href="papers/{{ paper_questions_path }}" target="_blank">{{ paper_questions }}</a> (<a href="{{ a.path }}"  target="_blank">answers</a>)</li>
  {% endfor %}
</ul>