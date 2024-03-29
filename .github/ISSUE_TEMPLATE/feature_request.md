---
name: Create New Job
about: Create a new Job in service-catalog-metering repository
labels: "new-job"
title: "Create Job: replace-me-with-your-job-name"
assignees: ""
---

Update the YAML properties and click "Submit new issue" to automate the creation of a new job in this repository:

```yaml job-creation-yaml
apiVersion: metering.wbd.com/v1alpha1
kind: CalculationJob
metadata:
  name: replace-me-with-your-job-name
  description: replace-me-with-your-description
  team: replace-me-with-your-job-team
  # This id will automatically filled after the github action run
  id:
  version: 1
  endpoint: replace-me-with-your-endpoint/v1
  dryRun: false
  #TODO: add boolean property to enable jobName addition as dimension
  needsUsageData: true
  active: true
  # This is an example for the format: '2023-11-11 00:00:00'
  notValidBefore: replace-me-with-your-notvalidbefore
  notValidAfter: replace-me-with-your-notvalidbefor
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
