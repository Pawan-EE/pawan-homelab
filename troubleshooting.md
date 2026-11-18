# Troubleshooting: fixing a Homepage shortcut

[← Project overview](README.md)

## Case study

**Goal:** change the NAS File Manager shortcut from a private network URL to its Cloudflare web hostname.

**Symptom:** the configuration contained an invalid appended line rather than a clean update to the existing service.

**Root cause:** `href` and `ping` text had been concatenated at the end of the file. The intended service entry still had its previous values.

### Before: malformed appended text

```text
href: https://files.example.comping: https://files.example.com
```

### After: keys inside the correct service block

```yaml
- Storage:
    - NAS File Manager:
        icon: mdi-folder-network
        href: https://files.example.com
        description: Browse and manage NAS files
        ping: https://files.example.com
        server: example-docker
        container: filebrowser-quantum
        showStats: true
```

This reconstruction preserves the structure of the corrected excerpt while replacing the actual domain and integration label. The Docker integration fields require a separate configured integration; the [navigation-only example](homepage-services.yaml.example) avoids that dependency.

## What the record confirms

The later user-provided excerpt shows separate `href` and `ping` fields under the intended service. That supports the **configuration correction**. A final successful page render, click-through, or health check was not captured in the available record.

## Verification workflow

1. Save a private backup of the configuration.
2. Edit the existing named service block and remove the malformed appended line.
3. Validate YAML structure and inspect the diff.
4. Refresh Homepage and check that the configuration renders.
5. Open the shortcut and confirm that it reaches the intended hostname.
6. Check authentication as an allowed and a denied user.

A navigation URL and a health check have different purposes. An Access-protected endpoint can challenge an unauthenticated monitor even when the origin is healthy. Do not remove authentication to satisfy a dashboard status indicator.

## Lessons carried forward

- Work with the configuration's structure, not just line numbers.
- Inspect the changed block before restarting or reloading a service.
- Separate syntax validation, link behavior, and authorization tests.
- Keep the original private configuration out of public support requests.
- Record what was verified instead of equating an edit with a successful deployment.

## Quick diagnostic guide

| Symptom | First check | Next step |
| --- | --- | --- |
| Homepage YAML error | Indentation, duplicate/appended keys, list structure | Restore a known-good block, validate, and inspect the rendered page |
| Shortcut opens old address | The service's `href` | Correct the entry and refresh |
| Protected service appears down | Access challenge or login redirect | Check the origin privately without weakening authentication |
| Tunnel route fails | Local service, connector, target hostname/port | Diagnose from origin outward |
| File permission denied | User scope, ownership, and application identity | Test with a disposable file and the intended account |
| Container restarts | Logs, changed settings, and mount availability | Identify the cause before redeploying |
| OS disk unexpectedly fills | Missing mount or writes to a fallback directory | Stop affected writes and inspect mount state |
| Remote administration unavailable | Host power, network, and private connectivity | Use the local recovery path |

[Operating routine →](operations.md) · [Security notes →](security.md)
