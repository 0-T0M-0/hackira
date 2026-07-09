+++
title = "{{ replace .File.ContentBaseName `-` ` ` | title }}"
description = ""
date = {{ .Date }}
draft = false
weight = 10
tags = []
toc = true
+++

Courte intro sur le sujet.

## Ressources

{{ `{{< resource title="Nom" url="https://exemple.com" type="repo" tags="tag1, tag2" >}}` }}
Une phrase de description.
{{ `{{< /resource >}}` }}
