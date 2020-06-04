---
title: StreamNative Cloud Overview
id: sn-cloud-overview
category: overview
---

# Introduction

The StreamNative Cloud provides an easy-to-use and fully-managed Pulsar service in the public cloud. The managed Pulsar clusters can run either in StreamNative cloud accounts or in customer’s cloud accounts. You can sign up on StreamNative Cloud through the StreamNative website to create and manage Pulsar clusters. After signing up for the cloud service, you can use the StreamNative Cloud CLI tool (snctl) for managing the clusters or use the StreamNative Cloud UI (Cloud Manager) for monitoring and managing the created cluster.

Based on whether to share physical resources with other organizations, Pulsar clusters are divided into *dedicate* clusters and *shared* clusters.

- A dedicated cluster has its own physical resources dedicated to the organization that creates it. You can choose to create a dedicated cluster under StreamNative cloud accounts or in customers' cloud accounts.

- A shared cluster shares the physical resources with other organizations. You can choose to create a shared cluster based on the available regions of certain cloud providers.

The following figure illustrates the overview of the StreamNative Cloud.

![](../../sn-cloud-overview.png)

# System architecture

The StreamNative Cloud consists of one main cluster for managing all StreamNative cloud resources and many control clusters spreading across different cloud providers for managing individual Pulsar clusters.

## Main cluster

The StreamNative Cloud service is mainly run in the main cluster for serving the StreamNative Cloud UI and API (https://api.streamnative.cloud). Users connect to the main cluster for signing up the service and creating and managing Pulsar clusters.

The main cluster consists of the following components:

- Cloud dashboard: it is the UI for the cloud service.
- Cloud API: access the cloud service.
- Pulsar cluster: aggregate metrics and resources from individual control clusters.

## Control cluster

Each region has one control cluster for managing the Pulsar clusters created in that region. The control cluster mainly comprises of the following components:

- API server: access and managing the resources in this region.
- Pulsar cluster: store the metrics collected from the managed clusters in this region.
- `installer`: create and update Pulsar clusters in this region.
- `monitor` : collect the metrics from the managed clusters in this region.
- `meter`: collect the statistics of resources (such as data in/out and retention) from the managed clusters in this region.

The following figure illustrates all the components of StreamNative Cloud.

![](../../image/sn-cloud-system-architecture.png)

# Strengths

## Quick and customized deployment

- Deploy production-grade Pulsar cluster within minutes.
- Support host clusters and managed clusters based on the location where Pulsar clusters are hosted.

  - Hosted clusters: the Pulsar clusters are hosted and managed in StreamNative cloud accounts. These clusters are automatically provisioned in the StreamNative Cloud website.

  - Managed clusters: the Pulsar clusters are hosted and managed in customers’ cloud accounts due to compliance and security requirements. Those clusters are provisioned manually.

## High flexibility

## Great Security

## Low costs

## Powerful operation and maintenance capability

# Features

# Documents
