# From laptop to HomeLab

[← Project overview](README.md)

## Challenge

The project brought several practical needs together: a place for shared files, a host for a personal website, remote access, and a manageable way to operate the services. The later discussion made one usability requirement especially clear: routine administration should not require typing shell commands every time.

## Solution

A Samsung Galaxy Book Flex was repurposed as a headless Ubuntu Server host. The recorded implementation combines four layers:

1. **Host and storage:** Ubuntu Server, SSH, and LVM responsibilities for the OS, Docker, NAS data, and websites.
2. **Applications and files:** Docker workloads, a portfolio website, Samba, and FileBrowser Quantum.
3. **Management:** Dockge for Compose stacks, Cockpit for host administration, and Homepage for navigation and service information.
4. **Access:** Tailscale for private connectivity and Cloudflare Tunnel with Access for selected web applications.

This is a personal integration project: the work is in assembling, configuring, operating, and documenting existing tools. It does not claim authorship of those upstream products.

## Engineering decisions and tradeoffs

| Decision | Why it fits the project | Tradeoff or follow-up |
| --- | --- | --- |
| Reuse a laptop | Builds practical infrastructure using existing hardware | One host remains a shared failure domain; thermal and power behavior need attention |
| Separate storage responsibilities | Makes OS, application state, and user data easier to reason about | Logical separation does not provide redundancy or backup |
| Use graphical management | Makes frequent inspection and service tasks more accessible | Management interfaces require restricted access; SSH is still useful for recovery |
| Run applications in containers | Gives workloads explicit runtime and persistent-data boundaries | A container image alone does not capture database state or host dependencies |
| Separate private admin and web access | Distinguishes administrator tools from browser-facing services | Policies and alternative routes must be tested to prevent bypass |
| Publish sanitized documentation | Makes the project reviewable without exposing the host | Readers cannot reproduce the exact environment from private values |

## A representative debugging example

The Homepage shortcut change illustrates the troubleshooting approach:

- **Observe:** inspect the service block and the unexpected appended line.
- **Explain:** two YAML keys were concatenated outside the intended entry.
- **Correct:** remove the malformed line and edit the existing keys in place.
- **Verify:** inspect the corrected excerpt, then test rendering and navigation.
- **Learn:** validate structure and review a diff instead of repeating positional edits blindly.

The available record demonstrates the corrected text. The final browser test is a follow-up check, not a claimed measurement. [Full case study →](troubleshooting.md)

## What this demonstrates

The project connects Linux host administration, application management, storage, file access, and networking in one working context described by the build discussion. It also shows a willingness to document failure modes and to distinguish an installed feature from a future improvement.

No cost savings, throughput, uptime, or recovery-time figures are asserted without measurements. The next iteration focuses on making recovery and operational validation as deliberate as the initial setup.

[Service catalog →](service-catalog.md) · [Roadmap →](roadmap.md)
