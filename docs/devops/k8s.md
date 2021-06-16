---
title: k8s
authors:
    - Alexander Serowy
---

## pod priority

> <https://github.com/aserowy/k8sworkshop/tree/master/PodPrioriy>

- manages pod numbers on low ressources with priorities
- the higher the priority the more important the pod is
- on low resources less important pods get destroyed to enable replicas of more important pods
- with tooling you can manage which user can deploy which priorities

## pod disruption budget

- is used to e.g. enable zero downtime while a rolling update runs

## pod eviction

- only memory is important for eviction
- what is eviction
    - kubelet is evicting pods before linux `oom killer` kills processes (on near maximum memory usage)
    - if pods are spinned up too fast, eviction will not used
    - processes killed by oom killer are listed under `kubectl describe node`
    - low priority for evictions are pods with ressource usage less than the requested memory

## init container

> <https://github.com/aserowy/k8sworkshop/blob/master/Pods/pod-init-hook.yaml>

- init container are executed before ?
- these containers can be used to set up the environment before a pod is started
- thus you can
    - copy statics
    - manage dependencies (e.g. loop till db is ready)
    - spin up services
