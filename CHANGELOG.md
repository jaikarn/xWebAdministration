# Change log for xWebAdministration

The format is based on and uses the types of changes according to [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

For older change log history see the [historic changelog](HISTORIC_CHANGELOG.md).

## [Unreleased]

### Added

- xWebAdminstration
  - Integration tests are running on more Microsoft-hosted agents to
    test all possible operating systems ([issue #550](https://github.com/PowerShell/xWebAdministration/issues/550)).
  - Fix a few lingering bugs in CICD ([issue #567](https://github.com/PowerShell/xWebAdministration/issues/567))
  - Remove an image from testing that MS will be deprecating soon ([issue #565](https://github.com/PowerShell/xWebAdministration/issues/567))

### Changed

- xWebAdminstration
  - Azure Pipelines will no longer trigger on changes to just the CHANGELOG.md
    (when merging to master).
  - The deploy step is no longer run if the Azure DevOps organization URL
    does not contain 'dsccommunity'.
  - Changed the VS Code project settings to trim trailing whitespace for
    markdown files too.
  - Ensure that Test-TargetResourse in xWebSite tests all properties before
    returning true or false, and that it uses a consistent style. ([issue #221](https://github.com/PowerShell/xWebAdministration/issues/550))   
- xIisMimeTypeMapping
  - Update misleading localization strings

### Fixed

- WebApplicationHandler
  - Integration test should no longer fail intermittent ([issue #558](https://github.com/PowerShell/xWebAdministration/issues/558)).

## [3.1.1] - 2020-01-10

### Changed

- xWebAdministration
  - Set `testRunTitle` for PublishTestResults task so that a helpful name is
    displayed in Azure DevOps for each test file artifact.
  - Update Visual Studio Code workspace settings for the repository.
  - Set a display name on all the jobs and tasks in the CI pipeline.

### Fixed

- xWebAdministration
  - Update GitVersion.yml with the correct regular expression.
  - Fix import statement in all tests, making sure it throws if module
    DscResource.Test cannot be imported.
- xWebsite
  - Fixed HTTPS binding issue causing failure when CertificateSubject matches
    multiple certificates.
  - Fix an issue where changes to LogFlags would fail to apply.

## [3.1.0] - 2019-12-30

### Added

- xWebAdministration
  - Added continuous delivery with a new CI pipeline
    ([issue #547](https://github.com/PowerShell/xWebAdministration/issues/547)).
  - Added CONTRIBUTION.md.

### Changed

- xWebAdministration.Common
  - Added new helper function `Get-WebConfigurationPropertyValue` to
    help return a value of a `WebConfigurationProperty`. *This helper*
    *function is unable to be unit tested because it is using a type*
    *that cannot be mocked.*
- xWebAppPoolDefaults
  - Changed to use the new helper function `Get-WebConfigurationPropertyValue`
    so that the resource can be properly unit tested.
- xWebConfigProperty
  - Changed to use the new helper function `Get-WebConfigurationPropertyValue`
    so that the resource can be properly unit tested.

### Fixed

- WebApplicationHandler
  - Fix Test-TargetResource to compare only properties that are specified
    in the configuration ([issue #544](https://github.com/PowerShell/xWebAdministration/issues/544)).
- xWebConfigProperty
  - In some cases a verbose message was not outputted with any text, now
    all verbose messages are correctly shown.
- xWebSite
  - In some cases a verbose message was not outputted with any text, now
    all verbose messages are correctly shown.

### Removed

- CommonTestHelper
  - Removed unused functions `Get-InvalidArgumentRecord` and
    `Get-InvalidOperationRecord`.
