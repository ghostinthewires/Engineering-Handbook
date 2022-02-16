---
layout: site
title: Project Documentation
body_class: process
---

Documentation is important for understanding the project at a higher level. This is where you can document decisions made about architecture, choice of external libraries and plugins, and process.

Generally speaking, long-lived documentation for a project should live within the project repository in the form of markdown files. This ensures that all documentation is version-controlled along with the project, and any changes needed to documentation can be done as part of a pull request on the project.

As a standard, projects should also contain READMEs at the project root level. These READMEs should lay out the basics of getting started with the project (i.e. instructions for installation and workflow), and no other information. Examples:

* How to build the project
* If it is a deployable, how to run it
* If it is a library, a quickstart on how to use it
* If it has an API, a link to more detailed API documentation

Additional meta information about the project not specifically intended for engineers can be located in a project wiki in Confluence and linked.
### Infra Runbook

If the project is a deployable, rather than a library, it must also have an Infra Runbook. This details the production infrastruture.

### APIs

Public APIs should have a page describing how to use the API. These documents should at a minimum include all publicly available calls, details on how to use authentication and example response and request formats.
