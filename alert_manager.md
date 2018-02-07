## <a name="alertmanager"></a>Alert Manager

```bash
https://192.168.27.199:8443/alertmanager/reload

https://192.168.27.199:8443/prometheus/reload
```

Configmap alert-rules

```json

  "data": {
    "sample.rules": "ALERT NodeMemoryUsage\n  IF (((node_memory_MemTotal-node_memory_MemFree-node_memory_Cached)/(node_memory_MemTotal)*100)) > 25\n  FOR 1m\n  LABELS {\n    severity=\"page\"\n  }\n  ANNOTATIONS {\n    SUMMARY = \"{{$labels.instance}}: High memory usage detected\",\n    DESCRIPTION = \"{{$labels.instance}}: Memory usage is above 75% (current value is: {{ $value }})\"\n  }\nALERT HighCPUUsage\n  IF ((sum(node_cpu{mode=~\"user|nice|system|irq|softirq|steal|idle|iowait\"}) by (instance, job)) - ( sum(node_cpu{mode=~\"idle|iowait\"}) by (instance,job)))/(sum(node_cpu{mode=~\"user|nice|system|irq|softirq|steal|idle|iowait\"}) by (instance, job)) * 100 > 2\n  FOR 1m\n  LABELS { \n    service = \"backend\" \n  }\n  ANNOTATIONS {\n    summary = \"High CPU Usage\",\n    description = \"This machine  has really high CPU usage for over 10m\",\n  }"
  }
```



Configmap monitoring-prometheus-alertmanager

```json
  "data": {
    "alertmanager.yml": "global:\nreceivers:\n- name: default-receiver\n- name: slack_general\n  slack_configs:\n  - api_url:  'https://hooks.slack.com/services/<YOUR API KEY>l'\n    channel: '#devops'\nroute:\n  group_wait: 10s\n  group_interval: 5m\n  receiver: slack_general\n  repeat_interval: 3h"
  }

```