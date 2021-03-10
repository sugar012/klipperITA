---
layout: default
title: M204 - Set Starting Acceleration
nav_order: 3
parent: Raccolta Macro di Desuuuu
grand_parent: Esempi di Macro su Klipper
has_children: false
permalink: /m204/
---

## M204 - Set Starting Acceleration

{% raw %}
```
[gcode_macro M204]
rename_existing: M204.1
default_parameter_F: 0.5
gcode:
  {% if 'S' in params %}
    SET_VELOCITY_LIMIT ACCEL={S} ACCEL_TO_DECEL={ S|float * F|float }
  {% else %}
    {% if 'P' in params %}
      {% if 'T' in params %}
        {% if P|int < T|int %}
          SET_VELOCITY_LIMIT ACCEL={P} ACCEL_TO_DECEL={ P|float * F|float }
        {% else %}
          SET_VELOCITY_LIMIT ACCEL={T} ACCEL_TO_DECEL={ T|float * F|float }
        {% endif %}
      {% else %}
        SET_VELOCITY_LIMIT ACCEL={P} ACCEL_TO_DECEL={ P|float * F|float }
      {% endif %}
    {% elif 'T' in params %}
      SET_VELOCITY_LIMIT ACCEL={T} ACCEL_TO_DECEL={ T|float * F|float }
    {% endif %}
  {% endif %}
  ```
  {% endraw %}
