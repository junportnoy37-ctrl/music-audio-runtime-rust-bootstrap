# music-audio-runtime-rust-bootstrap

Public bootstrap infrastructure for reproducing the Rust dependency set used by the private `music-audio-runtime` project.

This repository intentionally contains **no private project source code**. Its only purpose is to resolve and vendor the external Rust dependencies needed for offline development and verification.

## Policy

- Standard public GitHub-hosted runners only.
- No Docker.
- No private repository checkout or private source transfer.
- Dependency versions are pinned by the committed `Cargo.lock` produced on Rust 1.88.
- The vendor bundle is published as a GitHub Release asset so it can be reused without consuming private Actions minutes or requiring crates.io access from the development sandbox.
- This repository is bootstrap infrastructure, not a runtime or product dependency.

## Regenerating the bundle

Changes to `Cargo.toml` or the vendor workflow regenerate the dependency lock and publish a release asset from a standard `ubuntu-latest` runner.

The generated archive contains `vendor/`, `Cargo.lock`, and a Cargo source-replacement config suitable for offline use.
