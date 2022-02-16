---
layout: site
title: Code Reviews
body_class: process
---

Code reviews ensure the quality of what we’re building remains high, and that code we’re vouching for remains up to the same standard. Reviews are primarily about assessing the code quality, not necessarily the behaviour. The code author is the one responsible for writing the code and making sure it works, while the reviewer is there to review the code.

All code at Ghostinthewires Inc. must go through peer review before it can be merged. This can be done by raising a pull request (henceforth “PR”) on the relevant GitHub repository and asking your colleagues for input.

### Types of Reviews

There are three main styles of review that we undertake:

* **External Reviews** – Third-party plugins we’re seeking to use.
* **Internal Reviews** – Standard reviewing process before code is merged.
* **In-Depth Reviews** – Internal reviews, but for tricky features.

Each of these styles of review has different factors to check for, but generally speaking, internal reviews are stricter on code quality checks, while external reviews are stricter on security and performance checks. Generally speaking, internal reviews have a higher level of trust, so reviews can focus more on ensuring quality is high. With that said, security and performance must always be a factor regardless of source, as they are critical to the end product.

If an external review reveals a plugin is technically OK, but has low code quality, checking for alternatives is typically a good idea. These plugins are generally harder to maintain, and are a [code smell](https://blog.codinghorror.com/code-smells/) . If a plugin has a large development team that is active, this can outweigh the code quality factor, but it’s always worth checking.

Internal reviews should generally be performed piecemeal on the project; in other words, they should be done on pull requests before merge. This provides a much smaller set of code to be reviewed, and allows more in-depth reviews. Larger blocks of code are harder to review fully. The flip-side of this is that it can be harder to see the larger picture of the whole project, so the reviewer should be conscious of how code fits into the context of the project. In-depth reviews can be done by-request when someone works on something and wants a closer look to verify what they’re doing is right.

Never be afraid to ask for clarification. If you spot something in a review that seems a bit weird, mention it. It’s easier to have a quick conversation in the PR comments to double-check, than to assume something is correct only to find the issue in production. Spending time writing an emergency fix and deploying it is much more expensive (in time, and potentially in revenue) than taking the time initially.

When working with code submitted by partners, differing levels of review may be applied. Generally speaking, we want to help our partners to think and work like us, so these reviews can be treated as internal reviews. Some projects may necessitate different levels of reviewing, but should never be less strict than external reviews, as we need to vouch for this code. Style issues can be overlooked in these cases, but security can never be. Be pragmatic.

### Factors to Review

### Security

Security is one of the biggest factors involved in any review. All code that we push into a production or staging environment must be completely secure.

### Performance

Performance is very important with the scale of the sites we work on. Determining what is or isn’t performant is tough, and this role mostly falls on the code author. However, performance should also be checked by the reviewer, especially for external plugins that may not have been created with performance in mind.

### Accessibility

Our work should be usable and accessible for as many users as possible. Reviewers should check for obviously inaccessible patterns.

### Style

Code reviews should usually check that coding style matches our coding style guidelines. If someone is intentionally ignoring a guideline, that’s fine too.

Internal reviews are typically the only ones that need style checking, as we’re not responsible for external plugins. The exception to this is if we’re specifically asked for it.

Style checks should mostly be automated, as it’s easy to miss when writing or during a review. This can be performed by the Super Linter, and can be enabled on a repo using the [GitHub Action](https://github.com/github/super-linter/blob/master/README.md). 

### Behaviour and Logic

The actual behaviour of code typically does not need reviewing. Reviews are a process of checking work by others, not to duplicate that work again. Sometimes however, you may want your code double-checked, especially if you have some tricky logic.

Feel free to ask on any pull request for a more in-depth review; it’s always better to ask and not need it than to ship with something potentially broken. The best people to ask for these reviews are other people on the same project, as they can verify that the behaviour matches what they expect much more easily.

### Requesting a Review

When your code is ready for review, it’s up to you to request the review. The way to do this is via the GitHub “Request a Review” feature. This could also be visualised via a kanban column in a Jira Project Board.

### How do I perform a Code Review?

Don’t always rely on the diff - depending on the size of the changes in the pull request, it might be a good idea to check out the branch locally. This gives you a number of benefits:

* You can open up your IDE and see the code as it was written. A variable may have been renamed - you can search in your IDE for the old values.
* You can spin up the app and take it for a test drive. The code might look ok, but the UI may look terrible and spam the console with errors, APIs might be hard to use, and it might run like a dog.
* You can run the local build (including tests) and see any potential breakages.

**For the author:**

* Always merge the destination branch into your feature branch before starting the review process – otherwise your diff might show spurious changes and you could end up with a change that needs merge conflict resolution after the review
* **Review your own code before you ask someone else to review it!**  Make sure what you present to the code reviewer doesn’t have changes you know you should make.
* **Do not expect code reviewers to find bugs!**  They sometimes will, but that is not their job.
* Assign the review to the person who knows the area of code you are working on best, not the person who does the easiest reviews.  But try to spread your reviews around if you can.
* New team members should act as “secondary” reviewers on a bunch of code reviews before reviewing code on their own. 
* Continue working by branching off of your feature branch while you are waiting.  This is a powerful way not to get blocked.
* If you are blocked on a review, you should be aggressive in pinging the reviewer, and, if that doesn’t work, a manager.  **Fast code reviewing is a key part of a healthy team and everyone should feel responsible for reviewing code quickly.**  Speed of review is inversely correlated with the size of the change, so if you want your changes reviewed quickly, keep them small.
* When a review comes back, address every comment, even if just acknowledging that you made the suggested change.
* Test your code again after you have made the suggested changes!  Blindly commiting the reviewer’s suggested change is a common source of bugs and build breaks.
* Code reviews from more senior engineers are how you become a better coder – remember that.  Don’t get defensive when an engineer requests changes.

**For the reviewer:**

* **Treat code reviews as high priority.**  If you can’t immediately direct your attention to the review, you should let the author know when you expect to get to it.  I don’t think any review should sit for more than a couple hours unaddressed.
* **Focus on design issues first and foremost.**  The most impactful reviews ask a few key questions about design issues that are likely to cause problems down the line if not addressed early on.  

### When can I hit merge?

There are no hard and fast rules about when a PR can be merged, except that you have to have had a round of feedback from a peer, and responded to all raised issues either by committing further work or resolving any discussion in the PR itself. You may be merging into a project which another team is the owner for, this is encouraged! In doing so, you should make sure that a least one approval is from a member of that team.

We use Github branch rules to ensure that PRs must receive at least one code review approval, and have passed all required automated checks.

Reviewers are expected to approve, reject, or comment on the pull request, but should leave merging the pull request to the PR author unless asked specifically to merge.
