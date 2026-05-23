---
layout: page
title: Anasayfa
permalink: /
---

<div style="text-align: center; margin: 3rem 0;">
  <h1 style="font-size: 2.5rem; margin-bottom: 10px; color: #e0e0e0;">Esrarın Hükümdarı</h1>
  <p style="font-size: 1.2rem; color: #888; font-style: italic;">"Işık parlamaya devam etse de, esrar asla peşimizi bırakmaz."</p>
</div>

<div style="display: flex; flex-wrap: wrap; justify-content: center; gap: 15px; margin-bottom: 3rem;">
  
  <a href="#" id="resumeReadingBtn" style="display: none; background: #a41818; color: white; padding: 12px 24px; text-decoration: none; border-radius: 6px; font-weight: bold; font-size: 1.1rem; border: 1px solid #c21c1c;">
    🔖 Kaldığın Yerden Devam Et: <span id="resumeChapterName"></span>
  </a>

  <a href="/bolum-1" id="startReadingBtn" style="background: #1c1c1c; color: #e0e0e0; padding: 12px 24px; text-decoration: none; border-radius: 6px; font-weight: bold; font-size: 1.1rem; border: 1px solid #333;">
    👁️ İlk Bölümden Başla
  </a>

</div>

<div style="display: flex; flex-wrap: wrap; justify-content: space-between; gap: 15px; margin-bottom: 3rem; border-top: 1px solid #252525; border-bottom: 1px solid #252525; padding: 1.5rem 0;">
  
  <a href="/hakkinda/" style="flex: 1; text-align: center; background: #151515; padding: 15px; border-radius: 4px; color: #ccc; text-decoration: none; border: 1px solid #222;">
    <h3 style="margin: 0 0 5px 0; color: #e0e0e0;">🖋️ Proje Hakkında</h3>
    <span style="font-size: 0.85em;">Bu çevirinin amacı nedir?</span>
  </a>

  <a href="/sozluk/" style="flex: 1; text-align: center; background: #151515; padding: 15px; border-radius: 4px; color: #ccc; text-decoration: none; border: 1px solid #222;">
    <h3 style="margin: 0 0 5px 0; color: #d4af37;">📖 İkincil Sözlük</h3>
    <span style="font-size: 0.85em;">Terimler ve spoiler korumalı veri tabanı.</span>
  </a>

  <a href="/arsiv/" style="flex: 1; text-align: center; background: #151515; padding: 15px; border-radius: 4px; color: #ccc; text-decoration: none; border: 1px solid #222;">
    <h3 style="margin: 0 0 5px 0; color: #e0e0e0;">📚 Arşiv</h3>
    <span style="font-size: 0.85em;">Yayınlanmış tüm bölümler.</span>
  </a>

</div>

<div class="latest-updates">
  <h2 style="border-bottom: 2px solid #a41818; padding-bottom: 10px; margin-bottom: 20px;">🆕 Son Eklenen Bölümler</h2>
  
  <ul class="chapter-list">
    {% assign recent_chapters = site.chapters | sort: 'path' | reverse %}
    {% for chapter in recent_chapters limit: 5 %}
      <li>
        <span style="color: #666; font-size: 0.9em; min-width: 60px; display: inline-block;">[{{ chapter.date | date: "%d.%m" }}]</span>
        <a href="{{ chapter.url }}">{{ chapter.title }}</a>
      </li>
    {% endfor %}
  </ul>
</div>

<script>
  document.addEventListener('DOMContentLoaded', function() {
    var lastUrl = localStorage.getItem('imperiumLastChapterUrl');
    var lastTitle = localStorage.getItem('imperiumLastChapterTitle');
    
    if (lastUrl && lastTitle) {
      var resumeBtn = document.getElementById('resumeReadingBtn');
      var resumeSpan = document.getElementById('resumeChapterName');
      
      // Butonu görünür yap ve linki/ismi ata
      resumeBtn.style.display = 'inline-block';
      resumeBtn.href = lastUrl;
      
      // Uzun başlıkları kırpmak için ("Bölüm 5: Ritüel" -> "Bölüm 5" gibi)
      var shortTitle = lastTitle.split(':')[0]; 
      resumeSpan.textContent = shortTitle;
    }
  });
</script>
