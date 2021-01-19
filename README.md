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
