---
layout: site
title: Builds
body_class: code
---

As part of our commitment to Continuous Integration[^1], all products or libraries we release must have an automated build.

There are many ways to script an automated build, and the details will depend on the application or service in question.

### Build Steps

Irrespective of which tool you select, as a minimum an automated build must:

* be executed on a clean, provisioned environment
* use relevant package managers to install dependencies
* run any configured linters to identify code hygiene issues, failing the build if any are identified
* run test suites and generate test reports, failing the build if any test failures occur
* make available any logs generated during the build
* produce a uniquely-identified distribution artifact

### Artifacts

An important responsibility of the automated build is to produce the distribution artifacts. An automated process must exist for deploying the artifacts on to an environment provisioned to run it. Artifacts must:

* include all code required for the artifact to run
* contain any required third-party library dependencies
* never contain secrets or sensitive information
* This ensures that our artifact is complete and deployable, and always includes those dependencies and libraries that CI has tested against.

Artifacts should not contain code required during test and build, nor any development dependencies.

If the artifact is a Docker container image, the same rules apply (except the third-party dependencies include the underlying OS).

[^1]: [Continuous Integration](https://martinfowler.com/articles/continuousIntegration.html)