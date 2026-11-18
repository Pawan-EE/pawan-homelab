# Architecture

## Host and service layers

A repurposed laptop runs Ubuntu Server as the host. The recorded design assigns separate LVM storage responsibilities to the operating system, Docker, NAS data, and websites. Exact logical-volume names and capacities are not available in the retrieved project record.

Docker hosts application workloads. Dockge provides a graphical interface for Compose stacks. Cockpit provides host administration, while Homepage presents links and selected service status information. Samba serves network files; FileBrowser Quantum provides browser-based file access.

## Access paths

| Client | Path | Intended scope |
| --- | --- | --- |
| Administrator | Tailscale to host administration interfaces | Private management |
| Trusted LAN user | Samba to NAS data | Authorized file shares |
| Authorized remote web user | Cloudflare edge, Access, Tunnel, application login | Protected browser applications |
| Portfolio visitor | Cloudflare edge and Tunnel to website | Public website only |

Cloudflare Access and the application account are separate controls. Passing the edge login must not automatically grant unrestricted filesystem access.

## Boundaries to validate

The project summary reports remote access and Access authentication working. The exact firewall rules, bind addresses, origin bypass prevention, and per-user permissions were not independently inspected. Verify them before describing the installation as hardened.

Keep management interfaces off public routes. Give each application only the storage it needs. Docker management access is privileged; access to Dockge and the Docker API deserves the same care as host administration.

## Failure domains

One physical host means host failure can interrupt storage and hosted services together. Logical-volume separation does not provide hardware redundancy or an independent backup. Internet and Cloudflare availability affect tunneled access; retain a tested private/local recovery path.
