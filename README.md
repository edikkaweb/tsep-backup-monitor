# TSEP backup health monitor

Independent hourly HTTPS check of the public, minimal TSEP backup status.
No account credentials, user records, backup contents or application source code are stored here.
The check runs on GitHub-hosted infrastructure and does not depend on the Mac or VPS scheduler.
It verifies the age of the autonomous status and latest offsite backup, and the `ok` flag.
The VPS flag also includes early archive-capacity, free-disk and deletion-journal warnings.

Notifications: enable GitHub Actions web/email notifications for the workflow creator,
preferably failures only. A manual `simulate_failure` drill emits a clearly labelled
intentional failure after the live check; it does not change the service.

Limits: scheduled jobs may be delayed; GitHub disables public-repository schedules after
60 days without repository activity. Inspect the Actions schedule as part of monthly
operations. This is a beta monitoring mechanism, not an availability SLA or a billing cap.

Official documentation:
- https://docs.github.com/en/actions/concepts/workflows-and-actions/notifications-for-workflow-runs
- https://docs.github.com/en/actions/reference/workflows-and-actions/events-that-trigger-workflows#schedule
