# Dependabot Alerts: Auto-Dismissal Demo

:dependabot: Dependabot's new auto-dismissal feature helps to cut false positives and reduce alert fatigue substantially.
Please share feedback on the [GH community discussion](https://github.com/orgs/community/discussions/54290)! 


## TL;DR

When the feature is enabled, Dependabot will auto-dismiss certain types of vulnerabilities that are unlikely to be exploitable, or at worst, have limited impact (e.g. long-running tests and builds). This feature is shipped currently for npm `devDependency` alerts with `scope:development`. This feature will help you proactively filter out false positives on development-scoped (non-production or runtime) alerts without compromising on high risk devDependency alerts.

On-by-default for public repositories, and opt-in for private repositories, this feature will result in 15% of low impact npm alerts being auto-dismissed moving forward – so you can focus on the alerts that matter, without worrying about the ones that don’t.

![Dependabot alerts auto-dismissal list view](https://github.com/github/dependabot-alerts/assets/5788563/e6d82f6d-e6be-47d9-bda8-1cfc1d38e990)


## Frequently asked questions

### Why is GitHub making this change?

At GitHub, we’ve been thinking deeply about how to responsibly address long-running issues around alert fatigue and false positives. Rather than over-indexing on one criterion like reachability or dependency scope, we believe that a responsibly-designed solution should be able to detect and reason on a rich set of complex, contextual alert metadata.

That's why, moving forward, we're releasing a series of ships powered by an underlying, all-new, flexible and powerful alert rules engine. Today's ship, our first application, leverages GitHub-curated vulnerability patterns to help proactively filter out false positive alerts.

### How does GitHub identify and detect low impact alerts?

Auto-dismissed alerts match GitHub-curated vulnerability patterns. These patterns take into account contextual information about how you’re using the dependency and the level of risk they may pose to your repository. To learn more, see our documentation on [covered classes of vulnerabilities](https://docs.github.com/en/code-security/dependabot/dependabot-alerts/using-alert-rules-to-prioritize-dependabot-alerts). 

### How will this activity be reported?

Auto-dismissal activity is supported across webhooks, REST, GraphQL, and the audit log for Dependabot alerts. In addition, you can review your closed alert list with the `resolution:auto-dismissed` filter.

### How will this experience look and feel?

Alerts identified as false positives will be automatically dismissed without a notification or new pull request, and appear as special timeline event. As these alerts are closed, you’ll still be able to review any auto-dismissed alerts with the `resolution:auto-dismissed` filter.

### How do I reopen an automatically dismissed alert?

Like any manually dismissed alert, you can reopen an auto-dismissed alert from the alert list view or details page. This specific alert won’t be auto-dismissed again.

### What happens if alert metadata changes or advisory information is withdrawn?

Dependabot recognizes and immediately responds to any changes to metadata which void auto-dismissal logic. For example, if you change the dependency scope and the alert no longer meets the criteria to be auto-dismissed, the alert will automatically reopen.

### How can I enable or disable the feature?
This feature is on-by-default for public repositories and opt-in for private repositories. Repository admins can opt in or out from your Dependabot alerts settings in the Code Security page. 

### Is this feature available for enterprise?
Yes! In addition to all free repositories, this feature will ship immediately to GHEC and to GHES in version 3.10.

### What's next?

Next, we’ll expose our underlying engine – which enables Dependabot to perform actions based on a rich set of contextual alert metadata – so you can write your own custom rules to better manage your alerts, too.

### How do I learn more?

- [About the auto-dismissal feature](https://docs.github.com/en/code-security/dependabot/dependabot-alerts/using-alert-rules-to-prioritize-dependabot-alerts)
- [Dependabot alerts REST](https://docs.github.com/en/rest/dependabot/alerts)
- [Dependabot alerts GraphQL](https://docs.github.com/en/graphql/reference/objects#repositoryvulnerabilityalert)
- [Dependabot alerts webhook](https://docs.github.com/en/webhooks-and-events/webhooks/webhook-events-and-payloads#dependabot_alert)

### How do I provide feedback?

Let us know what you think by [providing feedback](https://github.com/orgs/community/discussions/categories/code-security) -- we're listening!
