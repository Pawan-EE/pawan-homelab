# Service catalog

[← Project overview](README.md)

A map of the recorded stack and the job each component performs. “Recorded” means described in the project discussion; it is not a current health status.

| Layer | Component | Job in the lab | Intended audience |
| --- | --- | --- | --- |
| Host | Ubuntu Server | Operating system for the headless host | Administrator |
| Host | SSH | Command-line administration and recovery | Administrator |
| Storage | LVM | Separates storage responsibilities | Administrator |
| Runtime | Docker | Runs application workloads | Administrator |
| Management | Dockge | Manages Compose stacks through a browser | Administrator |
| Management | Cockpit | Inspects and manages the host | Administrator |
| Navigation | Homepage | Central directory of service links and selected status | Authorized users |
| Files | Samba | Network file shares for trusted clients | Authorized file users |
| Files | FileBrowser Quantum | Browser-based file management | Authorized file users |
| Connectivity | Tailscale | Private remote connectivity | Authorized devices/users |
| Web routing | Cloudflare Tunnel | Connects selected origins to the Cloudflare edge | Application visitors |
| Web identity | Cloudflare Access | Controls entry to protected web applications | Allowed identities |
| Application | Portfolio website | Serves personal portfolio content | Public visitors |

## Keep these roles distinct

**Homepage is the directory, not the administrator.** A dashboard link opens another service; it does not grant access to that service.

**Cockpit and Dockge work at different layers.** Cockpit concerns the host. Dockge concerns Compose stacks and has privileged implications through Docker access.

**Access and FileBrowser permissions are separate.** Edge authentication determines who may reach the application; application and filesystem permissions determine what files that person may use.

**Tailscale and Tunnel serve different paths.** The project uses private networking for administration and hostname-based web routing for selected applications.

## Persistent data to account for

| Component | State to identify and protect privately |
| --- | --- |
| Docker applications | Compose definitions, configuration, persistent volumes, and database state |
| FileBrowser Quantum | User/account settings, application state, and intended file sources |
| Samba | Share definitions, account mappings, and filesystem ownership |
| Homepage | Dashboard configuration and any private integration settings |
| Portfolio | Site content and deployment configuration |
| Host/network services | Recovery notes, mount definitions, and private authentication material |

Paths and storage details depend on the installed configuration. [Use the private worksheet](deployment-worksheet.md) when preparing an inventory.

## Not part of the completed stack

The NAS AI assistant, Navidrome, and ESP32/IoT work are proposals. They remain in the [roadmap](roadmap.md).

[Operations →](operations.md) · [File services →](file-services.md) · [Networking →](networking.md)
