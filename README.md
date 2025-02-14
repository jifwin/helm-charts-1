# Victoria Metrics Helm Charts

[![Artifact Hub](https://img.shields.io/endpoint?url=https://artifacthub.io/badge/repository/victoriametrics)](https://artifacthub.io/packages/search?repo=victoriametrics&verified_publisher=true)
[![License](https://img.shields.io/github/license/VictoriaMetrics/VictoriaMetrics.svg)](https://github.com/VictoriaMetrics/helm-charts/blob/master/LICENSE)
![Helm: v3](https://img.shields.io/static/v1?label=Helm&message=v3&color=informational&logo=helm)
[![Slack](https://img.shields.io/badge/join%20slack-%23victoriametrics-brightgreen.svg)](https://slack.victoriametrics.com/)

This repository contains helm charts for VictoriaMetrics and VictoriaLogs.

## Add a chart helm repository

Access a Kubernetes cluster.

Add a chart helm repository with follow commands:

```console
helm repo add vm https://victoriametrics.github.io/helm-charts/

helm repo update
```

List [all charts](#list-of-charts) and versions of `vm` repository available to installation:

```console
helm search repo vm/
```

The command must display existing helm chart e.g.

```shell
NAME                         	CHART VERSION	APP VERSION        	DESCRIPTION
vm/victoria-logs-single      	0.1.3        	v0.3.0-victorialogs	Victoria Logs Single version - high-performance...
vm/victoria-metrics-agent    	0.9.8       	v1.93.3            	Victoria Metrics Agent - collects metrics from ...
vm/victoria-metrics-alert    	0.7.6        	v1.93.3            	Victoria Metrics Alert - executes a list of giv...
vm/victoria-metrics-anomaly  	0.3.4        	v1.1.0             	Victoria Metrics Anomaly Detection - a service ...
vm/victoria-metrics-auth     	0.3.6       	v1.93.3            	Victoria Metrics Auth - is a simple auth proxy ...
vm/victoria-metrics-cluster  	0.10.7       	v1.93.3            	Victoria Metrics Cluster version - high-perform...
vm/victoria-metrics-gateway  	0.1.46       	v1.93.3            	Victoria Metrics Gateway - Auth & Rate-Limittin...
vm/victoria-metrics-k8s-stack	0.17.7       	v1.93.3            	Kubernetes monitoring on VictoriaMetrics stack....
vm/victoria-metrics-operator 	0.23.1       	0.34.1             	Victoria Metrics Operator
vm/victoria-metrics-single   	0.9.7       	v1.93.3            	Victoria Metrics Single version - high-performa...
```

## Installing the chart

Export default values of ``victoria-metrics-cluster`` chart to file ``values.yaml``:

```console
helm show values vm/victoria-metrics-cluster > values.yaml
```

Change the values according to the need of the environment in ``values.yaml`` file.

Test the installation with command:

```console
helm install victoria-metrics vm/victoria-metrics-cluster -f values.yaml -n NAMESPACE --debug --dry-run
```

Install chart with command:

```console
helm install victoria-metrics vm/victoria-metrics-cluster -f values.yaml -n NAMESPACE
```

Get the pods lists by running these commands:

```console
kubectl get pods -A | grep 'victoria-metrics'

# or list all resorces of victoria-metrics

kubectl get all -n NAMESPACE | grep victoria
```

Get the application by running this commands:

```console
helm list -f victoria-metrics -n NAMESPACE
```

See the history of versions of ``victoria-metrics`` application with command.

```console
helm history victoria-metrics -n NAMESPACE
```

## How to uninstall VictoriaMetrics

Remove application with command.

```console
helm uninstall victoria-metrics -n NAMESPACE
```

## Kubernetes compatibility versions

helm charts tested at kubernetes versions from 1.23 to 1.27.

## List of Charts

- [Victoria Logs Single-Node](./charts/victoria-logs-single)
- [Victoria Metrics Agent](./charts/victoria-metrics-agent)
- [Victoria Metrics Alert](./charts/victoria-metrics-alert)
- [Victoria Metrics Anomaly](./charts/victoria-metrics-anomaly)
- [Victoria Metrics Auth](./charts/victoria-metrics-auth)
- [Victoria Metrics Cluster](./charts/victoria-metrics-cluster)
- [Victoria Metrics Gateway](./charts/victoria-metrics-gateway)
- [Victoria Metrics k8s Stack](./charts/victoria-metrics-k8s-stack)
- [Victoria Metrics Operator](./charts/victoria-metrics-operator)
- [Victoria Metrics Single-node](./charts/victoria-metrics-single)
