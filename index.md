<div style="display: flex; flex-wrap: wrap; justify-content: center; gap: 15px; margin-bottom: 3rem;">
  <a href="#" id="resumeReadingBtn" style="display: none; background: #a41818; color: white; padding: 12px 24px; text-decoration: none; border-radius: 6px; font-weight: bold; font-size: 1.1rem; border: 1px solid #c21c1c;">
    🔖 Kaldığın Yerden Devam Et: <span id="resumeChapterName"></span>
  </a>
  <a href="/bolum-1" id="startReadingBtn" style="background: #1c1c1c; color: #e0e0e0; padding: 12px 24px; text-decoration: none; border-radius: 6px; font-weight: bold; font-size: 1.1rem; border: 1px solid #333;">
    👁️ İlk Bölümden Başla
  </a>
</div>

<div class="quick-access-hub">
  <a href="/hakkinda/" class="hub-card">
    <h3 style="color: #e0e0e0;">🖋️ Proje Hakkında</h3>
    <span>Bu çevirinin amacı nedir?</span>
  </a>

  <a href="/sozluk/" class="hub-card">
    <h3 style="color: #d4af37;">📖 İkincil Sözlük</h3>
    <span>Terimler ve spoiler korumalı veri tabanı.</span>
  </a>

  <a href="/arsiv/" class="hub-card">
    <h3 style="color: #e0e0e0;">📚 Arşiv</h3>
    <span>Yayınlanmış tüm bölümler.</span>
  </a>
</div>

<div class="latest-updates">
  <h2 style="border-bottom: 2px solid #a41818; padding-bottom: 10px; margin-bottom: 20px;">🆕 Son Eklenen Bölümler</h2>
  
  <ul class="chapter-list">
    {% assign recent_chapters = site.chapters | sort: 'path' | reverse %}
    {% for chapter in recent_chapters limit: 5 %}
      <li>
        <span class="chapter-date">[{{ chapter.date | date: "%d/%m/%Y" }}]</span>
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
      
      resumeBtn.style.display = 'inline-block';
      resumeBtn.href = lastUrl;
      
      var shortTitle = lastTitle.split(':')[0]; 
      resumeSpan.textContent = shortTitle;
    }
  });
</script>
