---
layout: archive
title: "Presentations"
permalink: /presentations/
author_profile: true
---

<ul id="list"><li>Loading…</li></ul>

<script>
fetch('https://api.github.com/repos/lukasbrunner/presentations/contents/')
  .then(r => r.json())
  .then(files => {
    document.getElementById('list').innerHTML = files
      .filter(f => f.type === 'file')
      .map(f => `<li><a href="${f.html_url}">${f.name}</a></li>`)
      .join('');
  });
</script>
