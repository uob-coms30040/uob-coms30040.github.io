---
layout: default
title: schedule
---

{% capture nowunix %}{{'now' | date: '%s' }}{% endcapture %}
{% capture weekunix %}{{ 60 | times: 60 | times: 24 | times: 7 }}{% endcapture %}
{% capture startunix  %}{{ '2021-09-27' | date: '%s'  }}{% endcapture %}
{% capture startfridayunix  %}{{ '2021-10-01' | date: '%s'  }}{% endcapture %}

{% assign question_sheets = site.static_files | where: "question", true %}
{% assign answer_sheets = site.static_files | where: "answer", true %}

{% assign question_names = question_sheets | map: "basename" | join: "," | remove: "sheet" %}
{% assign answer_names = answer_sheets | map: "basename" | join: "," | remove: "sheet" %}

<img class="icon" src="assets/icons8-schedule-100.png"/>
<h2>At a glance</h2>

<div style="margin-left: 2em">
<p>Links to the lecture videos, problem sheets and their solutions will appear here as the unit progresses.  Check <a href="#wbyw">below</a> for the links alongside accompanying information.</p>
<br/>
<table class="pure-table-striped pure-table">
  <!-- <thead>
    <tr> 
      <th>Week</th><th>By</th><th>Theme</th><th>Videos</th><th>Problems</th>
    </tr>
  </thead> -->
  <tbody>
    <tr>
      <td colspan="3" style="text-align:center">Welcome Week</td>
    </tr>
    {% for week in site.data.weeks %}
    {% if week.num == 6 %}
    <tr>
      <td colspan="3" style="text-align:center"><a href="#week{{ week.num }}">Reading Week</a></td>
    </tr>
    {% elsif week.num == 9 or week.num == 10 or week.num == 11 %}
    <tr>
      <td colspan="3" style="text-align:center; color:grey">-</td>
    </tr>
    {% elsif week.num == 12 %}
    <tr>
      <td colspan="3" style="text-align:center">Revision Week</td>
    </tr>
    {% else %}
    {% capture this_week_unix %}{{ week.num | minus: 1 | times: weekunix | plus: startunix }}{% endcapture %}
    {% capture next_week_unix %}{{ week.num | times: weekunix | plus: startunix }}{% endcapture %}
    {% capture next_friday_unix %}{{ week.num | times: weekunix | plus: startfridayunix }}{% endcapture %}
    <tr> 
      <td><a href="#week{{ week.num }}">Week {{ week.num }}: {{week.theme}}</a></td>
      <td>
        {% if this_week_unix <= nowunix %}
          {% for l in week.core %}
            {% assign part_num = 1 %}{% for v in l.vids %}<a href="{{ v.url }}" target="_blank">C{{ l.lec }}.{{ part_num }}</a> {% assign part_num = part_num | plus: 1 %}{% endfor %} // 
          {% endfor %}
          {% if week.num != 8 %}
          <a href="{{ week.optional.url }}" target="_blank">S{{ week.num }}</a>
          {% endif %}
        {% endif %}
      </td>
      <td>
        {% if this_week_unix <= nowunix %}
        <a href="questions/sheet{{ week.num }}.pdf" target="_blank">qns</a>
        {% endif %}
        {% if next_friday_unix <= nowunix %}
         // <a href="answers/sheet{{ week.num }}.pdf" target="_blank">ans</a>
        {% endif %}
      </td>
    </tr>
    {% endif %}
    {% endfor %}
  </tbody>
</table>
</div>

<hr/>

<img class="icon" src="assets/icons8-calendar-100.png"/>
<h2>Day by day</h2>

<div style="margin:0em 2em 0em 2em">
  <div>It is helpful to think of each weeks of this unit as running Tuesday midday until the following Tuesday midday.  The pattern of working described below is recommended.</div>
  <div><img src="assets/weekly.svg" style="margin:2em 1em 2em 1em; max-width:40em" width="100%"/></div>
  <div>
    <b style="margin:1em">A</b> Watch the two recorded lectures (typically 4 videos) OR attend the two core lectures (seminar timetable slot); watch the supplementary lecture (video).<br/>
    <b style="margin:1em">B</b> Attend the problem class to discuss solutions to the problems of the <i>previous</i> week.<br/>
    <b style="margin:1em">C</b> Work on the problem sheet for at least 2 hours.<br/>
    <b style="margin:1em">D</b> Submit your answers to the problems to Eddie by midday Tuesday.
  </div>
</div>

<hr/>

<img class="icon" src="assets/icons8-timeline-week-100.png">
<h2 id="wbyw">Week by week</h2>

<div style="margin-left: 2em">

{% for week in site.data.weeks %}
{% unless week.num == 12 or week.num == 9 or week.num == 10 or week.num == 11 %}

<h3 id="week{{ week.num }}">Week {{ week.num }}: {{ week.theme }}</h3>
<i>{{ week.description | markdownify }}</i>
  <ul>
    {% capture this_week_unix %}{{ week.num | minus: 1 | times: weekunix | plus: startunix }}{% endcapture %}
    {% capture next_week_unix %}{{ week.num | times: weekunix | plus: startunix }}{% endcapture %}
    {% capture next_friday_unix %}{{ week.num | times: weekunix | plus: startfridayunix }}{% endcapture %}
    {% if this_week_unix <= nowunix %}
    <li>
      <p>Videos:<br/><br/>
      {% for l in week.core %}
      - Core Lecture {{ l.lec }}
      {% assign part_num = 1 %}
      <ul>
        {% for v in l.vids %}
          <li>
            <a href="{{ v.url }}" target="_blank">Part {{ part_num }}</a>: {{ v.dsc }} <i>({{ v.len }} mins)</i>
          </li>
          {% assign part_num = part_num | plus: 1 %}
        {% endfor %}
      </ul>
      {% endfor %}
      {% if week.num != 8 %}
      - Supplementary
      <ul>
        <li><a href="{{ week.optional.url }}" target="_blank">Part 1</a>: {{ week.optional.dsc }} <i>({{ week.optional.len }} mins)</i>
        </li>
      </ul>
      {% endif %}
      </p>
    </li>
    <li>
      Problems: <a href="questions/sheet{{ week.num }}.pdf" target="_blank">qns</a>{% if next_friday_unix <= nowunix %} / <a href="answers/sheet{{ week.num }}.pdf" target="_blank">ans</a>{% endif %}
    </li>
    <li>
      Slides: 
        {% if week.num == 1 %}
          <a href="slides/P2.pdf" target="_blank">2</a>
           / <a href="slides/P3.pdf" target="_blank">3</a>
            <a href="slides/P4.pdf" target="_blank">4</a>
        {% else %}
          <a href="slides/P{{ week.num | times: 4 | minus: 3 }}.pdf" target="_blank">{{ week.num | times: 4 | minus: 3 }}</a>
           <a href="slides/P{{ week.num | times: 4 | minus: 2 }}.pdf" target="_blank">{{ week.num | times: 4 | minus: 2 }}</a>
          / <a href="slides/P{{ week.num | times: 4 | minus: 1 }}.pdf" target="_blank">{{ week.num | times: 4 | minus: 1 }}</a>
           <a href="slides/P{{ week.num | times: 4 }}.pdf" target="_blank">{{ week.num | times: 4 }}</a>
        {% endif %}
    </li>
    {% endif %}
  </ul>

{% endunless %}
{% endfor %}
</div>

<hr/>

<div style="text-align: center; margin:0em 2em 2em 2em">
  Icons in this course are from the '<a href="https://icons8.com/icons/carbon-copy" target="_blank">Hand Drawn</a>' icon collection by <a href="https://icons8.com/" target="_blank">Icons8</a>.
</div>