---
layout: default
title: Configurazioni Moonraker
parent: Extra
nav_order: 5
has_children: false
permalink: /extra/configurazioni-moonraker/
---

# Configurazioni Moonraker
{: .fw-400 }

Moonraker è un server web basato su Python 3 che espone delle [API](https://it.wikipedia.org/wiki/Application_programming_interface){:target="_blank"}.

Le applicazioni client, per esempio le WebUI come Fluidd, Mainsail e affini, possono utilizzare Moonraker per interagire con Klipper.

**ATTENZIONE: Guida in stesura/completamento**
{: .fw-400 }

Esempio di configurazione base di Moonraker

{% raw %}
```
# Sample Moonraker Configuration File

[server]
# Bind server defaults of 0.0.0.0, port 7125
enable_debug_logging: True
config_path: ~/printer_config

[authorization]
enabled: True
trusted_clients:
# Enter your client IP here or range here
 192.168.1.0/24
cors_domains:
# Allow CORS requests for Fluidd
 http://app.fluidd.xyz

# Enable Octoprint compatibility for Slicer uploads
# Supports Cura, Slic3r, and Slic3r dervivatives
# (PrusaSlicer, SuperSlicer)
[octoprint_compat]
```
{% endraw %}
