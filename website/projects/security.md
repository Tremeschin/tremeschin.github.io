---
title: Security
icon: material/security
description: Details of security checks I take on my Open Source projects, package registries
  publishing, dependencies used, and how to report issues directly to me, for user integrity.
tags:
- About
- Security
---

-> As Open Source developers, user integrity and security is about being professional.

Supply chain attacks, social engineering, copycats, and others are a constant threat to users and ourselves. This page talks about the measures I take to mitigate risks, and how to report them.

## Forges

### Commits

All commits are signed with my main [SSH Key](https://api.github.com/users/Tremeschin/keys) created in Q3 2024, well-kept and with a strong password, alongside my GitHub account having [Vigilant Mode](https://docs.github.com/en/authentication/managing-commit-signature-verification/displaying-verification-statuses-for-all-of-your-commits) enabled.

### Releases

All projects uses native release channels mechanisms for reproducibility and least privilege:

- :simple-python: **Python**: Uses PyPI [Trusted Publishers](https://docs.pypi.org/trusted-publishers/) in GitHub Actions workflows. Account has 2FA enabled, ephemeral 7 days tokens are used for creating new packages (once). Final uploads uses the [`pypi-publish`](https://docs.pypi.org/trusted-publishers/using-a-publisher/#github-actions) action for provenance attestations.
- :simple-rust: **Rust**: Uses crates.io [Trusted Publishing](https://crates.io/docs/trusted-publishing) in GitHub Actions workflows. Account login via GitHub, also with 2FA enabled, and ephemeral tokens for new crates (once).

Repositories have [Immutable Releases](https://github.blog/changelog/2025-10-28-immutable-releases-are-now-generally-available/) enabled, so bound tags and assets cannot be replaced or renamed after creation, only deleted - community packages are welcome to source from it.

## Code

### Dependencies

=== ":simple-python: Python"

    For technical reasons, Python projects does not pin dependencies to `==` versions as it causes many problems with dependency resolution for users. Otherwise, I'm always looking to simplify, inline or write my own dependencies over adding new ones.

    As for version resolution, risks are inevitable for compatibility:

    - **Major**: Packages like `torch, numpy, attrs, pillow` are specified without a version, most likely resolved to the current latest one. High stakes, but people behind it would take quick action.
    - **Minor**: Well-known community, but small team or solo packages, are specified with `~=` mark up to the minor - eg. `~=1.2` accepts any `>=1.2.0,<2` version, mostly for semver.
    - **Suspicious**: Unmaintained, spicy history, human spaghetti (language models assisted), or runtime installed are pinned to exact versions.
    - **Self**: My own packages might accept any version to reduce micro management.
    - **Vibecoded**: Completely dismissed.

## Social

### Copycats

Virtually all projects suffers from copycats in this era of legal plagiarism machines.

:hash: Todo (...)
