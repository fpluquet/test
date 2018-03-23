---
# You don't need to edit this file, it's empty on purpose.
# Edit theme's home layout instead if you wanna make some changes
# See: https://jekyllrb.com/docs/themes/#overriding-theme-defaults
layout: default
---
{% for UE in site.data.UEs %}
# {{ UE.accronyme }} : {{UE.libelle}} ({{UE.quadrimestre}})

{% assign AAs = site.data.AAs | where:"UE", UE.accronyme %}
{% for AA in  AAs %}
{% assign: label = AA.accronyme | append: " : " | append: AA.libelle %}
- {% include aaLink.html label=label aa=AA %} (Profs :  {% for prof in AA.enseignants %} [{{prof}}]({{site.baseurl}}/personnels/{{prof | downcase}}.html){% if forloop.last == false %}, {% endif %}{% endfor %})
{% endfor %}

{% endfor %}