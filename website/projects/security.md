---
title: Security
icon: material/security
tags:
- About
- Security
---

-> As Open Source developers, user integrity and security is about being professional.

This page talks about the measures I take to mitigate risks, and how to report them.

## Commits

All commits are signed with my main [SSH Key](https://api.github.com/users/Tremeschin/keys) created in Q3 2024, well-kept and with a strong password, alongside my GitHub account having [Vigilant Mode](https://docs.github.com/en/authentication/managing-commit-signature-verification/displaying-verification-statuses-for-all-of-your-commits) enabled.

## Releases

All projects uses native release channels mechanisms for reproducibility and least privilege:

- :simple-python: **Python**: Uses PyPI [Trusted Publishers](https://docs.pypi.org/trusted-publishers/) in GitHub Actions workflows. Account has 2FA enabled, ephemeral 7 days tokens are used for creating new packages (once).
- :simple-rust: **Rust**: Uses crates.io [Trusted Publishing](https://crates.io/docs/trusted-publishing) in GitHub Actions workflows. Account login via GitHub, also with 2FA enabled, and ephemeral tokens for new crates (once).

Repositories have [Immutable Releases](https://github.blog/changelog/2025-10-28-immutable-releases-are-now-generally-available/) enabled, so bound tags and assets cannot be replaced or renamed after creation, only deleted - community packages are welcome to source from it.
