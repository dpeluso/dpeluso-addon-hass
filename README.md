# Home Assistant Add-ons Repository

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE.md)

Custom Home Assistant add-ons maintained in this repository.

## Included Add-ons

### 1. Node-RED Docker

- **Slug:** `nodered-docker`
- **Location:** [node-red](node-red)
- **Description:** Flow-based programming for the Internet of Things.
- **Ingress:** Yes
- **Supported architectures:** `aarch64`, `amd64`, `armhf`, `armv7`, `i386`
- **Highlights:** Home Assistant API integration, optional SSL, optional HTTP auth, runtime package/customization options.
- **Docs:** [node-red/DOCS.md](node-red/DOCS.md)

### 2. Cloudflare DynDNS

- **Slug:** `cloudflare_dyndns`
- **Location:** [cloudflare-dyndns](cloudflare-dyndns)
- **Description:** Dynamic DNS updates for Cloudflare DNS.
- **Ingress:** No
- **Supported architectures:** `aarch64`, `amd64`, `armv7`, `i386`
- **Auth options:** API token (recommended) or API key + email.
- **Docs:** [cloudflare-dyndns/README.md](cloudflare-dyndns/README.md)

### 3. Audiobookshelf Server

- **Slug:** `audiobookshelfserver`
- **Location:** [audiobookshelfserver](audiobookshelfserver)
- **Description:** Audiobookshelf media server packaged as a Home Assistant add-on with ingress support.
- **Ingress:** Yes
- **Supported architectures:** `aarch64`, `amd64`, `armhf`, `armv7`, `i386`
- **Current pinned upstream version:** `v2.35.1`
- **Docs:** [audiobookshelfserver/README.md](audiobookshelfserver/README.md)

## Install This Repository In Home Assistant

1. Open **Settings -> Add-ons -> Add-on Store**.
2. Open the three-dot menu and select **Repositories**.
3. Add this repository URL:

```text
https://github.com/dpeluso/hass-addons
```

4. Install the add-on you want from the store and configure it using that add-on's documentation.

## Repository Layout

- [node-red](node-red): Node-RED add-on
- [cloudflare-dyndns](cloudflare-dyndns): Cloudflare DynDNS add-on
- [audiobookshelfserver](audiobookshelfserver): Audiobookshelf add-on

## Contributing

Contributions are welcome. See [CONTRIBUTING.md](CONTRIBUTING.md) for workflow and standards.

## License

This repository is licensed under the MIT License. See [LICENSE.md](LICENSE.md).
