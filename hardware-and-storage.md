# Hardware and storage

## Recorded hardware

| Item | Available project record |
| --- | --- |
| Platform | Samsung Galaxy Book Flex |
| CPU | Intel Core i5 mentioned in prior discussion; exact model unverified |
| Memory | 8 GB mentioned in prior discussion; not independently measured |
| OS | Ubuntu Server; release unverified |
| Disk | Capacity, model, health, and physical layout unverified |
| Operation | Repurposed as a headless NAS and application host |

No serial numbers, device UUIDs, MAC addresses, or host identifiers are published.

## Storage responsibilities

The prior summary describes LVM volumes for the OS, Docker, NAS, and websites. This is a functional map, not a claim about exact mount points:

| Responsibility | Data to protect |
| --- | --- |
| OS | System configuration and recovery notes |
| Docker | Compose definitions and persistent application state |
| NAS | User files and share permissions |
| Websites | Site content and deployment state |

The paths in examples are generic substitutes. Do not infer partition sizes or filesystem types from them.

## Private verification checklist

Inspect the host locally before changing storage. Read-only tools such as `lsblk -f`, `df -hT`, `pvs`, `vgs`, `lvs`, and `findmnt` can establish the actual layout. Their output may contain private identifiers; retain it privately and publish only a manually sanitized summary.

Confirm persistent mounts after reboot, available capacity, application ownership, and that container data lands on the intended filesystem. If a mount is absent, stop affected writes before the application fills the OS filesystem.

Do not resize, format, repartition, or recursively change permissions based on this document. Those actions require a verified inventory and a tested backup.

## Reliability work still to validate

Check ventilation, temperature, battery condition, power-loss recovery, and lid/suspend behavior. Record a backup schedule and perform a restore test. LVM separation and a laptop battery do not establish backup or high availability.
