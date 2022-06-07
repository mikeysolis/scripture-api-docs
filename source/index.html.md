---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - javascript
  - php
  - python

toc_footers:
  - <a href='#'>Check out our demos</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - authentication
  - headers
  - volumes
  - books
  - chapters
  - verses
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the Scripture API
---

# Introduction

Welcome to the Scripture API. A fun little project I built to power the backend for a suite of mobile apps I'm creating. The API consists of the 'Standard' scripture library found in the Church of Jesus Christ of Latter-Day Saints. This includes the Old and New Testament from the King James version of the Bible, the Book of Mormon, Doctrine & Covenants and Pearl of Great Price.

These records are all part of the [public domain](https://en.wikipedia.org/wiki/Public_domain) and as such do not include the Topical Guide, Bible Dictionary, chapter headers, indexes, references and other content created later.

The API conforms to the JsonApi standard. Some feel the JsonApi standard is overly verbose and difficult to understand but I feel the predictability and flexibility it provides is well worth it here. This is an API that I may open up to others in the future and predictability and flexibility will be a great benefit to developers.

The data for this API comes from the [LDS Documentation Project](https://scriptures.nephi.org/).
