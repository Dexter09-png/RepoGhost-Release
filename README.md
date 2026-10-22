# RepoGhost

<p align="center">
  <img src="./repoghost_ghost_shield.ico" width="96" alt="RepoGhost shield">
</p>

**A local Windows desktop app for reviewing repository archives for potential security and privacy exposures.**

RepoGhost scans a selected ZIP archive and presents possible findings in a desktop interface. Findings are pattern matches to review—not proof that a file is vulnerable or that a clean scan is secure.

## What it checks

- Secret-like values, including API keys, passwords, database connection strings, and private-key markers
- Filenames commonly associated with environment files, backups, logs, and private keys
- Local filesystem paths and private or loopback IP addresses
- Severity-labeled findings with redacted match evidence

The desktop app can export its findings as a JSON report. It scans the selected archive's current contents; the desktop interface does not scan Git history.

## Windows download

There is no installer in this staging preview. Once a Windows installer has been reviewed and a release is approved, downloads will be published on the [GitHub Releases page](https://github.com/Dexter09-png/RepoGhost-Release/releases).

The app is designed to scan repository ZIP files on the local machine. The current interface accepts ZIP files up to 100 MB, with a maximum of 300 MB of extracted contents and 10,000 archive entries. Unsafe paths, symbolic links, duplicate paths, and unusually high compression ratios are rejected.

## Limitations

RepoGhost uses a set of detection patterns and can miss exposures or produce false positives. Review findings yourself and use additional security checks where appropriate. A scan with no findings is not a guarantee that a repository is safe to publish.

## Source and license

This is a distribution-only repository; it does not contain the application's Python source or development files. RepoGhost is provided under the [MIT License](./LICENSE).
