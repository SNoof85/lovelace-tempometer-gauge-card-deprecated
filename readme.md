# Lovelace tempometer-gauge-card
A Home Assistant lovelace custom gauge card for barometer or thermometer.

![Barometer style](https://user-images.githubusercontent.com/25659602/63027159-b7464980-beac-11e9-8d7a-2143eeead609.png)![Thermometer style](https://user-images.githubusercontent.com/25659602/63298831-b65e4f00-c2d4-11e9-88fc-292450dfe8c3.png)


## Usage
Add this custom card to your home assistant instance. Reference it into your lovelace configuration.

Add a custom card to your lovelace : `'custom:tempometer-gauge-card'`.

## Options
- `entity` : *(Required)* The barometer entity to track.
- `entity_min` : *(Optional)* The entity that define the minimum pressure reached (you have to create this entity, the card will not compute it !)
- `entity_max` : *(Optional)* The entity that define the maximum pressure reached (you have to create this entity, the card will not compute it !)
- `title` : *(Optional)* Card title to show.
- `style` : *(Optional)* Set this to thermometer to change icons to thermoter theme. (Default will be barometer theme)
- `severity` : *(Optional)* Severity map to change the gauge color. See above.

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
entity_min: sensor.barometer_min_this_week
entity_max: sensor.barometer_max_this_week
title: Barometer
severity:
  green: 1020
  yellow: 1000
  red: 900
```
```yaml
type: 'custom:tempometer-gauge-card'
entity: sensor.temperature
entity_min: sensor.temperature_min_this_week
entity_max: sensor.temperature_max_this_week
title: Thermometer
style: thermometer
severity:
  green: 22
  yellow: 24
  red: 27
```

Maybe more to come ! PR are welcome and i can have a look to features requests.
