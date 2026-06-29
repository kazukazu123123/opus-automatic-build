# opus-automatic-build

[![Build](https://github.com/kazukazu123123/opus-automatic-build/actions/workflows/build-opus.yml/badge.svg)](https://github.com/kazukazu123123/opus-automatic-build/actions/workflows/build-opus.yml)
[![Latest Release](https://img.shields.io/github/v/release/kazukazu123123/opus-automatic-build)](https://github.com/kazukazu123123/opus-automatic-build/releases/latest)
[![Downloads](https://img.shields.io/github/downloads/kazukazu123123/opus-automatic-build/total)](https://github.com/kazukazu123123/opus-automatic-build/releases)

Automatically builds and publishes Windows DLL binaries (x86 / x64) for
[Opus](https://opus-codec.org/), cross-compiled on Ubuntu using MinGW-w64.

## Downloads

Get the latest binaries from [Releases](https://github.com/kazukazu123123/opus-automatic-build/releases/latest).

- `opus-windows-x86_64-<version>.zip` — 64-bit
- `opus-windows-i686-<version>.zip` — 32-bit

Each ZIP contains the DLL (`bin/`), the headers (`include/`), and import
libraries in `lib_x64/` or `lib_x86/`:

- `libopus.dll.a` — MinGW / GCC
- `libopus.lib` — MSVC (`link.exe`)

## How auto-updates work

A GitHub Actions workflow ([`build-opus.yml`](.github/workflows/build-opus.yml)) does the following:

- **Weekly** (Mondays at 00:00 UTC) it checks the `xiph/opus` tags **via the GitHub API**.
- If a newer stable version is found and hasn't been released yet, it builds and publishes it.
- Versions that are already released are skipped.
