# Airports

SkyFolio airport database and mapping data.

## Disclaimer

This project is not affiliated with, endorsed by, or connected to Skycards in any way. This is an independent community project. All Skycards data remains the property of Skycards and their respective owners.

## Data Source

This repo references airport data from the [Skycards Community Data Project](https://github.com/Skycards/Changes), which automatically tracks and archives data from publicly available Skycards API endpoints.

Their `airports.json` serves as the canonical airport list. This repo builds on top of that data with additional mapping used by the SkyFolio app.

## How It Works

The Skycards/Changes repo fetches airport data from the Skycards API every 30 minutes and commits any changes. We periodically pull their latest `airports.json` and use it as the base layer for our mapping data.

**Their repo provides:** the full airport list including IATA, ICAO, name, coordinates, and placeCode for each airport.

**This repo provides:** a placeCode mapping that translates each placeCode into a country name, continent, and regional grouping where applicable.

## Repo Structure

```
placeCode-mapping.json   # Maps placeCode to country, continent, and region
README.md                # This file
```

## placeCode Mapping

The `placeCode-mapping.json` file maps every placeCode found in the Skycards airport data to its country and continent. For countries with regional groupings in the game, it also includes a region field.

Countries with regional breakdowns:
- Australia (8 states/territories)
- Canada (13 provinces/territories)
- China (31 provinces/regions)
- United States (50 states)

All other countries map directly to a country and continent with no region field.

### Example entries

Standard country:
```json
{
  "placeCode": "FR",
  "country": "France",
  "continent": "Europe"
}
```

Country with region:
```json
{
  "placeCode": "US-TX",
  "country": "United States",
  "continent": "North America",
  "region": "Texas"
}
```

## App Integration

The SkyFolio app uses this data to build its airport hierarchy:

1. Pull `airports.json` from Skycards/Changes for the full airport list
2. Look up each airport's `placeCode` in `placeCode-mapping.json`
3. Group airports by continent, then country, then region (where applicable)

This gives users a browsable structure instead of a flat list, which is especially useful for countries with hundreds of airports.

## Links

- [Skycards/Changes](https://github.com/Skycards/Changes) (upstream data source)
- [SkyFolio subreddit](https://reddit.com/r/SkyFolio)
