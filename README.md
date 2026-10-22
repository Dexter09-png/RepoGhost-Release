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



# RepoGhost

**A Desktop Security Scanner for Detecting Sensitive Data in ZIP Archives**

RepoGhost is a working Windows desktop application designed to help developers identify potentially exposed secrets and sensitive information in ZIP archives before sharing or distributing their projects.

It scans files for patterns associated with API keys, access tokens, passwords, private keys, database connection strings, sensitive filenames, and other potentially risky information. Findings are displayed in a desktop interface with severity levels, file locations, line numbers, and redacted evidence.

RepoGhost is designed to make an initial security review easier without requiring users to manually inspect every file in an archive.

## Overview

- **Application type:** Windows desktop application
- **Interface:** Python Tkinter GUI
- **Scan target:** ZIP archives
- **Primary purpose:** Identify potential secret and sensitive-data exposure
- **Results:** Findings with severity, file path, line number, issue description, and redacted evidence
- **Export:** JSON scan reports
- **Privacy:** Archive scanning is performed locally by the application
- **License:** MIT

## Features

### Secret and Credential Detection

RepoGhost checks archive contents for patterns that may indicate exposed credentials or sensitive configuration data, including:

- API keys and access tokens
- Password-related values
- Private-key markers
- Database connection strings
- Other text patterns associated with potentially sensitive information

Detection is pattern-based. A finding indicates a potential issue that should be reviewed, not necessarily a confirmed vulnerability.

### Sensitive File Detection

RepoGhost identifies filenames that may indicate sensitive content, such as environment configuration files or other files commonly associated with credentials and application configuration.

### Infrastructure and Local Information Checks

The scanner checks for selected patterns that may expose internal information, including local filesystem paths and private or internal IP addresses.

### Desktop Results Interface

Scan results are presented in the application so users can review findings without manually searching through each file. Results include available information such as:

- Severity level
- File containing the finding
- Line number, when available
- Issue description
- Redacted evidence to help identify the relevant content

### JSON Report Export

Users can export scan findings as a JSON report for record-keeping, further review, or integration into their own analysis workflow.

### ZIP Archive Safety Checks

RepoGhost applies limits and validation checks intended to reduce risks when processing ZIP archives:

- Maximum archive size: 100 MB
- Maximum total extracted content: 300 MB
- Maximum number of archive entries: 10,000
- Validation against unsafe archive paths
- Rejection of symbolic links and duplicate entries
- Checks for unusual compression ratios

These safeguards reduce certain archive-processing risks but do not guarantee that every malicious or malformed archive will be detected.

## How RepoGhost Works

1. **Select an archive.** Open RepoGhost and choose the ZIP archive you want to inspect.
2. **Validate the archive.** The application checks the archive against its configured size, entry-count, path, and other safety restrictions.
3. **Scan the contents.** RepoGhost examines eligible files for configured patterns associated with credentials, sensitive filenames, and potentially exposed infrastructure information.
4. **Review the findings.** The application displays detected issues with relevant context, including severity, file location, line number when available, and redacted evidence.
5. **Export the report.** Export the results to JSON if you need to retain or review the findings later.
6. **Fix and rescan.** Investigate genuine findings, remove or secure exposed information, and scan the corrected archive again.

## Windows Application

RepoGhost is an existing desktop application intended to run on Windows.

The application has been packaged as a Windows installer named `RepoGhost-Setup.exe`. However, the installer must be attached to a published GitHub Release before it can be downloaded from this repository.

**Download:** [RepoGhost Releases](https://github.com/Dexter09-png/RepoGhost-Release/releases)

If no release asset is available, the installer has not yet been published for download here.

## Privacy and Data Handling

RepoGhost is designed to scan ZIP archives locally on the user's computer. Its scanning workflow does not require uploading archive contents to a remote scanning service.

Treat scan reports as potentially sensitive because they may contain file paths and information about findings, even when evidence is redacted. Review reports before sharing them.

## Scope and Limitations

RepoGhost is an initial security-review tool, not a replacement for a full security audit, secret-management system, or dedicated static-analysis platform.

- Detection relies on configured patterns and heuristics.
- False positives may occur.
- Some secrets or vulnerabilities may not be detected.
- Results require human review and verification.
- The application scans the contents of the selected ZIP archive; it does not inspect the repository's complete Git history.
- A clean scan does not prove that an archive is free of secrets or security vulnerabilities.

For important projects, use RepoGhost alongside code review, secret scanning, dependency analysis, and appropriate security testing.

## Intended Use

RepoGhost may be useful for developers who want to perform a preliminary check before sharing project archives, submitting code, or distributing source packages.

Always ensure you have permission to scan the files you provide to the application.

## License

This project is distributed under the MIT License. See the [LICENSE](LICENSE) file for the full license text.

## Repository

- **GitHub:** [Dexter09-png/RepoGhost-Release](https://github.com/Dexter09-png/RepoGhost-Release)
- **Releases:** [Download page](https://github.com/Dexter09-png/RepoGhost-Release/releases)

