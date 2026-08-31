---
title: Presentation
permalink: /presentation/
---
### Upcoming lab meetings
Every Thursday, we get together (mix of virtual and in person) for lab presentations (with food! sometimes).
On a rotating basis, each member of the lab speaks and teaches about something they know or shares their work. 
Anything, really. Relevant and interesting topics, good skills to know, nice Python packages, CSS trends, new findings and literature reviews... anything!

## Spring 2026

<details markdown="1" open>
  <br>
<summary>📅 Spring 2026 Schedule (click)</summary>

| Date  | Name  | Location  | Time    |
|-------|-------|-----------|---------|
| 03/05 | Maida | N4 1412-2 | 13:00 ~ |
| 03/19 | MK    | N4 1412-2 | 13:00 ~ |
| 04/02 | ER    | N4 1412-2 | 13:00 ~ |
| 04/16 | HJ    | N4 1412-2 | 12:00 ~ |
| 04/30 | JH    | N4 1412-2 | 13:00 ~ |
| 05/14 | Party |           | 11:30 ~ |
| 05/28 | Maida | N4 1412-2 | 13:00 ~ |
| 06/11 | KJ    | N4 1412-2 | 13:00 ~ |

</details>

---

## Fall 2025

<details markdown="1">
  <br>
<summary>📅 Fall 2025 Schedule (click)</summary>

| Date  | Name                       | Location | Time    |
|-------|----------------------------|----------|---------|
| 9/08  | YoungTeak                  | N4 1334  | 14:00 ~ |
| 9/18  | Maida                      | N4 1334  | 13:00 ~ |
| 10/01 | Canceled                   |          |         |
| 10/16 | KyungJong Kim              | N4 1334  | 13:00 ~ |
| 10/30 | HyeongJae Lee              | N4 1334  | 13:00 ~ |
| 11/06 | Jiyoon Beak                | N4 1334  | 13:00 ~ |
| 11/20 | Maida                      | N4 1334  | 14:00 ~ |
| 12/04 | JiHyang Chun, EunRang Kwon | N4 1334  | 13:00 ~ |

</details>

---

### **Materials**
<div class="content list">
  {% for post in site.posts %}
    <div class="list-item">
      <p class="list-post-title">
        <a href="{{ site.baseurl }}{{ post.url }}">- {{ post.title }}</a> (<small>{{post.date | date: "%m/%d/%y" }}</small>)
      </p>
    </div>
  {% endfor %}
</div>
