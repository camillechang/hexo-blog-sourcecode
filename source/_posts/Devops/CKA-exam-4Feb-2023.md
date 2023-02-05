---
title: CKA-exam-4Feb-2023
date: 2023-02-04 11:18:40
tags: [CKA, Certification]
categories: CKA
---

### View Resources

- `k api-resources ` get names of Kubernetes resources

### ETCD backup and restore

- endpoint?
- when restore, change etcd files location in `hostPath`
  `vi /etc/kubernetes/etcd.yaml`

### monitoring, logging

- Metrics-server(CPU, memory), `k top nodes`, `k top pods —containers=true`
- crictl commands, logs, containers
- To load logs of service `journalctl -u kubelet -f`

### DaemonSet vs deployment vs StatefulSet

- DaemonSet 所有 Nodes 上运行 pod,每个 Node 上最多只能运行一个 pod.适合一些系统层面的应用，例如日志收集、资源监, eg: Kube-proxy
- StatefulSet, StatefulSet 类似于 ReplicaSet，但是它可以处理 Pod 的启动顺序，为保留每个 Pod 的状态设置唯一标识

### podAntiAffinity •

- 仅在 worker 上运行 topologySpreadConstraints
- requiredDuringSchedulingIgnoredDuringExecution,调度器只有在规则被满足的时候才能执行调度。此功能类似于 nodeSelector， 但其语法表达能力更强。
- Node Affinity,

### 临时卷（Ephemeral Volume）

- emptyDir, which is erased when a pod is removed,

### Service CIDR range—> static-pod, kube-apiserver.yaml

- `cat /etc/kubernetes/manifests/kube-apiserver.yaml | grep range`
- /etc/kubernetes/manifests/kube-apiserver.yaml : --service-cluster-ip-range
- /etc/kubernetes/manifests/kube-controller-manager.yaml : --service-cluster-ip-range

### upgrade culster

`kubeadm version`
`kubelet version`
`service kubelet status`
`systemctl daemon-reload && systemctl restart kubelet`

drain node01, A forceful drain of the node will delete any pod that is not part of a replicaset.
kubectl cordon node01, This will ensure that no new pods are scheduled on this node and the existing pods will not be affected by this operation.

### add node to cluster

kubeadm token create， node join

1. controlplane node, `kubeadm token create --print-join-command`
2. Worker node, execute the output from the above

### Certificate

- view cert details `openssl x509  -noout -text -in ./server.crt`
- `kubeadm` command , `kubeadm certs check-expiration`
- Renew apiserver cert ,` kubeadm certs renew api-server`

### Networking (CNI plugin)

- default path /etc/cni/net.d/
- Coredns-deployment, //in kube-system `kubectl -n kube-system get pod`
  Kube-scheduler, kube-scheduler.yaml

### Kubeconfig

- cluster and context info, ~/.kube/config

### manually scheduling

- If there is no scheduler in kube-system, add `nodeName` in pod.yaml, otherwise pod status is pending.

### troubleshooting

- `sudo journalctl -u kubelet`

## Exam experience

5/2/2023, exam check in is more smooth than AWS and easy to use.

1. Exam questions are way simpler than the killer mock exam. Only 1/3 amount of questions of the mock one.
2. Only regret things is I use laptop for easy, it's more hard for me do things quick and my eyes get blur. Next time, I will choose big monitor.
3. Exam topics:
   - ETCD backup and restore
   - multiple containers pod
   - cluster upgrade
   - cluster troubleshooting
   - clusterrole, rolebinding and serviceaccount
   - PV, PVC, pod
