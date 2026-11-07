# AION BSD Edition — Foundation Plan

Status: Architecture and integration baseline
Source foundation: GhostBSD Core Operating System source
Upstream fork: https://github.com/ghostbsd/ghostbsd-src
Local repository: https://github.com/mondubyrd-blip/phantomAionbsd
Base branch: stable/15

## Preservation rules

- Keep the inherited GhostBSD/FreeBSD source history intact.
- Do not rewrite or replace upstream source files as part of the initial integration.
- Keep AION-specific work isolated on this branch until reviewed and build-tested.
- Treat the uploaded `ghostbsd-build-master.zip` as a separate live-image builder; it is not the operating-system source tree.
- Do not run destructive build scripts against a developer workstation or an existing ZFS pool.

## Architecture boundary

AION BSD Edition is a distribution and system-services layer built on the GhostBSD/FreeBSD foundation. The initial implementation does not require a private kernel fork.

Initial layers:

1. **FreeBSD/GhostBSD base:** kernel, boot loader, userland, drivers, networking, storage and system interfaces.
2. **AION system integration:** service definitions, package manifests, configuration defaults, identity integration and first-boot setup.
3. **AION core services:** Identity Core, Cognitive Core, Memory Core and Orchestration Layer, integrated as independently packaged services with explicit dependencies and service boundaries.
4. **Distribution assembly:** use the separate GhostBSD live-media builder as the initial ISO-generation path, after validating its compatibility with this source branch and package repositories.

## Initial engineering decisions

- Retain the inherited `stable/15` source branch as the baseline.
- Keep kernel changes out of scope until a demonstrated AION requirement cannot be met through userland services, kernel configuration, device interfaces or existing FreeBSD facilities.
- Keep AION package and configuration overlays separate from inherited source wherever practical.
- Require reproducible build inputs, recorded source revisions and explicit package versions for release candidates.
- Separate live-session convenience settings from installed-system security defaults.

## Work sequence

### A. Source and build compatibility
- [ ] Record the fork parent and baseline commit.
- [ ] Inventory GhostBSD-specific source changes and local commits relative to `ghostbsd/ghostbsd-src`.
- [ ] Inspect `release/` targets and supported build environments.
- [ ] Validate the uploaded GhostBSD builder against the source branch, package ABI and repository configuration.
- [ ] Document host requirements and non-destructive build isolation.

### B. AION distribution overlay
- [ ] Define AION release identity, versioning and architecture support.
- [ ] Define package manifests for base, desktop, drivers and AION services.
- [ ] Define first-boot and installation configuration.
- [ ] Define service enablement, logging, update and rollback behavior.
- [ ] Define security defaults independently of live-media defaults.

### C. AION service integration
- [ ] Specify Identity Core interfaces and authentication boundaries.
- [ ] Specify Cognitive Core runtime interfaces and offline operation.
- [ ] Specify Memory Core storage format, access controls and backup boundaries.
- [ ] Specify Orchestration Layer service supervision and dependency model.
- [ ] Add service packages only after their interfaces and runtime dependencies are documented.

### D. Build and validation
- [ ] Produce a non-production image in an isolated build environment.
- [ ] Validate boot, installer/live session, storage, networking, graphics and package management.
- [ ] Validate offline behavior and service startup.
- [ ] Record test results and known limitations before any release claim.

## Evidence and change discipline

This document records the initial AION integration plan only. It does not claim that a kernel, ISO, installer, service or build has been produced or tested. Preserve original source artifacts and use separate commits for each AION-specific change.
