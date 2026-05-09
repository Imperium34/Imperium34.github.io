---
layout: page
title: Anasayfa
permalink: /
---

# Neden Yeni Bir Çeviri? "Esrarın Hükümdarı" Edisyonu

**Gizemlerin Efendisi** (_Lord of the Mysteries_), sadece bir web romanı değil; Viktorya dönemi endüstrisini, Lovecraftian kozmik dehşeti ve steampunk estetiğini harmanlayan modern bir klasiktir. Ancak bu eserin ruhu, standart çevirilerde sıkça kaybolmaktadır.

### Felsefemiz

Bir eseri çevirmek, kelimeleri bir dilden diğerine taşımak değil, o atmosferi yeniden inşa etmektir. Google Translate veya yüzeysel çevirilerde "Fool" kelimesi "Aptal" olarak çevrilip geçilir. Oysa Tarot kartlarındaki _The Fool_, bir başlangıcı, kuralların dışına çıkmayı ve sonsuz potansiyeli temsil eder. Bizim çevirimizde o, bir **Soytarı**'dır.

Bu çeviri projesi, **"Esrarın Hükümdarı"** edisyonu olarak adlandırılmıştır ve şu prensiplere dayanır:

1.  **Atmosferik Dil:** Karakterler modern sokak ağzıyla değil, yaşadıkları dönemin ağırlığına uygun konuşurlar.
2.  **Terim Derinliği:** _Seer_ sıradan bir Gözcü değil, yıldızlara bakan bir **Kâhin**'dir. _Scribe_ sadece Yazıcı değil, bir **Kâtip**'tir.
3.  **Miras:** İngilizce metnin aktaramadığı "Doğu/Xianxia" hiyerarşisi, Türkçenin zengin Osmanlıca kelime dağarcığı kullanılarak aslına sadık sunulmuştur.

**Örnek Karşılaştırma:**

- _Standart:_ "Bu çağa ait olmayan aptal."
- _Esrarın Hükümdarı:_ **"Bu asra mensup olmayan Soytarı."**

Amacımız, Klein Moretti'nin sislerin üzerindeki yalnızlığını iliklerinize kadar hissettirmektir.

---

## Hikaye Özeti

> Buhar gücü ve makinenin yükselen devrinde, kim bir **"Olağanüstü"** olmaya yaklaşabilir? Tarihin ve karanlığın sislerine bürünmüş, kulaklarımıza fısıldayan o pusudaki şer kimdir veya nedir?
>
> Zhou Mingrui, kendini bir dizi gizemle yüzleşerek uyanmış bulur. O artık Klein Moretti'dir ve bu alternatif Viktorya dönemi; topların, zırhlıların, zeplinlerin ve fark makinelerinin olduğu kadar; **İksirlerin, Kehanetlerin, Efsunların, Tarot Kartlarının** ve **Mühürlenmiş Eserlerin** de dünyasıdır.
>
> Işık parlamaya devam etse de, esrar asla peşimizi bırakmaz. Klein'ın, Olağanüstü iksirlerden kazandığı güçleri yavaşça keşfederken, dünyanın hem Ortodoks hem de Sapkın kiliseleriyle nasıl bir karmaşanın içine sürüklendiğine tanıklık edin.
>
> Tıpkı destedeki karşılığı olan ve sonsuz potansiyeli simgeleyen 0 numaralı kart gibi... **Bu, "Soytarı"nın efsanesidir.**

---

<div class="latest-updates">
  <h2>🆕 Son Eklenen Bölümler</h2>
  
  <ul class="chapter-list">
    {% assign recent_chapters = site.chapters | sort: 'path' | reverse %}
    {% for chapter in recent_chapters limit: 5 %}
      <li>
        <span style="color: #666; font-size: 0.9em;">[{{ chapter.date | date: "%d.%m" }}]</span>
        <a href="{{ chapter.url }}">{{ chapter.title }}</a>
      </li>
    {% endfor %}
  </ul>

  <div style="margin-top: 15px;">
    <a href="/arsiv" style="font-weight: bold; color: #a41818; text-decoration: none;">
      📚 Tüm Bölüm Listesi (Arşiv) &rarr;
    </a>
  </div>
  <div style="margin-top: 15px;">
    <a href="/sozluk" style="font-weight: bold; color: #d4af37; text-decoration: none;">
      📖 İkincil Sözlük ve Terimler &rarr;
    </a>
  </div>
</div>
