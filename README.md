# velero-backup-notification

This is a simple Kubernetes controller written in Ruby that sends email and/or Slack notifications when backups or restores are performed by [Velero](https://velero.io/).

## Installation

- Clone the repo
- Install with Helm

```bash
helm install ./helm \
  --name velero-backup-notification \
  --namespace velero \
  --set velero_namespace=velero \
  --set slack.enabled=true \
  --set slack.webhook=https://... \
  --set slack.channel=velero \
  --set slack.username=Velero \
  --set email.enabled=true \
  --set email.smtp.host=... \
  --set email.smtp.port=587 \
  --set email.smtp.username=... \
  --set email.smtp.password=... \
  --set email.from_address=... \
  --set email.to_address=... \
  --set email.subject_prefix="[Velero]"
```

That's it! You should now receive notifications when a backup/restore is started and when it's completed.
