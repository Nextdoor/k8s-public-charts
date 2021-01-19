# Common Helm Chart Components

This repo holds a series of common helm-charts that we've developed just to
help speed up our internal development and reduce repetition. There's no
business logic or anything private here.

## Installation of this repo

The repository metadata and artifacts are hosted by Github. All the data here
is public.

    $ helm repo add nextdoor https://oss.nextdoor.com/k8s-public-charts
    $ helm repo update
    $ helm search repo nextdoor
    NAME                      	CHART VERSION	APP VERSION	DESCRIPTION
    nextdoor/prometheus-alerts	0.0.1        	0.0.1      	Helm Chart that provisions a series of common P...

## Charts

All charts are fully documented in their individual values files. Use `helm
search repo nextdoor` to list the charts and `helm show values nextdoor/<chart
name>` to see the options for the charts.

## Using Charts in your Helm Chart

The intention of this repository is to make re-usable components - not projects
that are launched on their own. Given your existing `Chart.yaml` that looks like this:


    apiVersion: v2
    appVersion: "1.0"
    description: Launches the Nextdoor Widget Service
    name: neighbors-widget
    version: 0.1.0

You can add a simple `dependencies` section to bring in a component chart, and
then configure it with your `values.yaml` files. Here's the new `Chart.yaml` for example:

    apiVersion: v2
    appVersion: "1.0"
    description: Launches the Nextdoor Widget Service
    name: neighbors-widget
    version: 0.1.0
    dependencies:
      - name: prometheus-alerts
        version: 0.0.2
        repository: https://oss.nextdoor.com/k8s-public-harts

And you might then configure your `values.yaml` like this:

    # My own app configs..
    image: ...
    tag: ...

    # Customize the alerting for this project
    prometheus-alerts:
      alertManager:
        enabled: true
        pagerduty:
          routing_key: ...
