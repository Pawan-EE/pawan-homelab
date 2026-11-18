# Operating the lab

[← Project overview](README.md)

The management layer answers three different questions: **Where is the service?** (Homepage), **What is the application doing?** (Dockge), and **What is the host doing?** (Cockpit).

## Which tool to use

| Task | Starting point | Check afterward |
| --- | --- | --- |
| Find a service | Homepage | The link reaches the intended application |
| Inspect a Compose stack | Dockge | Container state, logs, and persistent mounts |
| Investigate host resource use | Cockpit | Relevant service, storage, and system logs |
| Diagnose a low-level issue | SSH | A targeted change and a recorded result |
| Manage files in a browser | FileBrowser Quantum | User scope and file operation permissions |
| Access a network share | Samba client | Share and filesystem authorization |

## Docker and Dockge

Docker and Dockge are recorded as installed. Dockge provides browser-based management of Compose stacks. Keep actual stack files and private configuration together on the host, with sanitized templates in Git.

Treat Docker management access as privileged. Restrict Dockge to intended administrators and keep the Docker API away from unrelated applications.

[Upstream Dockge documentation](https://github.com/louislam/dockge)

## Cockpit

Cockpit provides graphical host administration. Use the pages available in the installed configuration to inspect services, logs, storage, updates, and resources. The project's exact extensions are not inventoried here.

Keep administration on the private path and use a trusted HTTPS connection. SSH remains useful when the graphical interface cannot explain or recover a failure.

## Homepage

Homepage acts as the service directory. The project discussion contains portfolio and FileBrowser entries and Docker status fields. The public [services example](homepage-services.yaml.example) uses navigation-only links so it does not need private integrations.

A shortcut and a health check serve different purposes. Access can present a login challenge to an unauthenticated monitor even when an origin is healthy.

[Upstream Homepage service configuration](https://gethomepage.dev/configs/services/)

## Recommended update runbook

This is a documented procedure to adopt, not a claim that every past update followed it.

1. Identify the stack, current image version, persistent data, and dependencies.
2. Back up application state and note how recovery will work.
3. Review release notes and any database migration requirements.
4. Update one stack at a time through the chosen management workflow.
5. Check logs, application behavior, file access, and intended authentication.
6. Record the outcome and keep the previous version until validation is complete.

An older image may not read a database after a migration. A rollback plan must account for data as well as the container.

## When something breaks

Start with the layer closest to the symptom: application, container, host, then remote path. Preserve logs privately, change one variable at a time, and test with disposable data. Avoid replacing a stack or broadening permissions before identifying the cause.

[Troubleshooting →](troubleshooting.md) · [Recovery priorities →](roadmap.md)
