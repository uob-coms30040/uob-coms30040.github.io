---
layout: default
title: Course Materials
nav_order: 2 
---

## :green_book: Lecture Notes

  There is a complete set of lecture notes that contains everything you need for the unit.  I generally update the notes during term to correct mistakes and to make small improvements, so you will want to check here regularly for changes.

  The latest version of the lecture notes can be found [here](assets/notes.pdf){: target="_blank" }.

<!-- <table class="pure-table-striped pure-table">
  <thead>
  <tr>
    <th>Date</th><th>Change</th><th>Thanks to</th>
  </tr>
  </thead>
  <tbody>
  </tbody>
  </table> -->


## :page_with_curl: Problem Sheets

  One problem sheet is released each week.  The deadline for marking is end of the day on Monday the following week.  Please submit your work to your class tutor (see below) by email with subject "[TLC] Week N", where N is the number of the week containing the deadline, usually this will be the week in which you send the email.

- If you are in Group 1 (Ada Lovelace SM4), please email a pdf to Amos Holland (amos.holland.2021).
- If you are in Group 2 (Ada Lovelace SM3), please email a pdf to Tomos Sherlock (he22266).
- If you are in Group 3 (Ada Lovelace PC6), please email a pdf to Tom Divers (tom.divers).
- If you are in Group 4 (Ada Lovelace PC5), please email a pdf to Luna Abumatar (vv22872).

  <table class="pure-table-striped pure-table">
    <thead>
      <tr> 
        <th style="text-align:center">University Week</th>
        <th style="text-align:center">Problems / Solutions</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td colspan="2" style="text-align:center">Welcome Week</td>
      </tr>
{% for calendar_week in (1..12) %}
  {% if calendar_week <= 6 %}
    {% assign logical_week = calendar_week %}
  {% else %}
    {% assign logical_week = calendar_week | minus: 1 %}
  {% endif %}
  {% if calendar_week == 6 %}
    <tr>
      <td colspan="2" style="text-align:center">Reading Week</td>
    </tr>
  {% elsif calendar_week >= 9 and calendar_week < 12 %}
    <tr>
      <td colspan="2" style="text-align:center">Coursework Week</td>
    </tr>
  {% elsif calendar_week == 12 %}
    <tr>
      <td colspan="2" style="text-align:center">Revision Week</td>
    </tr>
  {% else %}
    <tr>
      <td style="text-align:center">Week {{ calendar_week }}</td>
      <td style="text-align:center">
    {% capture qns_name %}/questions/sheet{{ logical_week }}.pdf{% endcapture %}
    {% capture ans_name %}/answers/sheet{{ logical_week }}.pdf{% endcapture %}
    {% assign qns = false %}
    {% assign ans = false %}
    {% for static_file in site.static_files %}
      {% if static_file.path == qns_name %}
        {% assign qns = true %}
      {% endif %}
      {% if static_file.path == ans_name %}
        {% assign ans = true %}
      {% endif %}
    {% endfor %}
    {% if qns %}
        <a href="{{ qns_name | remove_first: "/" }}" target="_blank">qns</a>  
    {% endif  %}
    {% if ans %}
        / <a href="{{ ans_name | remove_first: "/" }}" target="_blank">ans</a>  
    {% endif %}
      </td>
    </tr>
  {% endif %}
{% endfor %}
    </tbody>
  </table>