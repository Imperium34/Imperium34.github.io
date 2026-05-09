---
layout: default
title: İkincil Sözlük
permalink: /sozluk/
---

<h1>📖 İkincil Sözlük ve Çeviri Notları</h1>
<p>Bu sözlük, çeviride kullanılan özel terimlerin İngilizce karşılıklarını ve arkalarındaki anlamları içerir.</p>

<div style="background: #a41818; color: white; padding: 15px; border-radius: 4px; margin-bottom: 20px; font-weight: bold;">
  ⚠️ DİKKAT: Üzeri kapalı ("Spoiler İçerir") terimler, serinin ilerleyen bölümlerine dair kritik gizemler barındırır. Kendi sorumluluğunuzda açınız.
</div>

<div class="search-container" style="margin-bottom: 30px;">
  <input type="text" id="termSearch" onkeyup="filterTerms()" placeholder="Terim veya İngilizce karşılığını ara..." 
  style="width: 100%; padding: 12px; font-size: 16px; background: #1a1a1a; border: 1px solid #444; color: #ddd; border-radius: 4px;">
</div>

<ul id="glossaryList" style="list-style-type: none; padding: 0;">
  {% for item in site.data.sozluk %}
    <li class="glossary-item" style="background: #151515; border: 1px solid #333; margin-bottom: 15px; padding: 15px; border-radius: 8px;">
      <h3 class="term-title" style="margin-top: 0; color: #d4af37;">
        {{ item.terim }} 
        <span style="font-size: 0.7em; color: #666;">({{ item.ingilizce }})</span>
      </h3>
      <span style="display: inline-block; background: #222; color: #888; padding: 3px 8px; border-radius: 3px; font-size: 0.8em; margin-bottom: 10px;">
        {{ item.kategori }}
      </span>
      {% if item.yol_grubu %}
        <span style="display: inline-block; background: #2b1b3d; color: #a882d4; padding: 3px 8px; border-radius: 3px; font-size: 0.8em; margin-bottom: 10px; margin-left: 5px; border: 1px solid #4a3463;">
          {{ item.yol_grubu }}
        </span>
      {% endif %}
      {% if item.spoiler %}
        <details style="cursor: pointer;">
          <summary style="color: #a41818; font-weight: bold; outline: none;">Spoiler İçerir (Görmek için tıklayın)</summary>
          <p class="term-desc" style="margin-top: 10px; color: #ccc;">{{ item.aciklama }}</p>
        </details>
      {% else %}
        <p class="term-desc" style="color: #ccc; margin-bottom: 0;">{{ item.aciklama }}</p>
      {% endif %}
    </li>

{% endfor %}

</ul>

<script>
function filterTerms() {
  var input = document.getElementById('termSearch');
  var filter = input.value.toUpperCase();
  var ul = document.getElementById("glossaryList");
  var li = ul.getElementsByTagName('li');

  for (var i = 0; i < li.length; i++) {
    var title = li[i].getElementsByClassName("term-title")[0];
    var desc = li[i].getElementsByClassName("term-desc")[0];
    var txtValue = (title.textContent || title.innerText) + " " + (desc.textContent || desc.innerText);
    
    if (txtValue.toUpperCase().indexOf(filter) > -1) {
      li[i].style.display = "";
    } else {
      li[i].style.display = "none";
    }
  }
}
</script>
