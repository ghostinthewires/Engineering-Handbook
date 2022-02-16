---
layout: site
title: Development Process
body_class: process
---

### Steps

The general process for development is:

**0. Determine MVP for the issue**

Before you start, make sure the issue is broken down to the minimum viable product. If it can be broken up into multiple issues, it should be. This allows better isolation of work, and better tracking for the project managers.

Issues should succinctly describe how to fix them. Vague descriptions make it hard to know when the issue is complete, and can make it harder for other people to get involved in the project.

**1. Take the issue**

When working on an issue, make sure you’re not overlapping with existing work. This is typically handled by assigning the issue to yourself via a kanban board in JIRA.

**2. Write the code!**

You’ve done the easy bits, now it’s time to actually do the work.

This work needs to happen on a branch. The pattern you should use is`{JIRA_issue_number}-{name_of_feature}` `(e.g. SP-123-add-user-auth)`.

**3. Push early, push often**

As soon as your code is in a usable state, you should push it up. This allows tracking the issue over time a little easier, and avoids cases where you disappear for a while to sort out an issue. It also allows others to watch and potentially correct a wrong assumption before you spend hours on it, and will trigger automated testing if set up for the repo.

You don’t need to push every commit, but be sensible.

**4. Iterate, complete, and submit a PR for review**

Keep working, and when ready, submit the PR for review, see the [reviews guide](code-reviews.html) for more info.

Pull requests should specifically mention the issues they close at the least. Ideally, have a sentence or two that describes how you solved the issue as well to provide context on the pull request.

**5. Merge and ship!**

Merging the branch is usually handled by the PR Author once approved by a peer. The branch will be automatically deleted after merging via GitHub’s branch policy.

### Deployable Main

The main branch of the repository should be deployable at any time. Deployment for projects is handled via GitHub Actions, where the production environment is essentially updated to the current commit (head) of main.

This means that features should only be merged into main when they’re ready to be deployed. Anything in main must go through code review before merging, and this is enforced via the GitHub repository settings.

For more complex projects with differing QA processes, additional workflow branches such as staging can be created. Features can then be merged into these branches before then merging those into main. This workflow only makes sense for more complex projects, and should be avoided if not necessary; keep it as simple as possible.

### Features in Isolation

With the asynchronous nature of how we work, it’s important that everyone is able to continue making movement without being blocked on anyone else. To ensure smooth flowing development, we create branches for new features or bug fixes. When these changes are ready, they then proceed into review and are merged.

Each branch should focus on a single issue with the goal of closing it out. Following the agile methodology, these issues should also be broken down as much as possible, so each branch should be a single focussed change to close out the issue.

Generally, these features should be entirely independent of each other. This allows engineers to grab an issue and work away on it without blocking. However, not all features are truly independent; a branch may provide underlying functionality required by other features. Merging these branches early helps.

### Incremental Improvement

Features should be shipped early in a minimal state, then improved further in future changes. The agile methodology is heavily focused on iterative improvement, encouraging constant improvement.

This means merging features when they’re ready in a minimal state, and continuing to build on top of this. This makes development much more parallelisable (it’s a word, trust me), as multiple engineers can work on different parts of the same feature once the base of it is in place. This is crucial for asynchronous work, with Ghostinthewires Inc. having a distributed workforce.