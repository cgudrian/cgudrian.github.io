---
date: {{ now.Format "2006-01-02" }}
lastmod: {{ now.Format "2006-01-02" }}
showTableOfContents: false
title: "{{ replace .File.ContentBaseName `-` ` ` | title }}"
type: "post"
---
