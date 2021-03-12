# Helm 3 Chart Example

## The Chart File Structure

A chart is organized as a collection of files inside of a directory. The directory name is the name of the chart

```
├── Chart.yaml  (1)
├── charts      (2)
├── values.yaml (3)
├── templates   (4)
│   ├── _helpers.tpl (5)
│   ├── Notes.txt (6)
│   ├── deploymentconfig.yaml (7)
│   ├── route.yaml (7)
│   └── service.yaml (7)
├── crds   (8)
├── LICENSE (9)
└── README.md (10)
```


1. A YAML file containing information about the chart.
1. A directory containing any charts upon which this chart depends.
1. The default configuration values for this chart.
1. A directory of templates that, when combined with values, will generate valid Kubernetes manifest files.
1. Default location for template partials.
1. OPTIONAL: A plain text file containing short usage notes.
1. Templatized Kubernetes resources.
1. Custom Resource Definitions.
1. OPTIONAL: A plain text file containing the license for the chart.
1. OPTIONAL: A human-readable README file.


## Install the Example Helm Chart

```
$ cd example-nginx-chart
$ oc project paas-testing


$ helm install nginx . --values values.yaml
NAME: nginx
LAST DEPLOYED: Fri Mar 12 19:21:50 2021
NAMESPACE: paas-testing
STATUS: deployed
REVISION: 1
TEST SUITE: None

$ oc get pods
NAME             READY     STATUS      RESTARTS   AGE
nginx-1-cp77c    1/1       Running     0          74s
nginx-1-deploy    0/1       Completed   0          77s
```

## Uninstall the Helm Chart
```
helm uninstall nginx
release "nginx" uninstalled
```

