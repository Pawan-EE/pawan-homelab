# Graphical administration and containers

## Docker and Dockge

The project record reports Docker and Dockge installed. Dockge manages Compose stacks through a web interface; use it to inspect stack state and logs and perform deliberate deployments.

Keep each stack definition with its associated private configuration. Track sanitized templates in Git, while credentials and application databases remain outside the repository. Before an update, record the running image version, back up persistent state, inspect release notes, and retain a rollback plan. Reverting an image may not reverse a database migration.

Docker API access can control the host. Restrict Dockge to authorized administrators over the private access path. Do not expose the Docker socket to unrelated applications.

Reference: [Dockge upstream project](https://github.com/louislam/dockge).

## Cockpit

Cockpit is recorded as installed for host administration. Use its available pages to inspect services, logs, storage, updates, and resource usage; the exact installed extensions have not been inventoried. Keep host administration private and use a trusted HTTPS connection. Retain SSH as a recovery path.

## Homepage

Homepage centralizes service links. The discussion includes entries for the portfolio and FileBrowser Quantum, plus Docker status fields. The sanitized example intentionally omits Docker integration and live monitoring so it does not require socket access or private credentials.

A navigation link and a health check serve different purposes. An Access-protected URL may return a login page or redirect to an unauthenticated monitor even when the origin is healthy. Do not weaken Access just to make a dashboard indicator green.

Reference: [Homepage service configuration](https://gethomepage.dev/configs/services/).

## Operational routine

1. Review storage capacity, failed services, container restarts, and backups.
2. Investigate logs privately; sanitize before sharing.
3. Back up persistent state before updates.
4. Change one stack at a time and check application behavior.
5. Verify private and protected access after network changes.
6. Record the version and rollback outcome in private maintenance notes.

No uptime, performance, or restore success is claimed without measurement.
