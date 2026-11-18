# Examples & configuration guide

[← Project overview](README.md)

These small examples make the configuration style reviewable without publishing private deployment files.

| File | Demonstrates | Deliberately excludes |
| --- | --- | --- |
| [Homepage services](homepage-services.yaml.example) | Groups, descriptions, navigation links | Private addresses, Docker API integration, credentials |
| [Samba share](samba-share.conf.example) | An authenticated, read-only share fragment | Actual users, real data paths, host-wide configuration |
| [Deployment worksheet](deployment-worksheet.md) | A private inventory and validation checklist | Filled-in infrastructure details |

## How to read the examples

`example.com` is a reserved documentation domain. `exampleuser` and `/srv/example-nas` are placeholders. The Samba fragment is intentionally read-only; it is not the original share configuration.

The Homepage example can explain the service-entry structure, but it does not configure application authentication. Following a link still requires whatever access the target application enforces.

## Before using an example

Make a private copy, adapt it to the installed version and local environment, validate the syntax, and test with disposable data and least-privilege accounts. Keep the private version outside this repository.

## Why there is no one-command deployment

Exact image versions, host mounts, application state paths, and live policy definitions were not available in the project record. A guessed Compose stack would be misleading and could mount the wrong data.

The repository therefore documents the implementation and provides bounded examples. Version-specific stack templates can be added after the [baseline inventory](roadmap.md) is verified.
