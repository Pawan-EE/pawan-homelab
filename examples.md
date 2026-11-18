# Sanitized examples

These files demonstrate structure, not the live NAS configuration. Do not deploy this directory as a complete stack.

- [Homepage services](homepage-services.yaml.example): navigation-only entries using reserved domains. No Docker API or monitoring credentials are required.
- [Samba share](samba-share.conf.example): a restrictive share fragment with a generic path and account.
- [Deployment worksheet](deployment-worksheet.md): fields to fill privately when preparing real stacks and access routes.

Exact Dockge, FileBrowser Quantum, and cloudflared deployment versions were unavailable. Runnable Compose files are intentionally deferred until version-specific settings and storage mappings are verified. Never fill these public templates with live secrets.
