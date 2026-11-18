# Troubleshooting and lessons learned

## Observed issue: malformed Homepage YAML

The project discussion includes a malformed line in which a new file-manager URL was appended to an existing key instead of replacing the intended entries:

```text
href: https://files.example.comping: https://files.example.com
```

The subsequent user-provided excerpt shows separate, correctly indented `href` and `ping` keys under the NAS File Manager entry. This confirms the text correction; a final browser or health-check success was not shown in the retrieved record.

**Lesson:** edit the named service block rather than appending replacement text to the end of a file. Back up the configuration, inspect the diff, validate YAML, and then confirm the rendered dashboard. Avoid copying line-number-based edits across different files.

## Diagnostic guide

| Symptom | Inspect first | Useful next step |
| --- | --- | --- |
| Homepage YAML error | Indentation, duplicate/appended keys, list structure | Restore last known-good block and validate YAML |
| Shortcut opens old address | The service's href field | Update that entry and refresh the dashboard |
| Protected service appears down | Login redirects or Access challenge | Check the origin privately; keep authentication enabled |
| Tunnel route fails | Local application, connector state, target hostname/port | Work outward from origin to edge |
| File access denied | Application scope, account, filesystem permissions | Test a disposable file with the intended user |
| Container restarts | Recent changes, logs, mount availability | Inspect privately before redeploying |
| Host disk unexpectedly fills | Missing mount or data written to OS volume | Stop affected writes and verify mount state |
| Remote admin unavailable | Host power, network, Tailscale connectivity | Use a tested local recovery path |

## Safe investigation

Change one variable at a time. Preserve relevant logs privately. Use a disposable file for permission tests. Do not disable authentication, publish admin ports, or use unrestricted recursive permissions to make an error disappear.
