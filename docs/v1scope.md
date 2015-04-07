# Kubernetes v1 Scoping

Updated Apr 7, 2015

This document is intended to capture the set of supported use cases, features,
docs, and patterns that we feel are required to call Kubernetes “feature
complete” for a 1.0 release candidate.  This list does not emphasize the bug
fixes and stabilization that will be required to take it all the way to
production ready.  This is a living document, and is certainly open for
discussion.

## Target workloads

Most realistic examples of production services include a load-balanced web
frontend exposed to the public Internet, with a stateful backend, such as a
clustered database or key-value store. We will target such workloads for our
1.0 release.

## APIs and core features
1. Consistent v1 API ([#1519](https://github.com/GoogleCloudPlatform/kubernetes/issues/1519))
2. Multi-port services for apps which need more than one port on the same portal IP ([#1802](https://github.com/GoogleCloudPlatform/kubernetes/issues/1802))
3. Nominal services for applications which need one stable IP per pod instance ([#260](https://github.com/GoogleCloudPlatform/kubernetes/issues/260))
4. API input is scrubbed of status fields in favor of a new API to set status ([#4248](https://github.com/GoogleCloudPlatform/kubernetes/issues/4248))
5. Input validation reporting versioned field names ([#2518](https://github.com/GoogleCloudPlatform/kubernetes/issues/2518))
6. Error reporting: Report common problems in ways that users can discover
7. Event management: Make events usable and useful
8. Persistent storage support ([#4055](https://github.com/GoogleCloudPlatform/kubernetes/issues/4055))
9. Allow nodes to join/leave a cluster ([#2303](https://github.com/GoogleCloudPlatform/kubernetes/issues/2303),[#2435](https://github.com/GoogleCloudPlatform/kubernetes/issues/2435))
  - high level [design doc](https://github.com/GoogleCloudPlatform/kubernetes/blob/master/docs/design/clustering.md).
10. Handle node death
11. Allow live cluster upgrades ([#2524](https://github.com/GoogleCloudPlatform/kubernetes/issues/2524))
12. Allow kernel upgrades
13. Allow rolling-updates to fail gracefully ([#1353](https://github.com/GoogleCloudPlatform/kubernetes/issues/1353))
14. Easy .dockercfg
15. Demonstrate cluster stability over time
16. Kubelet use the kubernetes API to fetch jobs to run (instead of etcd) on supported platforms

## Reliability and performance

1. Restart system components in case of crash ([#2884](https://github.com/GoogleCloudPlatform/kubernetes/issues/2884))
2. Scale to 100 nodes ([#3876](https://github.com/GoogleCloudPlatform/kubernetes/issues/3876))
3. Scale to 30-50 pods (1-2 containers each) per node ([#4188](https://github.com/GoogleCloudPlatform/kubernetes/issues/4188))
4. Scheduling throughput: 99% of scheduling decisions made in less than 1s on 100 node, 3000 pod cluster; linear time to number of nodes and pods ([#3954](https://github.com/GoogleCloudPlatform/kubernetes/issues/3954))
5. Startup time: 99% of end-to-end pod startup time with prepulled images is less than 5s on 100 node, 3000 pod cluster; linear time to number of nodes and pods ([#3952](https://github.com/GoogleCloudPlatform/kubernetes/issues/3952), [#3954](https://github.com/GoogleCloudPlatform/kubernetes/issues/3954))
6. API performance: 99% of API calls return in less than 1s; constant time to number of nodes and pods ([#4521](https://github.com/GoogleCloudPlatform/kubernetes/issues/4521))
7. Manage and report disk space on nodes ([#4135](https://github.com/GoogleCloudPlatform/kubernetes/issues/4135))
8. API test coverage more than 85% in e2e tests

## Project
1. Define a deprecation policy for expiring and removing features and interfaces, including the time non-beta APIs will be supported
2. Define a version numbering policy regarding point upgrades, support, compat, and release frequency.
3. Define an SLO that users can reasonable expect to hit in properly managed clusters
4. Accurate and complete API documentation
5. Accurate and complete getting-started-guides for supported platforms

## Platforms
1. Possible for cloud partners / vendors to self-qualify Kubernetes on their platform.
2. Define the set of platforms that are supported by the core team.

# Beyond 1.0

We acknowledge that there are a great many things that are not included in our 1.0 roadmap.  We intend to document the plans past 1.0 soon, but some of the things that are clearly in scope include:

1. Scalability - more nodes, more pods
2. HA masters
3. Monitoring
4. Authn and authz
5. Enhanced resource management and isolation
6. Better performance
7. Easier plugins and add-ons
8. More support for jobs that complete (compute, batch)
9. More platforms
10. Easier testing
