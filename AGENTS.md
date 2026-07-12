# Agent Instructions

This repository contains two independent Home Assistant add-ons:

- [Node-RED](node-red/README.md)
- [Cloudflare DynDNS](cloudflare-dyndns/README.md)

Treat them as separate codebases unless a change clearly spans both.

## Working Rules

- Prefer the existing documentation for details instead of re-explaining them here: [README.md](README.md), [CONTRIBUTING.md](CONTRIBUTING.md), and [node-red/DOCS.md](node-red/DOCS.md).
- Keep changes scoped to the owning add-on directory. Shared repo-level changes should be rare and deliberate.
- Respect the repository's YAML style rules in [.yamllint](.yamllint) when editing YAML files.
- Do not modify add-on-controlled Node-RED settings in [node-red/rootfs/etc/node-red/settings.js](node-red/rootfs/etc/node-red/settings.js); those values are overridden by [node-red/rootfs/etc/node-red/config.js](node-red/rootfs/etc/node-red/config.js) from `/data/options.json`.
- Treat [cloudflare-dyndns/data/run.sh](cloudflare-dyndns/data/run.sh) as the runtime source of truth for Cloudflare DynDNS config generation and validation. It expects either `api_token` or the `api_key` plus `email` combination.

## Editing Surfaces

- Node-RED add-on metadata and runtime behavior live in [node-red/config.json](node-red/config.json), [node-red/build.json](node-red/build.json), [node-red/package.json](node-red/package.json), and [node-red/rootfs/etc/node-red/](node-red/rootfs/etc/node-red/).
- Cloudflare DynDNS add-on metadata and startup behavior live in [cloudflare-dyndns/config.json](cloudflare-dyndns/config.json), [cloudflare-dyndns/build.json](cloudflare-dyndns/build.json), [cloudflare-dyndns/Dockerfile](cloudflare-dyndns/Dockerfile), and [cloudflare-dyndns/data/run.sh](cloudflare-dyndns/data/run.sh).

## Validation

- There is no single repo-wide test harness defined here.
- When editing YAML, validate against [.yamllint](.yamllint).
- When editing shell scripts or runtime entrypoints, check them for syntax and keep generated files and permissions intact.
- When editing Node-RED add-on behavior, verify the config override path still lines up with the add-on schema and runtime defaults.

## Add-On Conventions

- Node-RED uses Home Assistant add-on configuration to control auth, SSL, log level, credential secret, and the HTTP node/static auth settings.
- Cloudflare DynDNS is intentionally minimal: it builds a runtime config file, normalizes logging, and loops forever with the configured retry interval.
- When in doubt, follow the current structure and existing docs rather than introducing new abstractions.