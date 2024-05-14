# k8sMultiLogForDynatrace

** Stream multiple logs from a container (In OpenShift/Kubernetes) into Dynatrace. View comments of the files for further details.

** Can be used for other logging solutions with k8s, although this targets Dynatrace.

** This is a demo/proof of concept.

** Dynatrace environment: 
  - Logging of every app is disabled (to save on costs, performance, etc)
  - Deployed using the dynatrace operator that installs a DaemonSet on all nodes
  - Only "Known Technologies" or "High CPU consuming" processes will display in Dynatrace, unless declared
  - Declare custom processes in Dynatrace UI: Manage -> Settings -> Processes and Containers -> Declarative process grouping. View Dynatrace docs for more details.

## Tree:
```
├── OptionA-MergeLogsIntoOneSTDOUT : This merges 2+ logs into one stream (STDOUT)
│   ├── Containerfile-ExampleA - detailed example
│   ├── Containerfile-ExampleB - realistic app example
│   └── deployment.yaml - not important as all changes are done via Containerfile
├── OptionB-SeparateLogsUsingSidecars : This separates each log to be tailed by its own streams (STDOUT)
│   ├── Containerfile_mainApplication - Basic realistic app, not many changes.
│   └── deployment.yaml - All major changes are done here
```

