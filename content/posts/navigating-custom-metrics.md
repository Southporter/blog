---
title: "Navigating Custom Metrics"
date: 2020-04-15T15:22:17-05:00
draft: false
author: "Shem Sedrick"
tags:
  - kubernetes
  - prometheus
keywords:
  - kubernetes
  - k8s
  - custom metrics
description: "Navigating through the custom metrics api"
showFullContent: false
---


# Navigating Kubernetes Custom Metrics and HPA

### Custom Metric API Provider

This post assumes a few things:

- You have a kubernetes cluster setup and `kubectl` correctly configured
- You have a custom metrics api deployed into the cluster

For clarity, the custom metrics api that I am using is the [prometheus-adapter](https://github.com/DirectXMan12/k8s-prometheus-adapter). Some may be implemented differently so your mileage may vary.


### Using the Custom Metrics API


```bash
kubectl get --raw "/apis/custom.metrics.k8s.io/v1beta1" | jq
```

This outputs a list of available metrics in the custom metrics api. You may get a lot of lines in the output, so you may want to pipe that into a file or editor or your clipboard.

You will see lots of enteries with the following format:

```json
{
  "name": "resource/metric_name",
  "singularName": "",
  "namespaced": true|false,
  "kind": "MetricValueList",
  "verbs": [
    "get"
  ]
}
```

The main thing to take not of is the `name` field. We can use that to get further information into a metric.

To get the actual metric, you can use the following patern of request:

```bash
kubectl get --raw "/apis/custom.metrics.k8s.io/v1beta1/namespaces/NAMESPACE_HERE/resource/resource_name/metric_name" | jq

# You can also leave out the NAMESPACE_HERE
kubectl get --raw "/apis/custom.metrics.k8s.io/v1beta1/namespaces/*/resource/resource_name/etric_name" | jq
```

Enough with abstractions, let's have a real example.
Say you have metric that is attached to a Deployment. Your metric is `kube_deployment_status_replicas_available`.
You should see the following from `kubectl get --raw "/apis/custom.metrics.k8s.io/v1beta1"`:

```json
{
  "name": "deployments.extensions/kube_deployment_status_replicas_available",
  "singularName": "",
  "namespaced": true,
  "kind": "MetricValueList",
  "verbs": [
    "get"
  ]
}
```


Based on this, we can now query and get the metric. Let's assume that you have a Deployment named `my_cool_deployment` in the namespace `demo`:

```bash
kubectl get --raw "/apis/custom.metrics.k8s.io/v1beta1/namespaces/demo/deployments.extendsions/my_cool_deployment/kube_deployment_status_replicas_available"
```

This should give you something like the following:

```json
{
  "kind": "MetricValueList",
  "apiVersion": "custom.metrics.k8s.io/v1beta1",
  "metadata": {
    "selfLink": "/apis/custom.metrics.k8s.io/v1beta1/namespaces/demo/deployments.extensions/my_cool_deployment/kube_deployment_status_replicas_available"
  },
  "items": [
    {
      "describedObject": {
        "kind": "Deployment",
        "namespace": "demo",
        "name": "my_cool_deployment",
        "apiVersion": "extensions/v1beta1"
      },
      "metricName": "kube_deployment_status_replicas_available",
      "timestamp": "2020-04-15T00:00:00Z",
      "value": "4"
    }
  ]
}
```


###### Namespace Metric Caveat
**Note:** Getting a metric attached to a namespace is a little different, at least when using the [prometheus-adapter](https://github.com/DirectXMan12/k8s-prometheus-adapter). Use the following when getting a namespace metric:

```bash
kubectl get --raw "/apis/custom.metrics.k8s.io/v1beta1/namespaces/*/metrics/metric_name"

# Or with the namespace of demo
kubectl get --raw "/apis/custom.metrics.k8s.io/v1beta1/namespaces/demo/metrics/metric_name"
```


### The fight for knowledge
It took me way to long to figure out how to navigate this and get the information I needed. Hopefully, this will save some of you some pain in trying to understand how to navigate the custom metric api.
