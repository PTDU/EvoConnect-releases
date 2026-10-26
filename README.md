# EvoConnect Releases

Public release builds and auto-update feed for EvoConnect. This repo holds only release assets; the source code lives in the private [PTDU/EvoConnect](https://github.com/PTDU/EvoConnect) repo.

> Do not delete releases or edit their assets. Installed apps read `latest.yml` from the latest release.

## Release checklist

Steps 1-3 run in the main EvoConnect project, not in this repo.

1. Bump `version` in `package.json` (it must be higher than the last release), then commit and tag:
   ```
   git add package.json
   git commit -m "Release v1.8.2"
   git tag v1.8.2
   git push origin master --tags
   ```
2. On Windows, set a token with write access to this repo:
   ```
   set GH_TOKEN=<token>
   ```
3. Build and upload a draft release here:
   ```
   yarn buildall
   ```
4. Check the draft has `latest.yml`, `evoconnect-Setup-<version>.exe` and `evoconnect-Setup-<version>.exe.blockmap`.
5. Publish the draft. Drafts and pre-releases are not offered to installed apps.
6. Open `https://github.com/PTDU/EvoConnect-releases/releases.atom` in a private window and confirm it loads.

## Installing

Download `evoconnect-Setup-<version>.exe` from the latest release and run it. Installed apps check this repo on startup and prompt to restart when an update is downloaded.

## Troubleshooting

- Update log on Windows: `%APPDATA%\EvoConnect\logs\main.log`.
- `404` in the log: the repo or release is not public, or the release is still a draft.
- `No updates available`: the installed version is the same as or newer than the latest release.
- Updates are skipped in dev builds (`Skip checkForUpdatesAndNotify because application is not packed`).