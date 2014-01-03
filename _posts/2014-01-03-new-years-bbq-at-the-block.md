---
layout: post
title: New Years BBQ at the Block
date: 2014-01-03 14:17:00
image-urls:
  1:  {url: 0nX7PwABdc, desc: The Block }
  2:  {url: 7fk_mOwVTv, desc: Barbeque and Relax }
  3:  {url: G6c8B9MT9W, desc: The Block }
  4:  {url: TcnVI3p7hX, desc: Shy }
  5:  {url: af0t26Zc7i, desc: Sexy Chef }
  6:  {url: UwdlLKG5Xn, desc: Play }
  7:  {url: iSvBr4MP-q, desc: Play }
  8:  {url: PdV5izbIzd, desc: Not All Fun and Games }
  9:  {url: xiC5TqDF5x, desc: Dog }
  10: {url: 4wlUU4el62, desc: Chill and Watch }
  11: {url: cPFsHsTD58, desc: Watchful }
  12: {url: FVWdAAucKv, desc: Dogs }
  13: {url: B_aUwVcQH1, desc: Jumper }
  14: {url: e3HT3HQxR0, desc: Look }
  15: {url: REYnEpIGbg, desc: There }
  16: {url: KLJD-T5oV8, desc: Poser }
  17: {url: p03mUwvlbB, desc: Grace }
  18: {url: qQ1stL4nbI, desc: What a Beast }
  19: {url: MpCsgliXIw, desc: BBQ }
  20: {url: OuEY5hEpqq, desc: BBQ }
  21: {url: zBMYKymHw9, desc: Boys and Girls }
  22: {url: Pn9-wWJoJo, desc: Climber }
  23: {url: FAeU-dsZ6Q, desc: Horseplay }
  24: {url: _fZL0CKzCJ, desc: The Result }
  25: {url: YyzIgxw_GL, desc: Jumper }
  26: {url: 5ncGTolw_3, desc: Jumper }
  27: {url: eR4d5SEDG7, desc: Pour }
  28: {url: BpMJMMyu8u, desc: Say What }
  29: {url: Do8b4fsqPo, desc: The Drive Home }
  30: {url: AWY4qbCDqy, desc: Bokeh }
  31: {url: 0D3iECjoAt, desc: Bokeh }
  32: {url: 5pGCSFwp1c, desc: Bokeh }
  33: {url: NMSp0WZKCZ, desc: Bokeh }
---

For New Years a group of us had a BBQ and hangout at a mates property out of town. Here are some of the photos from the afternoon & evening. Click the thumbnails to view in a lightbox gallery (needs javascript), or follow the [link to the Dropbox gallery](https://www.dropbox.com/sh/da2ouzvsgr84ayg/D4hPAHynxb).

{% for img in page.image-urls %}
<div class="gallery-thumbnail-container">
  <a href="https://dl.dropboxusercontent.com/sh/da2ouzvsgr84ayg/{{ img[1].url }}/BBQ_{{ img[0] }}.jpg" data-lightbox="bbq" title="{{ img[1].desc }}">
    <img src="/images/new-years-block-bbq/BBQ_thumb_{{ img[0] }}.jpg" class="gallery-thumbnail" alt="BBQ_{{ img[0] }}" />
  </a>
</div>
{% endfor %}

