# Lovelace tempometer-gauge-card
A Home Assistant lovelace custom gauge card for barometer, thermometer, humidity meter or anything you want with custom icons.

![Barometer style](https://user-images.githubusercontent.com/25659602/63027159-b7464980-beac-11e9-8d7a-2143eeead609.png)![Thermometer style](https://user-images.githubusercontent.com/25659602/63299603-76986700-c2d6-11e9-8739-e9cbb441a94b.png)![Custom style](https://user-images.githubusercontent.com/25659602/73101770-b9e3ab00-3ef0-11ea-9784-7f721de5a24c.png)



## Usage
Add this custom card to your home assistant instance. Reference it into your lovelace configuration.
```
  - type: js
    url: /local/lovelace/tempometer-gauge-card.js
```
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

Example:
```yaml
severity:
  green: 1020
  yellow: 1000
  red: 900
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
```

Maybe more to come ! PR are welcome and i can have a look to features requests.
