# Lovelace tempometer-gauge-card

A Home Assistant lovelace custom gauge card for barometer, thermometer, humidity meter or anything you want with custom icons.
![pressure-and-temp](https://user-images.githubusercontent.com/25659602/106396921-2dc16900-640b-11eb-9921-baabe2fdb378.png)
![humidity-and-custom](https://user-images.githubusercontent.com/25659602/106397020-a9231a80-640b-11eb-882e-3b38cde7fa69.png)

## Usage
Add this card via HACS (recommended)

Or manually :
Add this custom card to your home assistant instance. Reference it into your lovelace configuration.
```
  - type: js
    url: /local/lovelace/tempometer-gauge-card.js
```

Finally :
Add it as a custom card to your lovelace : `'custom:tempometer-gauge-card'`.

## Options
### Card options
| **Option** | **Type** | **Description** |
|-|:-:|-|
| `entity` ***(required)*** | string | The barometer entity to track. |
| `min` ***(required)*** | number | The gauge's minimum value |
| `max` ***(required)*** | number | The gauge's maximum value |
| `entity_min` | string | The entity that define the minimum pressure/temperature reached (you have to create this entity, the card will not compute it !) |
| `entity_max` | string | The entity that define the maximum pressure/temerature reached (you have to create this entity, the card will not compute it !) |
| `title` | string | Card title to show. |
| `style` | string | Set this to `thermometer`, `humidity` or `custom` to change icons. (Default will be barometer theme, custom will need icon1, icon2, icon3 !) |
| `measurement` | string | Custom unit of measurement |
| `icon1` | string | Icon on left side in custom style. |
| `icon2` | string | Icon on center in custom style. |
| `icon3` | string | Icon on right side in custom style. |
| `severity` | [severity object](#severity-object) | Severity map to change the gauge color. |
| `decimals` | number | Decimal precision of entity value. |

#### Severity object
| **Option** | **Type** | **Description** |
|-|:-:|-|
| green ***(required)*** | number | Value for the color green.
| yellow ***(required)*** | number | Value for the color yellow.
| red ***(required)*** | number | Value for the color red.
| max | number | Maximum value of the last step, normal color will be rendered above

Example:
```yaml
severity:
  green: 1020
  yellow: 1000
  red: 900
  max: 1100
```

## Tip
The maximum and minimum bounds have a hover tooltip with their own values.

## Full examples
```yaml
type: 'custom:tempometer-gauge-card'
entity: sensor.barometer
min: 980
max: 1050
entity_min: sensor.barometer_min_this_week
entity_max: sensor.barometer_max_this_week
title: Barometer
decimals: 0
severity:
  green: 1020
  yellow: 1000
  red: 900
```
```yaml
type: 'custom:tempometer-gauge-card'
entity: sensor.temperature
min: 15
max: 30
entity_min: sensor.temperature_min_this_week
entity_max: sensor.temperature_max_this_week
title: Thermometer
style: thermometer
severity:
  green: 22
  yellow: 24
  red: 27
```
```yaml
type: 'custom:tempometer-gauge-card'
entity: sensor.power
min: 0
max: 4000
entity_min: sensor.power_min_this_week
entity_max: sensor.power_max_this_week
title: Power Meter
style: custom
icon1: mdi:flash-off
icon2: mdi:flash-outline
icon3: mdi:flash
severity:
  green: 1000
  yellow: 2000
  red: 3000
  max: 5000
```

Maybe more to come ! PR are welcome and i can have a look to features requests.
