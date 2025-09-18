---
layout: default
title: welcome
---

![i icon](assets/icons8-info-100.png){: .icon }
## Welcome

Welcome to the home of *COMS30040: Types and Lambda Calculus*.  This unit introduces you to the mathematical foundations of programming languages, with an emphasis on functional programs and type systems.  

Our focus will be on the *expressive power* of the language with and without types; the *algorithmics* of assigning types to terms; and the close *correspondence* with logic and proof.  A secondary goal is to teach you to write mathematical proofs.

This unit prepares you for *COMSM0067: Advanced Topics in Programming Languages* in the programming languages theme in your fourth year, but is not a prerequesite.  It shares themes and techniques with the unit *MATH30100: Logic*.

* * *

![contacts](assets/icons8-smartphone-tablet-100.png){: .icon }
## Contacts

The unit is run by [Steven Ramsay][1] (lectures) and Luna Abumatar, Amos Holland, Tomos Sherlock and Tom Divers (classes).

[1]: https://sjrsay.github.io

Outside of lectures and classes, if you have any questions about the material, the way the unit runs or are just curious about programming language theory or logic more generally, then please post to the General channel of the [Team](https://teams.microsoft.com/l/channel/19%3AmqnhGdYxFVZnIkAmCpOFOnM_OjWSvbtbcQwIzAA4gg81%40thread.tacv2/General?groupId=afade0de-43f6-49e7-9b2c-f875492929a1&tenantId=b2e47f30-cd7d-4a4e-a5da-b18cf1a4151b){: target="_blank" }.  We would like to hear from you!

* * *

![materials](assets/icons8-briefcase.svg){: .icon }
## Materials

### Lecture Notes
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

  For additional reading, you might like to consult the following, but note there will be significant differences compared to how we set things up in our unit:
    
  * For more on PCF, consult Chapter 2 of Mitchell's *Foundations for Programming Languages*, this chapter is freely [downloadable](https://theory.stanford.edu/people/jcm/books/fpl-chap2.ps) as a sample of the book.
  * If you want to learn more about this style of proof, you could try learning to use an interactive theorem prover, like [Lean](https://lean-lang.org/introduction_to_lean/).  These kinds of tools take the relationship between programming and proving to the next level, by giving a precisely defined programming language in which you can write your proofs, which can then be checked to be correct by the tool.
  * The ultimate reference on pure, untyped lambda calculus is Barendregt's book *The lambda calculus: its syntax and semantics*, available in the [library](https://bris.on.worldcat.org/oclc/822020339).
  * A gentler introduction, which also includes some treatment of types is Hindley & Seldin's *Lambda Calculus and Combinators: An Introduction*, available in the [library](https://bris.on.worldcat.org/oclc/247301736).


### Problem Sheets
  One problem sheet is released each week.  The deadline for marking is end of the day on Monday the following week.  Please submit your work to your class tutor (see below) by email with subject "[TLC] Week N", where N is the number of the week containing the deadline, usually this will be the week in which you send the email.

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

* * *

![schedule](assets/icons8-schedule-100.png){: .icon }
## Schedule

You should expect to spend around *6-7 hours per week* working on this unit.

  * __Lectures (2 hr).__ Excepting Week 1 (which has an additional Monday lecture), There are two lectures per week, given on campus:
      - Monday at 4pm in Queens 1.06
      - Thursday at 2pm in Queens 1.18
    Each lecture corresponds to one chapter in the lecture notes (see above).

  * __Reading (0-1 hr).__ You will probably find that you need to revisit the material from the lectures in conjunction with doing the problem sheets.  There is a complete set of [lecture notes](assets/notes.pdf){: target="_blank" } that covers everything to need to know on this unit.  
 
  * __Problem Sheets (2-3 hr).__ You will only learn by completing the problem sheets.  There is one sheet released each week.  You should aim to spend *at least two hours* working on each problem sheet each week, in your own time.  You will need to consult the course [lecture notes](assets/notes.pdf){: target="_blank" } whilst attempting the problems.  You should complete the Week n problem sheet and submit it no later than the end of the (following) Monday of Week (n+1).
  
      *Attempting the problem sheets each week is the single most important thing to do in this unit.  One can certainly excel without attending a single lecture, but not doing the problems will lead to certain disaster.*

<!-- Please submit your work by email with subject "[TLC] Week N", where N is the number of the week containing the deadline (usually this will be the current week).  So, the first sheet should be submitted with subject "[TLC] Week 2".  To see who you should submit it to, consult your timetable:

- If you are in Group 1 (Ada Lovelace SM4), please email (a scan/photo/image/pdf) to Amos Holland (amos.holland.2021).
- If you are in Group 2 (Ada Lovelace SM3), please email (a scan/photo/image/pdf) to Rose Hudson (cv21874).
- If you are in Group 3 (Ada Lovelace PC6), please email (a scan/photo/image/pdf) to Charlie Walpole (op18921). -->
    
      

  * __Problem Class (1 hr).__ You should attend a problem class each week to discuss the answers to the problems of the previous week and look ahead to problems of the next week.  There will be no class in Week 1, since you have not yet had time to complete a problem sheet.
     - Friday 2pm in Ada Lovelace SM3/SM4/PC6
   
  * __Office Hours (0-2 hr).__ Except for weeks 4, 9 and 12, Steven will be running office hours every Wednesday from 1pm-2pm in his office, MVB 2.46.  
  
<!-- The TAs will be running office hours every Friday from 4pm-5pm in their office, 81 Woodland Rd, room 1.05: opposite MVB, the staircase next to the bus stop, go up the stairs, all the way into the garden, then Sam will let you in the back door. -->



* * *

![report card](assets/icons8-report-card-100.png){: .icon } 
## Assessment

The unit is 100% assessed by one section in the written exam "Topics in Computer Science" in the December exam period.

<!-- For this year, you will be able to take one A4 page (= one side of a sheet of A4 paper) of your own notes into the exam and consult them freely.   -->

The exam is _closed book_, you may not bring any notes with you to the exam room.  However, at the back of the Types and Lambda Calculus section in the exam is an appendix containing most of the important definitions from the unit.  You can take a look at what was provided last year here: [appendix](papers/appendix.pdf).

The exam is a series of problems to solve in the same style as the weekly problem sheets. There will be one question, split into several parts that are worth a total of 50 marks.  The problems are of varying difficulty and  the difficulty is labelled on each question.  The difficulty of problems is related to your possible marks in *roughly* the following way:

* 1* problems only account for approximately 40% of available marks.
* 1* and 2* problems account for approximately 70% of available marks.
* 1\*, 2\* and 3* problems account for approximately 100% of available marks.

Typical examples of 1* questions (mostly mechanical derivations, using definitions carefully but with little insight):
* Identifying a correct use of a definition, e.g. that some reduction is correct.
* Identifying parts of terms/types/derivations, e.g. list all free variables/redexes in a given term.
* Giving simple examples of e.g. reductions, normal forms, types etc.
* Constructing type derivations to justify a type assignment.
* Constructing terms that inhabit a given type.

Typical examples of 2* questions (mostly proofs that are of a similar shape to those you have been doing routinely - do not require any tricks or difficult insights):
* Prove that a term satisfies a property, e.g that a term implements the square function on numerals.
* Prove a property of all terms, all reduction sequences, all types etc. typically using induction.
* Prove that no term exists that satisfies a given property/specification.
* Prove that a term is untypable.
* Give an example of a term satisfying a given complex specification.

*Before the day of the exam, ensure you are confident in how to answer typical 1\* and 2\* questions!*

<!-- _The last part of the first question (on untyped PCF) is a 4* question, do not attempt it until you have done all you can on all other question parts_.  In general, the difficulty of problems increases throughout each of the two questions - the last problem of Question 1 is very difficult, but the first problem of Question 2 should be easy. -->

<!-- Note that Chapter 9 of the notes, on decidability and undecidability is not examined (since I did not have time to cover it in lectures).  The last two sections of the last chapter, 13.3 and 13.4 are not examined either. -->

Below you will find a selection of past papers and their answers.  HOWEVER, before 2024 the exam was a different format: it was a 2 hour exam dedicated to Types and Lambda Calculus and questions were not labelled with their difficulty.  Now, Types and Lambda Calculus just forms one section in the 2 hour "Topics in Computer Science" exam.  Therefore, each of the past papers below contains roughly twice as many problems as you will need to solve in your exam.  Note, you will also typically find the older "past papers" more difficult than the real exam, because what you have been taught differs from what has been taught in previous iterations of the unit.  For example, in previous years, students had much more practice with pure terms (PCF without constants, as in Problem Sheet 5).  

<ul>
    <li><a href="papers/jan-2019.pdf" target="_blank">January 2019</a> (<a href="papers/jan-2019-answers.pdf"  target="_blank">answers</a>)</li>
    <li><a href="papers/2019-Summer.pdf" target="_blank">Summer 2019</a> (<a href="papers/2019-Summer-answers.pdf"  target="_blank">answers</a>)</li>
    <li><a href="papers/jan-2021.pdf" target="_blank">January 2021</a> (<a href="papers/jan-2021-answers.pdf"  target="_blank">answers</a>)</li>
    <li><a href="papers/jan-2023.pdf" target="_blank">January 2023</a> (<a href="papers/jan-2023-answers.pdf"  target="_blank">answers</a>)</li>
</ul>

* * *

{: style="text-align:center"}
Icons in this course are from the '[Hand Drawn](https://icons8.com/icons/carbon-copy)' icon collection by [Icons8](https://icons8.com/).