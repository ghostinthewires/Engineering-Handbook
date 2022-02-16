---
layout: site
title: Continuous Integration
body_class: code
---

We use Continuous Integration[^1] for any code that we release. However, we do not follow a strict trunk-based development workflow; rather, we use small, short-lived feature branches to ensure we are never straying far from the workflow branch - see [Development Process](development-process.html) for specifics.

Branches must be verified by an [automated build](builds.html) prior to code review and merge. This is tightly integrated into [source control](source-control.html) using GitHub Actions.

CI should trigger automatically on Pull Requests to the main branch, and must run the same [automated build](builds.html) as workflow branches.

If the project is open-sourced and the repository is public, the build should also be public.

[^1]: [Continuous Integration](https://martinfowler.com/articles/continuousIntegration.html)