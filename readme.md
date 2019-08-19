# lovelace-barometer-gauge-card
A Home Assistant lovelace custom card for barometer.

![Barometer Gauge Card](https://user-images.githubusercontent.com/25659602/63027159-b7464980-beac-11e9-8d7a-2143eeead609.png)

## Usage
Add this custom card to your home assistant instance. Reference it into your lovelace configuration.

Add a custom card to your lovelace : `'custom:barometer-gauge-card'`.

## Options
- `entity` : *(Required)* The barometer entity to track.
- `entity_min` : *(Optional)* The entity that define the minimum pressure reached (you have to create this entity, the card will not compute it !)
- `entity_max` : *(Optional)* The entity that define the maximum pressure reached (you have to create this entity, the card will not compute it !)
- `title` : *(Optional)* Card title to show.
- `style` : *(Optional)* Set this to thermometer to change icons to thermoter theme.
- `severity` : *(Optional)* Severity map to change the gauge color. See above.

```yaml
severity:
  green: 1020
  yellow: 1000
  red: 900
```
## Tip
The maximum and minimum bounds have a hover tooltip with their own values.

## Full example
```yaml
type: 'custom:barometer-gauge-card'
entity: sensor.barometer
entity_min: sensor.barometer_min_this_week
entity_max: sensor.barometer_max_this_week
title: Barometer
severity:
  green: 1020
  yellow: 1000
  red: 900
```

Maybe more to come ! PR are welcome and i can have a look to features requests.
