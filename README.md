# LocalSend for High Sierra

An unofficial backport of [LocalSend](https://github.com/localsend/localsend) for macOS High Sierra 10.13.6 on Intel x86_64 Macs.

This repository exists for one target only: keeping current LocalSend releases usable on High Sierra. It does not build Android, iOS, Windows, Linux, Apple Silicon, or newer-macOS packages.

## Current proven baseline

The first working High Sierra baseline is preserved at commit `964545bdd3b47838c5b300a86d9f66b5f8291f13` and branch `high-sierra-first-working`.

That build uses LocalSend `1.18.2+64`, Flutter `3.41.9`, Dart `3.11.x`, and Rust `1.97.1`. The source snapshot is based on upstream `main` commit `6279d3e30d1d1290caee3b81549f8128a8b01d9f`, which is newer than the official `v1.18.2` release tree. On a real macOS High Sierra 10.13.6 Intel machine it has been verified to start, discover peers, and transfer files successfully.

Because that baseline is a post-`v1.18.2` upstream snapshot rather than the exact `v1.18.2` release tree, the automation will not publish it automatically as an official-version-matched GitHub Release.

## Automatic upstream release backport

`.github/workflows/sync-upstream-release.yml` checks the official LocalSend releases twice per hour. When it sees a new stable release, it:

1. fetches the exact official release tag and commit;
2. replaces the application source with that release tree while preserving this repository's High Sierra-only workflows and documentation;
3. records the upstream tag and commit;
4. dispatches the High Sierra backport workflow;
5. publishes `vX.Y.Z-high-sierra` only if the complete fail-closed compatibility build succeeds.

The build does not lower metadata and hope for the best. It keeps the existing source, ABI, Objective-C runtime, Swift overlay, Metal, Dart VM, Native Asset, code-signing, and final-bundle validations. If a new Flutter engine, plugin, or LocalSend release invalidates one of the assumptions that was verified for the current baseline, CI fails and no GitHub Release is published. That failure is the signal to add the next precise backport.

## Builds

The only application build workflow is `.github/workflows/macos-high-sierra.yml`. Release assets are ZIP archives for macOS 10.13.6, Intel x86_64, accompanied by SHA-256 checksums.

This project is not affiliated with or endorsed by the LocalSend project. LocalSend remains licensed under the upstream Apache License 2.0; the upstream project and its contributors retain their respective copyrights.
