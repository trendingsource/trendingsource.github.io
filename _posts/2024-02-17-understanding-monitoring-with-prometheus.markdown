---
layout: post
title: "Understanding Monitoring with Prometheus"
date:   2024-02-17 21:46:25 +0000
categories: "Prometheus"
excerpt_image: https://sysdig.com/wp-content/uploads/Blog-Kubernetes-Monitoring-with-Prometheus-4-Architecture-Overview.png
image: https://sysdig.com/wp-content/uploads/Blog-Kubernetes-Monitoring-with-Prometheus-4-Architecture-Overview.png
---

Prometheus is an open-source monitoring system and time series database that allows you to query, alert on, and visualize metrics from various sources. In this article, we will explore Prometheus in depth, including its key concepts, usage, exporters, visualization options, and more.
### Metric Types in Prometheus
Prometheus provides four main metric types to help you observe your system's performance:
**Counter:** These metrics increment over time, like a total request count. A restart can reset the value to zero. 
**Gauge:** Used for metrics that can increase or decrease, like memory usage, thread counts, and temperatures. 
**Histogram:** Tracks observed values and counts them in configurable buckets. Common uses include request sizes or durations.
**Summary:** Similar to a histogram but aggregates observed values by configurable quantiles over a sliding time window, like 90%, 95% and 99% quantiles of request latencies.

![](https://appfleet.com/blog/content/images/size/w1200/2020/04/36-Kubernetes-monitoring-using-Prometheus.png)
### Reasons for System Monitoring
There are several key reasons why monitoring systems like Prometheus are essential:
Receiving alerts about abnormal system behavior helps you address issues proactively. Understanding both normal and abnormal patterns aids troubleshooting. Monitoring the impact of changes allows you to refine software or scale infrastructure appropriately. Performance metrics assist with capacity planning, optimization, and auditing the effects of changes.
### Prometheus Architecture
The Prometheus server scrapes metrics from instrumented applications, services, and devices via exporters. Exporters generate these metrics on a periodic basis and format them for Prometheus ingestion. Scraping is pull-based, avoiding client overheads. Stored time series data allows querying past states in addition to real-time information.
### Implementing Prometheus Exporters
Exporters are the bridge between applications and the Prometheus server. There are two main options for building exporters:
**Application Built-In:** Native applications that have monitoring built directly in. Careful integration is required to avoid regressions. 
**Standalone/Third-Party:** External services that poll data via APIs or logs and reformat it into the Prometheus schema. Commonly used for databases, queue systems or proprietary applications.
### Exporter Examples in Python
Python is a popular choice for building exporters due to its expressiveness and handy libraries like Prometheus client. Here are two examples:
A standalone CPU/memory exporter polls system metrics via psutil and exposes them on port 9999 for scraping. 
A Flask application exporter tracks request durations and uptime. It uses a WSGI app to avoid conflicts between Flask and Prometheus servers. Metrics are available at the /metrics endpoint.
### Visualizing with Grafana
With Prometheus storing time series data, **visualization tools** like Grafana allow you to build **dynamic dashboards** for monitoring. Grafana pulls metrics using PromQL and displays them graphically. This enables **intuitive exploration** of historical and current performance.
### The Elastic Stack
The Elastic Stack - Elasticsearch, Logstash, Kibana and Beats - provides another option for aggregating logs and metrics. Elasticsearch indexes data for search and Kibana presents visualizations. Metricbeat and Filebeat help stream metrics and logs. The commercial X-Pack brings additional alerting, reporting, security and more.
### Sensu for Multi-Cloud Monitoring
**Sensu Go** takes a different approach as an agent-based monitoring system. It offers visibility into services, infrastructure and custom metrics across any public or private cloud. Agents run on nodes to gather telemetry which is sent to a centralized backend for storage, processing and alerting. Sensu integrates with Prometheus or runs independently.
### Other Prometheus Features
Prometheus provides several important utilities beyond data collection and storage:
- A built-in web UI allows viewing live metrics, querying historical data and config inspection. 
- The Alertmanager handles alert grouping, deduplication, notifications across communication channels including email, Slack or PagerDuty.
- The Pushgateway aggregates batch metrics from uninstrumented sources into the time series database. 
- Client libraries in many languages simplify building exporters.
- The API allows custom clients for unusual data sources or novel visualizations beyond Grafana.
So in summary, Prometheus offers a comprehensive toolkit for gathering, storing, retrieving and notifying on metrics in real-time from over platforms and languages.
### Past, Present and Future of Open Source Monitoring
Initially the market flooded with many homegrown and commercial monitoring solutions as demand grew. Over time, the most full-featured and reliable tools have gained dominance through competitive pressures. Today's leading lights like Prometheus, Grafana and the Elastic Stack cater to diverse use cases across architectures from bare metal to containers and serverless. Meanwhile, new approaches continue innovating, making monitoring more powerful, flexible and cost-effective for modern applications and infrastructure. The next decade will be an exciting period for open source observability.
 ![Understanding Monitoring with Prometheus](https://sysdig.com/wp-content/uploads/Blog-Kubernetes-Monitoring-with-Prometheus-4-Architecture-Overview.png)