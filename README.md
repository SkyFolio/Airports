# Airports

SkyFolio airport database and mapping data.

## Disclaimer

This project is not affiliated with, endorsed by, or connected to Skycards in any way. This is an independent community project. All Skycards data remains the property of Skycards and their respective owners.

## Data Source

This repo references airport data from the [Skycards Community Data Project](https://github.com/Skycards/Changes), which automatically tracks and archives data from publicly available Skycards API endpoints.

Their `airports.json` serves as the canonical airport list. This repo builds on top of that data with additional enrichment fields used by the SkyFolio app.

## How It Works

The Skycards/Changes repo fetches airport data from the Skycards API every 30 minutes and commits any changes. We periodically pull their latest `airports.json` and use it as the base layer for our enrichment data.

**Their repo provides:** the full airport list with all fields from the Skycards API.

**This repo adds:** geographic enrichment like coordinates, continent, country, and region mapping for use in SkyFolio on iOS and Android.

## Repo Structure

```
airports.json        # Enrichment/mapping data (coming soon)
README.md            # This file
```

## Status

Setting up the initial data pipeline and enrichment schema. More to come.

## Links

- [Skycards/Changes](https://github.com/Skycards/Changes) (upstream data source)
- [SkyFolio subreddit](https://reddit.com/r/SkyFolio)
