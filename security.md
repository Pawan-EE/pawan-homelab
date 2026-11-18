# Security and publication boundaries

[← Project overview](README.md)

## What is intentionally excluded

This repository contains no actual passwords, tokens, private keys, tunnel credentials, user databases, private domains, network addresses, personal server login names, hardware identifiers, or raw configuration exports.

Examples use reserved domains, generic paths, and symbolic accounts. They are authored illustrations rather than redacted copies of live files.

## Controls to maintain and verify

- Keep administration on a private access path.
- Give file users and applications only the access they need.
- Keep application authentication behind edge authentication where applicable.
- Protect Docker management access as privileged host access.
- Store credentials outside Git and restrict access to secret files.
- Review updates, backup coverage, and recovery procedures.
- Check for alternate routes that bypass intended authentication.

These are operating expectations, not a certification of the current host.

## Before a public commit

Review the complete staged diff and new file list. Inspect URLs, addresses, logs, screenshots, environment files, database exports, and certificates. Check both content and filenames. A .gitignore file prevents some accidental additions but does not remove previously tracked files or substitute for review.

If a secret is committed, revoke or rotate it first, then address repository history and any copies. Deleting the latest file alone does not make the old secret private again.

## Scope

This publication documents the project; it does not modify the live NAS, change network policy, rotate credentials, or establish a tested backup.
