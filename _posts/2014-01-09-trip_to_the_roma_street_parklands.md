---
layout: post
title: Trip to the Roma Street Parklands
date: 2014-01-09 20:45:00
gallery-word: Garden
dropbox-folder-url: https://dl.dropboxusercontent.com/sh/4rvhm5ibn32tv26
thumbnail-folder-url: /images/garden_gallery_thumbs
image-urls:
  "01": {url: buEsnzqEgN, desc: "" }
  "02": {url: 41bJcuPdZd, desc: "(Taken by my wife)" }
  "03": {url: Dx48KmgdLF, desc: "" }
  "04": {url: niDkHCL__L, desc: "" }
  "05": {url: g3b2Fa6H8O, desc: "Basking in the mist from the fountain" }
  "06": {url: BkPOqbETJi, desc: "" }
  "07": {url: WKizHgLfC4, desc: "" }
  "08": {url: wIKC2k-rCU, desc: "" }
  "09": {url: xte9MwuFig, desc: "" }
  "10": {url: JGB_3ru1Sl, desc: "" }
  "11": {url: qp-S5wi89W, desc: "" }
  "12": {url: ZsDEp7I7vS, desc: "They were everywhere, and not at all shy!" }
  "13": {url: 3xFieY_V4O, desc: "Cutie" }
  "14": {url: zaySx7hDtN, desc: "" }
---

We spent a long weekend mini-holiday in Brisbane recently. Here are some photos from the Roma Street Parklands where we spent the morning with an old friend and her kids. If I get permission I'll post some photos of them too... gorgeous kids.

Most of the trip we spent indoors due to a poorly timed heat wave... which was fine, but it meant for fewer photos than I had expected. I did however find [this](http://www.amazon.com/Canon-EOS-Digital-Field-Guide/dp/1118169123) which is obviously perfect! I've just started and it already has given some good practical shooting advice... not, alas, in time for this shoot.

{% for img in page.image-urls %}
<div class="gallery-thumbnail-container">
  <a href="{{ page.dropbox-folder-url }}/{{ img[1].url }}/{{ page.gallery-word }}_{{ img[0] }}.JPG" data-lightbox="{{ page.gallery-word }}" title="{{ img[1].desc }}">
    <img src="{{ page.thumbnail-folder-url }}/{{ page.gallery-word }}_thumb_{{ img[0] }}.JPG" class="gallery-thumbnail" alt="{{ page.gallery-word }}_{{ img[0] }}" />
  </a>
</div>
{% endfor %}

