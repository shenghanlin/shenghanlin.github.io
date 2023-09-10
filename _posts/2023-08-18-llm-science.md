---
layout: post
title: LLM Science Exam
date: 2023-08-18 08:57:00-0400
description: How to Turn a NLP Classifer into a Multiple Choice Question Model
categories: kaggle notebook transformer nlp
giscus_comments: true
related_posts: false
featured: true
---
It may take a few moments for the Jupyter notebook to load. Thank you for your patience =)

{::nomarkdown}
{% assign jupyter_path = "assets/notebook/llm-science-exam.ipynb" | relative_url %}
{% capture notebook_exists %}{% file_exists assets/notebook/llm-science-exam.ipynb %}{% endcapture %}
{% if notebook_exists == "true" %}
    {% jupyter_notebook jupyter_path %}
{% else %}
    <p>Sorry, the notebook you are looking for does not exist.</p>
{% endif %}
{:/nomarkdown}
