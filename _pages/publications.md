---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

{% if site.author.googlescholar %}
  <div class="wordwrap">You can also find my articles on <a href="{{site.author.googlescholar}}">my Google Scholar profile</a>.</div>
{% endif %}

<!-- ### paper title
author list
[code](repo link), [PDF](paper link)
<div style="display: flex; align-items: center;">
    <div style="flex: 1;">
        ![main pic](paper-image.jpg)
    </div>
    <div style="flex: 2;">
        ABS.
    </div>
</div> -->

## 2023

***

### Are Intermediate Layers and Labels Really Necessary? A General Language Model Distillation Method
Shicheng Tan, Weng Lam Tam, **Yuanchun Wang**, Wenwen Gong, Shu Zhao, Peng Zhang, Jie Tang
[code](https://github.com/aitsc/GLMKD), [PDF](https://aclanthology.org/2023.findings-acl.614.pdf)
<div style="display: flex; align-items: center;">
    <div style="flex: 1;">
        ![main pic](../images/glmd.jpg)
    </div>
    <div style="flex: 2;">
        A general language model distillation (GLMD) method that performs two-stage word prediction distillation and vocabulary compression, which is simple and surprisingly shows extremely strong performance.
    </div>
</div>

<!-- {% include base_path %}

{% for post in site.publications reversed %}
  {% include archive-single.html %}
{% endfor %} -->
