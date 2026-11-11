# Homelab documentation workflow

The owner authorizes automatic documentation updates to `J0N3B0I/Proxmox-homelab` for homelab changes performed during assistant sessions.

After completing a change:

1. Verify the resulting behavior and service health using checks appropriate to the change.
2. Update the relevant repository documentation with what changed, why, validation results, and any material limitations or follow-up work. Record significant changes with a date. Keep incident history distinguishable from the current configuration.
3. Review the proposed publication for private information. Use placeholders for private addresses, host-specific identifiers, and personal account details. Keep credentials, API keys, tokens, private keys, application databases, and raw configuration backups out of Git.
4. Read the current repository state before writing. Preserve unrelated edits and history. Publish the documentation update using the existing GitHub connection when available. This standing authorization covers documentation commits to the default branch without another conversational approval request.
5. Include the GitHub update in the completion message. If publishing fails, retain the prepared update locally and report the pending upload accurately.

Document actual outcomes. Identify incomplete checks and failed changes explicitly. Update the architecture diagram and service inventory when the deployed topology changes.

This workflow applies while an assistant is working on the homelab. Changes made outside an assistant session require an explicit inspection or a separately configured monitoring system to be discovered.
