---
layout: page
title: Anasayfa
permalink: /
---

# Neden Yeni Bir Çeviri? "Esrarın Hükümdarı" Edisyonu

**Gizemlerin Efendisi** (*Lord of the Mysteries*), sadece bir web romanı değil; Viktorya dönemi endüstrisini, Lovecraftian kozmik dehşeti ve steampunk estetiğini harmanlayan modern bir klasiktir. Ancak bu eserin ruhu, standart çevirilerde sıkça kaybolmaktadır.

### Felsefemiz
Bir eseri çevirmek, kelimeleri bir dilden diğerine taşımak değil, o atmosferi yeniden inşa etmektir. Google Translate veya yüzeysel çevirilerde "Fool" kelimesi "Aptal" olarak çevrilip geçilir. Oysa Tarot kartlarındaki *The Fool*, bir başlangıcı, kuralların dışına çıkmayı ve sonsuz potansiyeli temsil eder. Bizim çevirimizde o, bir **Soytarı**'dır.

Bu çeviri projesi, **"Esrarın Hükümdarı"** edisyonu olarak adlandırılmıştır ve şu prensiplere dayanır:

1.  **Atmosferik Dil:** Karakterler modern sokak ağzıyla değil, yaşadıkları dönemin ağırlığına uygun konuşurlar.
2.  **Terim Derinliği:** *Seer* sıradan bir Gözcü değil, yıldızlara bakan bir **Kâhin**'dir. *Scribe* sadece Yazıcı değil, bir **Kâtip**'tir.
3.  **Miras:** İngilizce metnin aktaramadığı "Doğu/Xianxia" hiyerarşisi, Türkçenin zengin Osmanlıca kelime dağarcığı kullanılarak aslına sadık sunulmuştur.

**Örnek Karşılaştırma:**
* *Standart:* "Bu çağa ait olmayan aptal."
* *Esrarın Hükümdarı:* **"Bu asra mensup olmayan Soytarı."**

Amacımız, Klein Moretti'nin sislerin üzerindeki yalnızlığını iliklerinize kadar hissettirmektir.

---

## Son Eklenen Bölümler

<ul>
  {% for post in site.posts limit:10 %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      <span style="color: #666; font-size: 0.8em;"> - {{ post.date | date: "%d/%m/%Y" }}</span>
    </li>
  {% endfor %}
</ul>

[Tüm Bölüm Listesi](/arsiv/)
