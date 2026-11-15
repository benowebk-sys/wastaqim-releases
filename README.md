# Wastaqim Windows Release Report

## Release configuration

- Application: Wastaqim 1.1.0
- Electron: 44.7.2
- electron-builder: 26.17.0
- Target: Windows 10/11, x64
- Installer: NSIS assisted Setup.exe, ASAR enabled
- Application ID: `com.dynamicnova.app` (retained for compatibility)
- Executable metadata: Product `Wastaqim`; company `Belal Mohamed`
- Installer options: installation directory selection, desktop shortcut, Start Menu shortcut, and user-data preservation on uninstall

## Measured sizes

Measurements are from the built x64 distribution. MiB means 1,048,576 bytes.

| Measurement | Before optimization | After optimization | Change |
|---|---:|---:|---:|
| Setup.exe | 117,277,427 bytes (111.84 MiB) | 112,454,355 bytes (107.24 MiB) | -4,823,072 bytes (-4.60 MiB; 4.11%) |
| Unpacked/installed application tree | 380,294,531 bytes (362.68 MiB) | 338,779,902 bytes (323.09 MiB) | -41,514,629 bytes (-39.59 MiB; 10.92%) |
| `app.asar` | 44,297,750 bytes (42.24 MiB) | 2,890,743 bytes (2.76 MiB) | -41,407,007 bytes |

The largest remaining contributors are Electron/Chromium runtime files, which are required:

- `Wastaqim.exe`: 245,672,448 bytes (234.29 MiB)
- `dxcompiler.dll`: 25,744,384 bytes (24.55 MiB)
- `LICENSES.chromium.html`: 20,477,229 bytes (19.53 MiB)
- `resources.pak`: 12,436,139 bytes (11.86 MiB)
- `icudtl.dat`: 10,875,024 bytes (10.37 MiB)

## Optimization and package contents

- Bundle inspection found `lucide-static` contributed 37.48 MiB to ASAR, primarily unused font files, the full icon catalog, and preview data. Production now includes only the 19 SVG icons referenced by the application, plus the Lucide license (20 files, 12.05 KiB total).
- Runtime branding images are stored under `assets/` rather than `build/`: electron-builder reserves `buildResources` for installer/build assets and does not include that directory in ASAR. The packaged PNG and ICO are 73,384 and 119,834 bytes; the settings page now resolves its logo from the ASAR.
- `lucide-static` remains a development dependency for excluded promo tooling; it is not present in the production ASAR.
- The packaged stylesheets contain 19 SVG references; all 19 resolve to files in the ASAR.
- `promo/`, `site/`, build tooling, tests, documentation, and source maps are excluded by the existing packaging rules. No large promo images or duplicate site assets are in the installed application.
- Automatic application updates are disabled in this build: the update setting, IPC/preload hooks, and update toast are no longer active; `electron-updater` and the GitHub publish configuration were removed. The updater source files remain in the development project but are excluded from ASAR. Existing installations are unaffected until this installer replaces them.
- The final package contains no `app-update.yml` or `resources/elevate.exe`; the installer no longer packs the updater elevation helper.
- The only production dependency is `node-ical` 0.27.3 and its runtime dependencies. The production dependency audit reported zero known vulnerabilities.
- No native Node.js modules were found in the production dependency tree. `helper/nova-helper.exe` is correctly unpacked from ASAR because the application launches it as a separate process.
- NSIS uses electron-builder's default `normal` compression. A measured `maximum`-compression build of the pre-icon-correction package saved only 56 bytes from the 112,521,939-byte installer, so the slower setting was not retained.

## Security and Windows integration

- ASAR packages application files; it is not encryption. Its JavaScript contents remain recoverable.
- Renderer windows use context isolation and expose application operations through preload bridges; Node integration is disabled in the main and mini-player windows. The settings window also explicitly enables Electron sandboxing. Main and mini-player windows rely on Electron 44's default sandbox setting.
- The island, settings, and mini-player pages have Content Security Policy metadata. External navigation is denied in-app; supported HTTPS links open through the system browser.
- No custom Electron permission-grant handler was found in the inspected main-process files.
- The helper is included in the package and was observed running during installed-app validation. It targets the .NET Framework 4 family, which is normally included with Windows 10/11; a clean-machine test was not available.
- The installer and application are unsigned because no signing certificate was configured. Windows SmartScreen may show a warning. A certificate is required for trusted publisher signing.

## Validation performed

- `npm.cmd run dist` completed successfully and generated `release/Wastaqim-Setup.exe`.
- Automated package checks confirmed x64 output, version 1.1.0 metadata, expected application assets, and no updater references, dependency, update metadata, or elevation helper.
- The changed JavaScript passed `node --check`; `npm.cmd audit --omit=dev` reported zero vulnerabilities.
- This no-update rebuild was not installed or launched during this pass. An earlier package was installed and uninstalled successfully; a separate clean Windows machine/Sandbox was not available.
- The complete feature set was not manually retested in this release pass.

## Deliverable

- Installer: `release/Wastaqim-Setup.exe`
- This report is retained in `release/` and is not included in the application package.
