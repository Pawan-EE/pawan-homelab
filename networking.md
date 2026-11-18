# Remote access and web publishing

[← Project overview](README.md)

## Tailscale

The project record reports Tailscale private networking for remote administration. Keep device names, addresses, identity details, and policy exports private. Verify which administrators and devices can reach SSH, Cockpit, and Dockge; membership alone should not substitute for deliberate access rules.

## Cloudflare Tunnel

The recorded setup publishes selected web applications and a portfolio through a custom domain and Cloudflare Tunnel. A tunnel connector establishes outbound connectivity to Cloudflare, avoiding the need for a publicly routable origin address. This does not automatically protect every application.

Reference: [Cloudflare Tunnel documentation](https://developers.cloudflare.com/cloudflare-one/networks/connectors/cloudflare-tunnel/).

## Cloudflare Access

Cloudflare Access with email OTP is reported in the project summary. Exact application definitions, allowed identities, session settings, and origin restrictions were not exported or audited.

Keep the portfolio's intended public route separate from protected dashboard and file-manager routes. Test an allowed identity, a disallowed identity, and a signed-out browser. An application login and filesystem authorization remain necessary after edge authentication.

## Generic route map

| Example hostname | Purpose | Intended policy |
| --- | --- | --- |
| www.example.com | Portfolio | Public |
| dashboard.example.com | Homepage | Explicit Access policy |
| files.example.com | FileBrowser Quantum | Access plus application permissions |

These are reserved example domains, not the real deployment.

## Validation sequence

Check local application health first, then connector health, hostname routing, and Access behavior. Confirm that an alternative address or port does not bypass the intended controls. Keep actual origin URLs, tunnel identifiers, tokens, and policy exports out of screenshots and commits.
