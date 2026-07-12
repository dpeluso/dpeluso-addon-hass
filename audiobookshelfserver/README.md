# Home Assistant Add-on: Audiobookshelf Server

Audiobookshelf is a self-hosted audiobook and podcast server.

This add-on packages the upstream release pinned in [build.json](build.json) and exposes it through Home Assistant ingress.

## Details

- Latest pinned release: v2.35.1
- Ingress path: handled by Home Assistant
- Base path inside the container: root (`ROUTER_BASE_PATH` is cleared so ingress can own the URL)

## Storage

- [config](config.json): Audiobookshelf application config and database files
- [media](config.json): Your audiobook and podcast library
- [share](config.json): Optional shared files

## Notes

- Audiobookshelf requires a websocket-capable reverse proxy, which is why this add-on uses ingress.
- The upstream project documents a fixed `/audiobookshelf` subpath for traditional reverse proxy setups, but the add-on clears that base path so the Home Assistant ingress URL remains authoritative.
- To update to a newer upstream release, change the tag in [build.json](build.json) and keep [config.json](config.json) in sync.# Audiobookshelf Home Assistant Add-on
![Static Badge](https://img.shields.io/badge/release-2.35.1-blue)
![Project Stage][project-stage-shield]
[![License][license-shield]](LICENSE.md)

![Supports aarch64 Architecture][aarch64-shield]
![Supports amd64 Architecture][amd64-shield]

![Project Maintenance][maintenance-shield]
[![GitHub Activity][commits-shield]][commits]

[aarch64-shield]: https://img.shields.io/badge/aarch64-yes-green.svg
[amd64-shield]: https://img.shields.io/badge/amd64-yes-green.svg

[commits-shield]: https://img.shields.io/github/commit-activity/y/bigred10151990/ha-addons.svg
[commits]: https://github.com/bigred10151990/ha-addons/commits/main
[license-shield]: https://img.shields.io/github/license/bigred10151990/ha-addons.svg
[maintenance-shield]: https://img.shields.io/maintenance/yes/2026.svg
[project-stage-shield]: https://img.shields.io/badge/project%20stage-production%20ready-brightgreen.svg

[![](https://img.shields.io/static/v1?label=Sponsor&message=%E2%9D%A4&logo=GitHub&color=%23fe8e86)](https://github.com/sponsors/bigred10151990)

This app runs [Audiobookshelf](https://www.audiobookshelf.org/) inside Home Assistant OS.

This app has access to the addon_config, backup, media, and share folders.  
Audiobookshelf Version 2.35.1

## Installation
[![Open your Home Assistant instance and show the add app repository dialog with a specific repository URL pre-filled.](https://my.home-assistant.io/badges/supervisor_add_addon_repository.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https%3A%2F%2Fgithub.com%2Fbigred10151990%2Fha-addons)

Install the **Audiobookshelf** app from this repo and start it.

Home Assistant Ingress is supported, so you can open Audiobookshelf directly from the add-on panel without exposing a network port.
Audiobookshelf supports subfolder hosting on the fixed `/audiobookshelf` path, which is the path this add-on uses for ingress.

If you want to use a network drive please add it to homeassistant in Network Storage with the media usage option.

## Configuration

- **CONFIG_PATH** (default: /config)
  - Path to the config directory.
  - It will contain the database (users/books/libraries/settings). This location must not be mounted over the network.

- **METADATA_PATH** (default: /metadata)
  - Path to the metadata directory.
  - It will contain cache, streams, covers, downloads, backups and logs.

- **BACKUP_PATH** (default: /metadata/backups)
  - Path to where backups are stored.
  - Backups contain a backup of the database in /config and images/metadata stored in /metadata/items and /metadata/authors

- **ALLOW_CORS** (default: '0')
  - Allow Cross-Origin Resource Sharing if set to '1'.

- **ALLOW_IFRAME** (default: '1')
  - Allow use of iframes. This can also be done at the reverse proxy level.

- **ACCESS_TOKEN_EXPIRY** (default: '43200')
  - Access token expiration in seconds (default: 43200 = 12 hours)

- **REFRESH_TOKEN_EXPIRY** (default: '604800')
  - Refresh token expiration in seconds (default: 604800 = 7 days)


## Disclaimers and copyright information

This add-on wraps the official Audiobookshelf container image so it runs as a Home Assistant add-on with ingress support.

Audiobookshelf Self-hosted audiobook server
Copyright (C) 2021  advplyr

This program comes with ABSOLUTELY NO WARRANTY










