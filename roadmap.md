# Roadmap

[← Project overview](README.md)

The core stack is recorded as installed. The items below are future work; each phase has a concrete completion condition.

## 01 · Verify the baseline

- [ ] Confirm CPU model, memory, Ubuntu release, and physical disk inventory.
- [ ] Record sanitized LVM capacities and filesystem responsibilities.
- [ ] Identify running application versions and persistent state privately.
- [ ] Verify mounts and service behavior after reboot.
- [ ] Test intended private and protected access with allowed and denied users.

**Done when:** the private inventory matches the running host and a sanitized summary can be published with supporting checks.

## 02 · Make recovery repeatable

- [ ] Define an independent backup destination and retention.
- [ ] Include application configuration/state as well as NAS and website files.
- [ ] Restore disposable test data and a representative application.
- [ ] Write a recovery sequence and record the observed outcome.
- [ ] Test local administration when remote access is unavailable.

**Done when:** recovery has been demonstrated, rather than inferred from a backup job's success.

## 03 · Improve operations

- [ ] Add capacity, host-temperature, and service-failure visibility.
- [ ] Choose meaningful health checks for applications behind authentication.
- [ ] Record update and rollback steps for each stack.
- [ ] Refine Homepage navigation and management workflows.

**Done when:** common failures have an actionable signal and a documented response.

## 04 · Explore assistance and new workloads

- [ ] Prototype read-only NAS diagnostics through an AI chat interface.
- [ ] Evaluate a model backend against the host's available resources.
- [ ] Add narrowly scoped maintenance actions only with explicit approval and audit records.
- [ ] Evaluate additional websites, Navidrome, and isolated ESP32/IoT experiments.

**Guardrail:** an assistant should not receive unrestricted sudo or a writable Docker socket. AI, music, and IoT items are not represented as installed.

[Project decisions →](case-study.md)
