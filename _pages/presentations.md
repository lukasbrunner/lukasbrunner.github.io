---
layout: archive
title: "Presentations"
permalink: /presentations/
author_profile: true
---

Slides and presentations — files are hosted in a [separate repository on GitHub](https://github.com/lukasbrunner/presentations).

<div id="pres-loading" style="font-style:italic;color:#666;">Loading…</div>
<ul id="pres-list"></ul>
<p id="pres-error" style="display:none;">
  Could not load the file list automatically.
  <a href="https://github.com/lukasbrunner/presentations">Browse files on GitHub →</a>
</p>

<script>
(function () {
  var API = 'https://api.github.com/repos/lukasbrunner/presentations/contents/';
  var loading = document.getElementById('pres-loading');
  var list    = document.getElementById('pres-list');
  var error   = document.getElementById('pres-error');

  function linkFor(file) {
    var ext = file.name.split('.').pop().toLowerCase();
    if (ext === 'html' || ext === 'htm') {
      // Render HTML presentations in the browser via htmlpreview.github.io
      return 'https://htmlpreview.github.io/?' + file.download_url;
    }
    if (ext === 'pdf') {
      // Direct download / inline PDF
      return file.download_url;
    }
    // Fallback: GitHub blob view
    return file.html_url;
  }

  fetch(API)
    .then(function (r) {
      if (!r.ok) throw new Error('HTTP ' + r.status);
      return r.json();
    })
    .then(function (items) {
      loading.style.display = 'none';
      var files = items
        .filter(function (i) { return i.type === 'file'; })
        .sort(function (a, b) { return b.name.localeCompare(a.name); }); // newest-first by name

      if (files.length === 0) {
        list.innerHTML = '<li>No files found.</li>';
        return;
      }

      files.forEach(function (file) {
        var li = document.createElement('li');
        var a  = document.createElement('a');
        a.href   = linkFor(file);
        a.target = '_blank';
        a.rel    = 'noopener noreferrer';

        // Strip extension for display, keep it readable
        var label = file.name.replace(/[-_]/g, ' ').replace(/\.[^.]+$/, '');
        a.textContent = label;

        var small = document.createElement('small');
        small.style.color = '#888';
        small.style.marginLeft = '0.4em';
        small.textContent = '(' + file.name.split('.').pop().toUpperCase() + ')';

        li.appendChild(a);
        li.appendChild(small);
        list.appendChild(li);
      });
    })
    .catch(function () {
      loading.style.display = 'none';
      error.style.display   = 'block';
    });
})();
</script>
