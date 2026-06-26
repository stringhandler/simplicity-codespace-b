# Devcontainer

This devcontainer builds the Simplicity workshop toolchain:

- **simc** (SimplicityHL compiler) — built from source
- **hal-simplicity** — built from source
- **smplx** / **simplexup**
- **simplicityhl-lsp**
- **elements-cli** and **elementsd** (Elements Core)

## Architecture note

Most tools are compiled from source and are architecture-agnostic. However,
**Elements Core (`elements-cli` / `elementsd`) is installed from a prebuilt
`x86_64-linux-gnu` binary**. The container is therefore expected to run on an
**x86_64 host** (e.g. GitHub Codespaces).

On an ARM64 host (such as Apple Silicon) the image will build, but the Elements
binaries will not execute (`exec format error`). If you need ARM support, swap
the download in the `Dockerfile` for the matching `aarch64-linux-gnu` release
asset, or build Elements from source.

## Versions

The Elements version is pinned via the `ELEMENTS_VERSION` build arg in
`devcontainer.json` (and defaulted in the `Dockerfile`). Update both if you
bump it.
