# Optional Task Supervisor World for Coopanion

This directory contains the complete source and built runtime of **cortico-world-task-supervisor 0.1.0-preview.2**, an optional World API 6 extension. It combines scoped DSH/Codex task monitoring, approved conversation control, DSH external-memory tools, an important-event queue and the owner's QQ task channel in one World.

Its setup page, in-World installation guidance and human-facing World metadata support all eleven host languages: Simplified Chinese, Traditional Chinese, English, Japanese, Korean, French, German, Latin American Spanish, Brazilian Portuguese, Italian and Russian. The separately run DSH installer retains English terminal prompts. Tool/model instructions remain English, and local paths, commands, IDs and source conversation content retain their original values.

The [pinned workspace list](https://github.com/YuZhou0311/Coopanion/blob/ff30069db35cd96ce57be6f034fc8b5057f24075/pnpm-workspace.yaml) contains only packages/*. This optional integrations directory is outside that workspace glob. The contribution preserves the application source, Cortico submodule, root dependencies/lockfile, default Worlds and startup behavior.

## Provenance

- Canonical project: [rtmhjx/cortico-world-task-supervisor](https://github.com/rtmhjx/cortico-world-task-supervisor).
- Reviewed preview.2 archive: [immutable publication commit](https://github.com/rtmhjx/cortico-world-task-supervisor/blob/85492b5a9f4d388da55372fd017ea5deae40876b/cortico-world-task-supervisor-0.1.0-preview.2-source.zip).
- Source ZIP SHA256: **a3da12dc299fc222ce8b76774928a6bfc58867af2e2d50944182c0e1fe74585a**.
- Complete package tree: **150** files; this integration guide is one additional file.
- Original host base: **ff30069db35cd96ce57be6f034fc8b5057f24075**, Coopanion 0.2.4.
- Previous contribution: **b1bfbcea347472312dcd6a50e6dc29afa1adaf33**. The refresh descends directly from it; temporary workflows on the fork main do not enter the PR.
- Pinned Cortico: **087289dfcdf262a771c573d16dbaf2392ce6764b**, version 0.2.3 / API 6, unchanged.
- Package licensing and provenance: [LICENSE](LICENSE), [NOTICE](NOTICE), [THIRD-PARTY-LICENSES.txt](THIRD-PARTY-LICENSES.txt) and [SOURCES.md](SOURCES.md).

## Install and configure

Use Node 24 for the extension build and separate gateway installer. Build this optional package directory explicitly:

    npm install
    npm run build

Open Coopanion **Advanced mode → Extensions** and use its existing local-directory installer to select this directory. Restart when requested, enable **Task Supervisor** in **World Overview**, and open its setup page. After publication to the npm registry your host uses, the same Extensions page can install **cortico-world-task-supervisor** by package name. Copying this source directory does not publish, install or enable it.

The setup page lets you select the owner QQ, underlying loopback QQ service, permitted DSH/Codex workspaces and conversation directories, exclusions and individual optional read/write functions. Credentials remain host-managed deployment data. Do not store credentials in the repository. Check each configured connection and follow the page's save/restart guidance.

Raw transport provides the owner task conversation and fixed-owner replies without requiring another QQ World. Native SnowLuma mode requires the included native add-on helper; it is not a stock SnowLuma API. OneBot v11 is an optional transport. Advanced trusted-metadata mode instead reuses a compatible QQ World. Avoid two reply owners for the same private conversation.

DSH control requires a separate running DSH host with the conversation gateway. The setup page generates a private local installation kit and launcher; generating it is not installation. Run it locally, select the DSH home/profile, confirm the installation, restart DSH as required and check authenticated health. Codex-only read monitoring does not require a fictitious DSH workspace, but native control remains unavailable until its required gateway/application is ready.

## Reporting and authorization

Reporting and model task-access tools default **OFF**. Only the configured owner's genuine private message beginning with **#@**, or consisting of that marker, toggles access. Nicknames, quotes, forwards, transcriptions and later mentions of the marker do not provide a switch command. The setup panel displays status rather than toggling access.

ON injects queued important events and allows completion/approval/problem reports. Ordinary progress does not become a notification stream. Raw-mode ordinary owner chat is ignored while OFF, and task-content reads/delivery through this World remain closed. The switch is not task confirmation: submission still needs a separate fresh owner confirmation.

Changing owner or permitted scope establishes a new OFF queue and closes the previous access. Already submitted native operations continue in their coding application. Scoped reads are not an OS sandbox for submitted commands, and selected conversation content can reach the configured model service. See [SECURITY.md](SECURITY.md).

## Validation evidence

| Check | Observed evidence | Boundary |
| --- | --- | --- |
| Preview.2 complete extension suite | **298 tests: 297 passed, zero failed, one skipped**. Includes all 22 UI tests, a real World metadata check across all eleven language strings and seven DSH prepared-session cases. | The skip is unavailable Windows file-symlink permission; DSH persistence is synthetic/in-memory. |
| Two actual SDK source typechecks | Both Cortico 0.2.6 and the fork's 0.2.3 passed, each covering 82 source/fixture seeds. | Typechecking is distinct from execution and live deployment. |
| Two actual SDK isolated integration probes and upstream extension-check | Real World assembly, synthetic secret/persistence/restart contracts, string-language metadata, five dry-mount checks and the upstream extension checker passed for both SDKs. | The checker used its actual SDK's public builtin dependency graph; no real Minecraft/QQ/DSH service was started. |
| Target-fork host plus sealed preview.2 optional integration | All five requested commands passed: test 285 passed/one filesystem-case skip, test:worlds 158 passed, and typecheck/typecheck:web/typecheck:worlds exit 0. | Isolated working tree on previous PR head b1bfbcea, whose original host base is ff30069d; this is not a claim about the final public refresh commit. Host test configurations exclude this external integration package. |
| Host setup frontend | Official Coopanion 0.2.8 settings frontend displayed the World against an isolated Cortico 0.2.6 WebApp. | Browser/settings integration, not full Electron startup. |

Host checks used Node 24 on Windows, synthetic profile/data/temp directories, the unchanged frozen host lock and the exact locked Electron 44.4.4 only as Node for a loopback fixture. They are not the upstream Node 22 cross-platform CI matrix. Preview.2's own suite and SDK checks are separate from those host checks.

Validation records retain two earlier failures: the previous-head test initially lacked its documented pet-panel build prerequisite, and the preview.2 host's concurrent first run timed out while checking a nonexistent extension and hit a Windows cleanup EPERM. Only the isolated pet bundle prerequisite was built. The unchanged complete main suite then passed when rerun separately with the same test timeout and selection; host/vendor source was not patched.

**Full Electron application startup, real QQ delivery/control, production DSH execution and prolonged stability remain unverified.** Keep this preview optional until those deployment-specific acceptance steps are completed.

## Maintenance

Develop future versions in the canonical project. Review each sealed source archive and checksum, preserve its complete tree and licenses, then refresh this optional integration and its guide in a dedicated PR. Do not include submodule upgrades, host dependency changes or default startup changes in a package refresh.
