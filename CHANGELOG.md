# LeGo CertHub Changelog

## [v0.7.0] - 2023-04-29

Major updates were made to the frontend in this release, including removing
Create React App and replacing it with Vite.

### Added
Backend
- Added tests for validation package.

Frontend
- Defined props with prop-types.
- Added sublabel on text array component.
- Added placeholder message on empty InputSelect fields.

### Changed
Backend
- Log Cloudflare domains at Info level.
- Updated email validation regex and method. Domain piece uses domain validator
  and email username is separately validated.
- DNS Manual Script name updated.

Frontend
- Port from Create React App to Vite (CRA is deprecated).
- Moved constants to a separate file.
- Updated paths for navigation when using cancel and submit buttons. Next
  destination is now explicit rather than relative.
- Login form clears if backend rejects the login.

### Fixed
Frontend
- Did a ton of linting.
- Fixed issue where Axios errors could cause a loop on logout and also cleaned
  up Axios error handling in general.
- Fixed issue where Rollover Account Key would still show loading message even
  after loaded.

### Removed
Frontend
- Removed dummy forms.
- Removed duplicative FormError component and replaced with common ApiError
  component.


## [v0.6.11] - 2023-03-12

### Added
- Added debug log message when dns checker is configured to skip the check.

### Changed
- Update dependency versions: x/text, x/net, x/time, x/crypto, & go-retryablehttp
- Abort dns checker sleep when configured to skip and shutdown signal is received.

### Fixed
- Patched several CVEs by upgrading dependencies, including CVE-2022-32149,
  CVE-2022-41721, CVE-2022-27664, and CVE-2022-41723.
- Add missing error check in Cloudflare challenge provider.

### Removed
N/A


## [v0.6.10] - 2023-03-08

### Added
N/A

### Changed
- Update Go version and move Node and Go versions to global variables in build script.
- Rename DNS example scripts to avoid accidental overwrite.
- Minor code clarification in CORS.

### Fixed
N/A

### Removed
N/A


## [v0.6.9] - 2023-01-29

### Added
- Config option to disable dns checker module. Instead, specify a time to sleep and
  then assume dns propagated successfully.
- Manual DNS script challenge validation module. Calls external scripts to create
  and remove DNS records. This allows support for any DNS provider. Add example scripts
  to show variables available to scripts.
- Add some more config comments on dns checker config.

### Changed
- Better logging for config parsing.
- Better authentication logging for audit trail.
- Better download logging for audit trail.
- Exit on improperly formatted config.yaml

### Fixed
- Fix install and upgrade linux scripts to work when called from any path.
- Fix logic auto order logic that could sometimes result in the job being called
  twice on the same day.
- Include subject in the CSR DNSNames field (not just Alt Names). LE accepted the
  previous method but Pebble returns an error without this.
- Frontend: Fix missing Staging Flag in All Certificates.
- Frontend: Fix wrong information in confirm delete certificate Dialog.

### Removed
N/A
