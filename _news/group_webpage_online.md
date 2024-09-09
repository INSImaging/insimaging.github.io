---
layout: post
title: Group webpage online.
date: 2024-09-09
inline: false # true, for only showing in front page, no separate page
related_posts: false
---

<!-- A simple inline announcement with Markdown emoji! :sparkles: :smile: -->

Our group webpage is now online! There are several steps more to complete the webpage, and the first step is to update the **people** page. To this end, we need you to complete the two files which can be downloaded from [here](/assets/file/information.zip "download").

Complete the downloaded files, and send them to me (Jingwei) together with a **证件照**. Below are some guidelines on how to complete the two downloaded files. 



---
### The markdown file (firstname_lastname.md)
The markdown file is rather easy to complete, as you only need to fill the following information

    ---
    layout: page
    title: Firstname Lastname
    description: 
    img: assets/img/people/profile.jpg
    importance: 1
    category: undergraduate
    ---

You need to
 - Change the "Firstname Lastname" to your name.
 - Change the "profile.jpg" to your picture's name, also the file format if it is not JPG picture.
 - Change the category to yours, choices of category include "faculty, postdoc, phd student, master student, undergraduate, alumni".

You can also write some introduction about yourself in the file.

---
### The YAML file (firstname_lastname.yml)
The YAML file consists of several different blocks to fill, just follow the file is fine. Here is an example of [Qiaoqiao's page](/people/qiaoqiao_ding/). You can also add other customized block as you want. 

**Warning** do not use **tap** key for space, use **space** key. 

General information block, you can add extra item in the contents, such as your office. Just use the template would do the work, see below

    ---
    - title: General Information
      type: map
      contents:
        - name: Email Address
          value: your_email_name at sjtu dot edu dot cn
        - name: Research Interests
          value: xx, xx
        - name: Office
          value: xx xx xx
    ---

Working experience block (most of you don't need this). For the itemization in the *description*, simply delete them if you do not need them, this also applies to the following blcks. 

    ---
    - title: Experience
      type: time_table
      contents:
          - title: name of the position
          institution: name of the institute
          year: start year - end year
          description:
              - Description 1.
              - Description 2.
              - title: Description 3.
              contents:
                  - Sub-description 1.
                  - Sub-description 2.
          - title: name of the position
          institution: name of the institute
          year: start year - end year
          description:
              - Description 1.
              - Description 2.
    ---

Education block

    ---    
    - title: Education
      type: time_table
      contents:
          - title: PhD in Mathematics
          institution: name of the institute
          year: start year - end year
          description:
              - Description 1.
              - Description 2.
              - title: Description 3.
              contents:
                  - Sub-description 1.
                  - Sub-description 2.
          - title: Master in Mathematics
          institution: name of the institute
          year: start year - end year
          description:
              - Description 1.
              - Description 2.
          - title: Bachelor in Mathematics
          institution: name of the institute
          year: start year - end year
          description:
              - Description 1.
              - Description 2.
    ---

Research experience, such as internships, visitings.

    ---
    - title: Research Experience & Internships
      type: time_table
      contents:
          - title: name of the experience
          year: 2014 - 2015
          description: extra information
    ---

Publication block.

    ---
    - title: Selected Publications
      type: publications
      contents:
          - year: 2024.01
          name: title of the paper 1
          publisher: Journal of the publisher 1
          authors: Author 1, Author 2, etc.
          url: link to the paper
          - year: 2024.01
          name: title of the paper 2
          publisher: Journal of the publisher 2
          authors: Author 1, Author 2, etc.
          url: link to the paper
    ---

Honors and award received.

    ---
    - title: Honors and Awards
      type: time_table
      contents:
          - year: 2024
          items:
              - name of the honor or awards
          - year: 2023
          items:
              - name of the honor or awards
    ---

Other things you want to mention.

    ---
    - title: Other Interests
      type: list
      contents:
          - <u>Hobbies:</u> Hobby 1, Hobby 2, etc.
    ---