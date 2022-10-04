---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
draft: true # until false then posted to production
author: "david.moreno"
description: "some short form description here"
tags: [
  "tag1",
  "tag2",
  "tagn",
]
ShowToc: true
ShowBreadCrumbs: true

## including a cover image
# cover:
#   image: "<image path/url>"   # as static content
#   image: https://i.ibb.co/K0HVPBd/paper-mod-profilemode.png  # as a url
#   alt: "<alt text>"
#   caption: "<text>"
---

---
