# k8s-node-label-monitor Helm Chart

## Chart Configuration

[k8s-node-label-monitor] can be configured to support a number of different
notification mechanisms based on observed changes to label states within the
cluster.

| Notifier | Description |
|----------|-------------|
| Logger   | Log-based notification, piggybacking on the default logger instance |
| REST API Endpoint | POSTs the JSON-encoded payload to a defined REST API endpoint  |
| Kubernetes CronJob | Manually trigger a Kubernetes CronJob (such as [descheduler]) |

Possible configurations for chart values are as follows:

```yaml
labelMonitor:
  logging: true
  cronjob: cronJobName
  notificationUrl: https://rest.api/endpoint
```

the default chart is configured to simply provide logging, while the others
must be manually configured at install time (e.g. `helm install --set labelMonitor.cronjob=descheduler ...`)

[k8s-node-label-monitor]: https://github.com/adaptant-labs/k8s-node-label-monitor
