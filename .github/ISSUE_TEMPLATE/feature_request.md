---
name: Create New Job Definition
about: Create a new job definition
title: "Create a new job: replace-me-with-your-job-name"
labels: "new-job"
assignees: ""
---

Update the YAML properties and click "Submit new issue" to automate the creation of a new cost calculation job:

```yaml job-definition-yaml
apiVersion: metering.wbd.com/v1alpha1
kind: CalculationJob
metadata:
  name: example-cost-calulation
  description: cost-calculator
  team: team-name
  id: 14a743e5-85f9-49d9-9371-823de7002a8e
  version: 1
  endpointVersion: 1
  dryRun: false
  needUsageData: true
  active: true
  notValidBefore: "2023-11-11 00:00:00"
  notValidAfter: "2023-12-11 00:00:00"
spec:
  usageDataQueries:
    - alias: dataset1
      query: sum(metric) by (omd_component)
    - alias: dataset2
      query: sum(metric2) by (omd_component)
  costDataQueries:
    - alias: costdata1
      query: SELECT SUM(cost) FROM x WHERE tag1='logging-as-a-service' AND tag2='backend-logging'
  calculationQuery: |
    SELECT * from dataset1 as d1 LEFT JOIN dataset2 as d1 ON d1.omd_component = d2.omd_component
```
