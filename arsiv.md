---
layout: default
title: Kütüphane Arşivi
permalink: /arsiv/
---

<h1>📚 Kütüphane Arşivi</h1>
<p>Geçmişten günümüze yayınlanan tüm bölümler.</p>

<div class="search-container" style="margin-bottom: 20px;">
  <input type="text" id="chapterSearch" oninput="filterChapters()" placeholder="Bölüm ara (Örn: Kızıl, 12)..." 
  style="width: 100%; padding: 12px; font-size: 16px; background: #1a1a1a; border: 1px solid #444; color: #ddd; border-radius: 4px;">
</div>

<ul id="fullChapterList" class="chapter-list">
  {% assign all_chapters = site.chapters | sort: 'path' %}
  
  {% for chapter in all_chapters %}
    {% if chapter.date <= site.time %}
      <li>
        <a href="{{ chapter.url }}" class="chapter-link">
          <span class="chapter-title">{{ chapter.title }}</span>
        </a>
      </li>
    {% endif %}
  {% endfor %}
</ul>

<script>
function filterChapters() {
  var input = document.getElementById('chapterSearch');
  var filter = trNormalize(input.value);
  
  var ul = document.getElementById("fullChapterList");
  var li = ul.getElementsByTagName('li');

  for (var i = 0; i < li.length; i++) {
    var a = li[i].getElementsByTagName("a")[0];
    var txtValue = a.textContent || a.innerText;
    
    if (trNormalize(txtValue).indexOf(filter) > -1) {
      li[i].style.display = "";
    } else {
      li[i].style.display = "none";
    }
  }
}
function trNormalize(s) {
  return (s || "")
    .toLocaleLowerCase("tr-TR")
    .replace(/ı/g, "i")
    .normalize("NFD")
    .replace(/[\u0300-\u036f]/g, "");
}
</script>
