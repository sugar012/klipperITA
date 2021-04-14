---
layout: default
title: Credits
nav_order: 9
permalink: /credits/
---

# Credits
{: .fw-400 }

Puoi aiutarci a tenere aggiornata la guida inviando una Pull request su [GitHub](https://github.com/sugar012/klipperITA/pulls){:target="_blank"}

* Un ringraziamento per la creazione della guida va a:

  * Laurienzu
  * Factotum_res
  * Jacopo Franco
  * TheBugLebowsky
  * sugar0

# Contributors

| contributor | link |
|:--------|:-----|
{% for contributor in site.data.contributors %}{% if contributor.login != "morganfw" and contributor.login != "dependabot[bot]" %}|![]({{ contributor.avatar_url }}){: style="width: 20px; vertical-align: bottom;"} **{{ contributor.login }}**|[{{ contributor.html_url }}]({{ contributor.html_url }}){:target="_blank"}|
{% endif %}{% endfor %}
