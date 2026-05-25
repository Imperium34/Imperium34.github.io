---
layout: default
title: İkincil Sözlük
permalink: /sozluk/
---

<style>
.dynamic-spoiler {
  filter: blur(5px);
  opacity: 0.6;
  user-select: none;
  pointer-events: none;
  background-color: rgba(21, 21, 21, 0.8);
  padding: 2px 6px;
  border-radius: 4px;
  transition: filter 0.8s ease, opacity 0.8s ease, background-color 0.8s ease;
}

.dynamic-spoiler.unlocked {
  filter: blur(0);
  opacity: 1;
  user-select: auto;
  pointer-events: auto;
  background-color: transparent;
}
</style>

<h1>📖 Sözlük ve Çeviri Notları</h1>
<p>Bu sözlük, çeviride kullanılan özel terimlerin İngilizce karşılıklarını ve arkalarındaki anlamları içerir.</p>

<div style="background: #a41818; color: white; padding: 15px; border-radius: 4px; margin-bottom: 20px; font-weight: bold;">
  ⚠️ DİKKAT: Üzeri kapalı ("Spoiler İçerir") terimler, serinin ilerleyen bölümlerine dair kritik gizemler barındırır. Kendi sorumluluğunuzda açınız.
</div>

<div class="filter-container" style="margin-bottom: 30px; display: flex; flex-direction: column; gap: 10px;">
  <input type="text" id="termSearch" oninput="filterTerms()" placeholder="Terim veya İngilizce karşılığını ara..." style="width: 100%; padding: 12px; font-size: 16px; background: #1a1a1a; border: 1px solid #444; color: #ddd; border-radius: 4px; box-sizing: border-box;">
  
  <div style="display: flex; gap: 10px; flex-wrap: wrap;">
    <select id="categoryFilter" onchange="filterTerms()" style="flex: 1; min-width: 180px; padding: 10px 12px; font-size: 14px; background: #1a1a1a; border: 1px solid #444; color: #ddd; border-radius: 4px;">
      <option value="">Tüm Kategoriler</option>
      <option value="Temel Kavramlar">Temel Terimler</option>
      <option value="Organizasyonlar">Organizasyonlar</option>
      <option value="İlahlar ve Yüce Kadimler">İlahlar ve Yüce Kadimler</option>
      <option value="Tarot Kulübü">Tarot Kulübü</option>
      <option value="Aşkın Yolları">Aşkın Yolları</option>
    </select>

    <select id="spoilerFilter" onchange="filterTerms()" style="flex: 1; min-width: 180px; padding: 10px 12px; font-size: 14px; background: #1a1a1a; border: 1px solid #444; color: #ddd; border-radius: 4px;">
      <option value="">Spoiler Durumu: Tümü</option>
      <option value="false">Yalnızca Spoilersız</option>
      <option value="true">Yalnızca Spoilerlı</option>
    </select>

    <button onclick="resetFilters()" style="padding: 10px 18px; font-size: 14px; background: #222; border: 1px solid #444; color: #aaa; border-radius: 4px; cursor: pointer;">
      Filtreleri Sıfırla
    </button>

  </div>
  <p id="resultCount" style="margin: 0; font-size: 0.85em; color: #666;"></p>
</div>

<ul id="glossaryList" style="list-style-type: none; padding: 0;">
  {% for item in site.data.sozluk %}
    <li class="glossary-item" data-terim="{{ item.terim | downcase }}" data-ingilizce="{{ item.ingilizce | downcase }}" data-kategori="{{ item.kategori }}" data-spoiler="{{ item.spoiler }}" style="background: #151515; border: 1px solid #333; margin-bottom: 15px; padding: 15px; border-radius: 8px;">
      
      <h3 class="term-title" style="margin-top: 0; color: #d4af37;">
        {{ item.terim }} <span style="font-size: 0.7em; color: #666;">({{ item.ingilizce }})</span>
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
          <p style="margin-top: 10px; color: #ccc;">{{ item.aciklama }}</p>
        </details>
      {% else %}
        {% if item.aciklama %}
          <p style="color: #ccc; margin-bottom: 0;">{{ item.aciklama }}</p>
        {% endif %}
      {% endif %}

      {% if item.mertebeler %}
        <ul style="list-style: none; padding: 0; margin-top: 15px; border-top: 1px dashed #333; padding-top: 10px;">
          {% for mertebe in item.mertebeler %}
            <li style="margin-bottom: 8px; font-size: 0.95em;">
              <strong style="color: #888;">Mertebe {{ mertebe.seviye }}:</strong>
              <span class="dynamic-spoiler" data-unlock="{{ mertebe.bolum_siniri }}">
                {{ mertebe.isim }}
              </span>
            </li>
          {% endfor %}
        </ul>
      {% endif %}

    </li>

{% endfor %}

</ul>

<p id="noResults" style="display: none; color: #666; text-align: center; padding: 40px 0;">
  Arama kriterlerinize uygun terim bulunamadı.
</p>

<script>
function filterTerms() {
  var searchVal = document.getElementById('termSearch').value.toLowerCase().trim();
  var categoryVal = document.getElementById('categoryFilter').value;
  var spoilerVal = document.getElementById('spoilerFilter').value;
  var items = document.querySelectorAll('.glossary-item');
  var visibleCount = 0;

  items.forEach(function(item) {
    var terim = item.dataset.terim || '';
    var ingilizce = item.dataset.ingilizce || '';
    var kategori = item.dataset.kategori || '';
    var spoiler = item.dataset.spoiler || '';

    var matchesSearch = !searchVal || terim.indexOf(searchVal) > -1 || ingilizce.indexOf(searchVal) > -1;
    var matchesCategory = !categoryVal || kategori === categoryVal;
    var matchesSpoiler = !spoilerVal || spoiler === spoilerVal;

    if (matchesSearch && matchesCategory && matchesSpoiler) {
      item.style.display = '';
      visibleCount++;
    } else {
      item.style.display = 'none';
    }
  });

  var countEl = document.getElementById('resultCount');
  var noResultsEl = document.getElementById('noResults');
  var total = items.length;

  if (visibleCount === total && !searchVal && !categoryVal && !spoilerVal) {
    countEl.textContent = '';
  } else {
    countEl.textContent = visibleCount + ' / ' + total + ' terim gösteriliyor.';
  }
  noResultsEl.style.display = visibleCount === 0 ? 'block' : 'none';
}

function resetFilters() {
  document.getElementById('termSearch').value = '';
  document.getElementById('categoryFilter').value = '';
  document.getElementById('spoilerFilter').value = '';
  filterTerms();
}

document.addEventListener("DOMContentLoaded", function() {
  const lastChapterTitle = localStorage.getItem("imperiumLastChapterTitle");
  if (!lastChapterTitle) return;
  
  const match = lastChapterTitle.match(/Bölüm\s+(\d+)/i);
  if (match) {
    const currentChapter = parseInt(match[1]);
    const spoilers = document.querySelectorAll(".dynamic-spoiler");
    
    spoilers.forEach(spoiler => {
      const unlockAt = parseInt(spoiler.getAttribute("data-unlock"));
      if (currentChapter >= unlockAt) {
        spoiler.classList.add("unlocked");
      }
    });
  }
});
</script>
