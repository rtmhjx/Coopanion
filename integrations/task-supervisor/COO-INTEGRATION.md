# Optional Task Supervisor World for Coopanion

This directory contains the complete source and built runtime of **cortico-world-task-supervisor 0.1.0-preview.1**, an optional World API 6 extension. It brings DSH conversation control, scoped Codex monitoring, scoped DSH external-memory tools, an important-event queue, and an owner-only QQ task channel into **one World** with a setup page.

The integration is outside the application's workspaces: the [pinned workspace list](https://github.com/YuZhou0311/Coopanion/blob/ff30069db35cd96ce57be6f034fc8b5057f24075/pnpm-workspace.yaml) contains only `packages/*`. The integrations directory is outside that glob. This contribution does not change Coopanion's application code, Cortico submodule, root dependencies or lockfile, packaged application, default Worlds, or startup behavior. Installing this source directory is an explicit user choice.

## Provenance

- Canonical project: [rtmhjx/cortico-world-task-supervisor](https://github.com/rtmhjx/cortico-world-task-supervisor).
- Reviewed source archive: [immutable publication commit](https://github.com/rtmhjx/cortico-world-task-supervisor/blob/15007151a9aad36bcc5da67c154be1367420366c/cortico-world-task-supervisor-0.1.0-preview.1-source.zip).
- Source ZIP SHA256: **3bb54b6543a6fe23bb46790851a5dfd8894f2fb9b62481808ffe2bf141b91395**.
- Source package: exactly 148 files, preserved under this directory; this guide is the only additional integration file.
- Fork contribution base: YuZhou0311/Coopanion main at **ff30069db35cd96ce57be6f034fc8b5057f24075** (Coopanion 0.2.4).
- Cortico submodule at that base: **087289dfcdf262a771c573d16dbaf2392ce6764b**, version **0.2.3**, World API **6**. The submodule is preserved.
- Licensing and upstream component attribution remain in [LICENSE](LICENSE), [NOTICE](NOTICE), [THIRD-PARTY-LICENSES.txt](THIRD-PARTY-LICENSES.txt), and [SOURCES.md](SOURCES.md).

## Install through the existing extension UI

Use a Node 24 environment for building the extension and running its separate gateway installer. From this optional integration directory, explicitly run:

    npm install
    npm run build

In Coopanion, open **Advanced mode → Extensions** and use the existing **local-directory installer** to select this directory. Restart the process when requested, enable **Task Supervisor** in **World Overview**, and open its page. Once the preview package is available from the npm registry used by your host, the same Extensions page can install the package by name: **cortico-world-task-supervisor**.

This source contribution does not publish an npm package or make an unpublished package appear in the catalog. It does not install or enable itself. The three older bridge Worlds are bundled as implementation modules and must not be installed separately for this integration.

## Configure in the World

1. **Connect services:** enter your own QQ number, select a QQ transport, and supply its loopback endpoint, bot account and credential through the setup page. Native SnowLuma mode uses the included native add-on helper; it is not an API guaranteed by stock SnowLuma. OneBot v11 is an optional transport. Advanced trusted-metadata mode reuses an already compatible QQ World instead of providing a separate raw channel.
2. **Select scope:** choose only the DSH/Codex workspaces and conversation directories you want to expose, then add private directories to the exclusion list. Optional project-file reads, raw mirrors and external-memory writes have separate controls.
3. **Check connections and apply:** the setup page performs explicit connection checks and shows component-specific readiness. Save and restart when requested. Avoid having two QQ Worlds own replies for the same private conversation.
4. **Install the external gateway if needed:** the setup page can produce a private local installation kit. Download/run its launcher once, select the DSH home/profile, and follow the backup-and-install guide. Generated files are explicitly **not installed** until the separate DSH host is configured, restarted as required, and its authenticated health check succeeds.

Raw QQ mode supplies the configured owner's task conversation and fixed-owner replies without requiring another QQ World. It still needs the selected underlying QQ service. DSH task control needs a separate running DSH host with the conversation gateway; installing a Coo World does not replace that host. Codex-only read monitoring can run without pretending a DSH workspace exists, while native task control remains unavailable until its required gateway/application is ready.

Credentials remain host-managed deployment data and are never stored in this source tree or returned by the setup API. Keep services on loopback. Content read from the selected conversations can reach the configured model service; scope checks are not an operating-system sandbox for commands executed by a coding agent. See [SECURITY.md](SECURITY.md).

## The reporting switch

Remote reporting and model task-access tools start **OFF**. Only a genuine private message from the configured owner whose original message begins with **#@**, or consists of **#@**, toggles the switch. Nicknames, quoted/forwarded messages, transcriptions, and later mentions of the marker do not supply this command. The web panel shows status; it does not impersonate the owner or toggle access.

When turned ON, queued important events are injected and new completed-task or approval/problem events can be delivered. Ordinary progress steps do not become a stream of notifications. In raw mode, ordinary owner task chat is ignored while OFF. Turning OFF closes the task-access tools and prevents further task-content delivery through this World.

The marker is not permission to submit a coding task. Draft/confirm control requires a separate fresh owner confirmation. Changing the owner or permitted scope closes the old access and establishes a new OFF queue; already submitted native operations continue under their original coding application's permissions.

## What was actually validated

| Environment | Observed evidence | Limit |
| --- | --- | --- |
| This fork's Cortico 0.2.3 / API 6 at 087289df | Real isolated World assembly; five mount checks; secret storage, live/disk persistence, restart and setup invocation contracts; extension check passed. | Synthetic isolated state, without starting external services. |
| Official Coopanion 0.2.8 settings UI with Cortico 0.2.6 / API 6 | Real settings frontend displaying the real World setup page, backed by an isolated running Cortico WebApp. | Browser/settings integration, not full Electron application startup. |
| Sealed package core baseline | 282 tests: 281 passed and one Windows file-symlink permission case skipped; typecheck covered 81 source/fixture files; byte-exact rebuild verified. | Local fixture and build evidence. |
| Final UI-only revision | All nine UI tests passed, including the two new guidance cases. Core/bundle bytes were unchanged. | The resulting 284-test inventory was not rerun as one full suite. |

**Full Electron startup, real QQ delivery/control, production DSH execution, and prolonged stability were not established by these checks.** The preview label remains intentional. Passing SDK checks is not evidence that a user's live QQ or coding-agent deployment is configured.

## Updating this optional integration

Use the canonical project for future package development. Review a new sealed version, verify its archive checksum and component licenses, replace the 148-file package tree intentionally, and update this guide's version/base/validation record in a dedicated optional-integration PR. Do not edit the Cortico submodule or application defaults as part of a package refresh.
