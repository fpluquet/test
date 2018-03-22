---
# You don't need to edit this file, it's empty on purpose.
# Edit theme's home layout instead if you wanna make some changes
# See: https://jekyllrb.com/docs/themes/#overriding-theme-defaults
layout: default
---
{% for UE in site.data.grille %}
# {{ UE[0] }} : {{UE[1].libelle}} ({{UE[1].quadrimestre}})

{% assign AAs = site.data.AA | where:"UE", UE[0]%}
{% for AA in  AAs %}
- {{AA.accronyme}} : {{AA.libelle}} (Profs :  {% for prof in AA.enseignants %} [{{prof}}]({{site.baseurl}}/personnels/{{prof | downcase}}.html){% if forloop.last == false %}, {% endif %}{% endfor %})
{% endfor %}

{% endfor %}