# oragent
Orijtech observability service. Easily extract and examine your metrics, traces and profiles
from your services.

## Table of contents
- [Requirements](#requirements)
- [Running it](#running-it)
- [Services](#services)
    - [Agent](#agent)
    - [Metrics](#metrics)
    - [Traces](#traces)
- [Customizing your services](#customizing-your-services)

## Requirements

Requirement|Comment
---|---
Docker and docker-compose|If you don't have it, please visit https://www.docker.com/get-started
Port 55678|To receive traces and metrics in the [OpenCensus Agent Protocol](https://opencensus.io/agent/)
Port 55679|To self introspect the agent
Port 9411|By default, ships with Zipkin for examining traces
Port 9445|By default, ships with Prometheus for examining metrics

## Running it
```shell
docker-compose up
```

## Services
We ship a couple of services:

### Agent
It ships with an [OpenCensus Agent Protocol compatible daemon](https://opencensus.io/agent) available on port 55678 and [zPages](https://opencensus.io/zpages) available at port 55679. This agent will receive traces and metrics.

### Metrics
To examine metrics, by default [Prometheus](https://prometheus.io/) is availabe on port 9445, so visit http://localhost:9445/

### Traces
To examine traces, by default [Zipkin](https://zipkin.io/) is available on port 9411, so visit http://localhost:9411/

## Customizing your services
You can customize which agent receivers and exporters you'd like to change by modifying the file [oragent/config.yml](./oragent/config.yml)
following the [OpenCensus Agent guide](https://opencensus.io/agent) to entirely swap out [exporters](https://opencensus.io/agent/exporters) and [receivers](https://opencensus.io/agent/receivers)
