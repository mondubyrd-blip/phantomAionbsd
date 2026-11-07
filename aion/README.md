# AION BSD Edition

This directory is the AION-owned distribution overlay for the inherited GhostBSD/FreeBSD source tree.

It is intentionally separate from upstream source directories. The inherited kernel, userland, release engineering files, and project history remain unchanged.

## Foundation

- Source repository: `ghostbsd/ghostbsd-src`
- Local fork: `mondubyrd-blip/phantomAionbsd`
- Baseline branch: `stable/15`
- Initial target: amd64 development image, subject to build-host and hardware validation
- Image assembly: separate GhostBSD live-media builder, after compatibility validation

## Architecture

AION is initially implemented above the kernel as a set of independently packaged and supervised system services:

- **Identity Core** — identity, authentication and authorization interfaces.
- **Cognitive Core** — local inference/runtime integration and task execution interfaces.
- **Memory Core** — persistent state, indexing, access control and backup interfaces.
- **Orchestration Layer** — service lifecycle, dependency ordering, health reporting and policy enforcement.

These names describe integration boundaries, not completed implementations. Each component requires a documented API, threat model, package dependencies and service lifecycle before production code is added.

## Design constraints

1. Preserve upstream FreeBSD and GhostBSD source history.
2. Keep AION changes under `aion/` or in narrowly scoped, documented integration points.
3. Prefer userland services and existing kernel interfaces over kernel modifications.
4. Keep runtime operation local/offline by default; network access must be explicit and configurable.
5. Separate live-session convenience from installed-system security policy.
6. Record source revisions, package inputs and build outputs for every candidate image.
7. Do not claim a bootable ISO or tested feature until a reproducible build and validation record exist.

## Next engineering gates

1. Compare the fork with its upstream parent and classify inherited/local deltas.
2. Verify the live-media builder against the FreeBSD 15 source and package ABI.
3. Select a supported desktop and installer path.
4. Define package manifests and first-boot configuration.
5. Implement the first AION service as an isolated package.
6. Build and test in a disposable FreeBSD build environment.
