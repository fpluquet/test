---
layout: innerPage
---
{% for UE in site.data.UEs %}
# {{ UE.accronyme }} : {{UE.libelle}} ({{UE.quadrimestre}})

{% assign AAs = site.data.AAs | where:"UE", UE.accronyme %}
{% for AA in  AAs %}
{% assign: label = AA.accronyme | append: " : " | append: AA.libelle %}
- {% include aaLink.html label=label aa=AA %} (Profs :  {% for prof in AA.enseignants %} [{{prof}}]({{site.baseurl}}/personnels/{{prof | downcase}}.html){% if forloop.last == false %}, {% endif %}{% endfor %})
{% endfor %}

{% endfor %}