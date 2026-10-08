---
title: CKA Exam Notes and Experience — February 2023
date: 2023-02-04 11:18:40
tags: [CKA, Certification]
categories: CKA
---

### View resources

- Use `k api-resources ` to get the names of Kubernetes resources.

### ETCD backup and restore

- endpoint?
- when restore, change etcd files location in `hostPath`
  `vi /etc/kubernetes/etcd.yaml`

### Monitoring and logging

- Metrics Server provides CPU and memory metrics: `k top nodes`, `k top pods —containers=true`.
- Use crictl commands to inspect logs and containers.
- To stream service logs, use `journalctl -u kubelet -f`.

### DaemonSet vs deployment vs StatefulSet

- A DaemonSet runs pods on all nodes, with at most one pod on each node. It is suitable for system-level applications such as log collection and resource monitoring; for example, Kube-proxy.
- A StatefulSet is similar to a ReplicaSet, but it can manage pod startup order and assigns each pod a unique identity to preserve its state.

### podAntiAffinity

- Use topologySpreadConstraints to run workloads only on worker nodes.
- With requiredDuringSchedulingIgnoredDuringExecution, the scheduler can schedule a pod only when the rule is satisfied. This is similar to nodeSelector, but its syntax is more expressive.
- Node Affinity.

### Ephemeral volumes

- emptyDir, which is erased when a pod is removed.

### Service CIDR range—> static-pod, kube-apiserver.yaml

- `cat /etc/kubernetes/manifests/kube-apiserver.yaml | grep range`
- /etc/kubernetes/manifests/kube-apiserver.yaml : --service-cluster-ip-range
- /etc/kubernetes/manifests/kube-controller-manager.yaml : --service-cluster-ip-range

### Upgrade a cluster

`kubeadm version`
`kubelet version`
`service kubelet status`
`systemctl daemon-reload && systemctl restart kubelet`

Drain node01. A forceful drain of the node will delete any pod that is not part of a ReplicaSet.
Run kubectl cordon node01. This ensures that no new pods are scheduled on this node, while existing pods are not affected.

### Add a node to the cluster

Use kubeadm token create to generate the node join command.

1. On the control-plane node, run `kubeadm token create --print-join-command`.
2. On the worker node, execute the output from the command above.

### Certificate

- View certificate details: `openssl x509  -noout -text -in ./server.crt`.
- Check certificate expiration with the `kubeadm` command: `kubeadm certs check-expiration`.
- Renew the API server certificate: ` kubeadm certs renew api-server`.

### Networking (CNI plugin)

- The default path is /etc/cni/net.d/.
- The CoreDNS deployment is in kube-system: `kubectl -n kube-system get pod`.
  Kube-scheduler, kube-scheduler.yaml

### Kubeconfig

- Cluster and context information is stored in ~/.kube/config.

### Manual scheduling

- If there is no scheduler in kube-system, add `nodeName` to pod.yaml; otherwise, the pod remains pending.

### Troubleshooting

- `sudo journalctl -u kubelet`

## Exam experience

### 5/2/2023

The exam check-in process was smoother than AWS and easy to use.

1. The exam questions were much simpler than the difficult mock exam. The real exam had only about one-third as many questions as the mock exam.
2. My only regret was using a laptop for convenience. It was harder to work quickly, and my vision became blurry. Next time, I will choose a large monitor.
3. Exam topics:
   - ETCD backup and restore
   - multiple containers pod
   - cluster upgrade
   - cluster troubleshooting
   - clusterrole, rolebinding and serviceaccount
   - PV, PVC, pod

### 6/2/2023

Twenty-four hours later, after receiving the result, I learned that I had failed the exam. I missed some small details during the exam, and I still had some knowledge gaps.

---

## 中文版

### 查看资源

- 使用 `k api-resources ` 获取 Kubernetes 资源名称。

### ETCD 备份与恢复

- endpoint 是什么？
- 恢复时，在 `hostPath` 中修改 etcd 文件的位置：
  `vi /etc/kubernetes/etcd.yaml`

### 监控与日志

- Metrics Server 提供 CPU 和内存指标：`k top nodes`、`k top pods —containers=true`。
- 使用 crictl 命令检查日志和容器。
- 使用 `journalctl -u kubelet -f` 持续查看服务日志。

### DaemonSet、Deployment 与 StatefulSet

- DaemonSet 在所有节点上运行 Pod，每个节点上最多运行一个 Pod。它适合日志收集、资源监控等系统级应用，例如 Kube-proxy。
- StatefulSet 与 ReplicaSet 类似，但它可以管理 Pod 的启动顺序，并为每个 Pod 分配唯一标识以保留其状态。

### podAntiAffinity

- 使用 topologySpreadConstraints 让工作负载仅在 worker 节点上运行。
- 使用 requiredDuringSchedulingIgnoredDuringExecution 时，只有满足规则，调度器才能调度 Pod。此功能类似于 nodeSelector，但语法表达能力更强。
- Node Affinity。

### 临时卷

- emptyDir 会在 Pod 被删除时清空。

### Service CIDR 范围—> static-pod、kube-apiserver.yaml

- `cat /etc/kubernetes/manifests/kube-apiserver.yaml | grep range`
- /etc/kubernetes/manifests/kube-apiserver.yaml：--service-cluster-ip-range
- /etc/kubernetes/manifests/kube-controller-manager.yaml：--service-cluster-ip-range

### 升级集群

`kubeadm version`
`kubelet version`
`service kubelet status`
`systemctl daemon-reload && systemctl restart kubelet`

对 node01 执行 drain。强制 drain 节点会删除所有不属于 ReplicaSet 的 Pod。
运行 kubectl cordon node01。这可以确保不再有新 Pod 被调度到该节点，同时不会影响现有 Pod。

### 向集群添加节点

使用 kubeadm token create 生成节点加入命令。

1. 在控制平面节点上运行 `kubeadm token create --print-join-command`。
2. 在工作节点上执行上述命令的输出。

### 证书

- 查看证书详细信息：`openssl x509  -noout -text -in ./server.crt`。
- 使用 `kubeadm` 命令检查证书到期时间：`kubeadm certs check-expiration`。
- 更新 API server 证书：` kubeadm certs renew api-server`。

### 网络（CNI 插件）

- 默认路径为 /etc/cni/net.d/。
- CoreDNS Deployment 位于 kube-system 中：`kubectl -n kube-system get pod`。
  Kube-scheduler、kube-scheduler.yaml

### Kubeconfig

- 集群和 context 信息存储在 ~/.kube/config 中。

### 手动调度

- 如果 kube-system 中没有 scheduler，请在 pod.yaml 中添加 `nodeName`；否则 Pod 会保持 pending 状态。

### 故障排查

- `sudo journalctl -u kubelet`

## 考试经历

### 5/2/2023

考试签到流程比 AWS 更顺畅，也很容易使用。

1. 考试题目比高难度模拟考试简单得多。正式考试的题量大约只有模拟考试的三分之一。
2. 我唯一后悔的是为了方便使用了笔记本电脑。这样更难快速操作，而且眼睛会变得模糊。下次我会选择大显示器。
3. 考试主题：
   - ETCD 备份与恢复
   - 多容器 Pod
   - 集群升级
   - 集群故障排查
   - clusterrole、rolebinding 和 serviceaccount
   - PV、PVC、Pod

### 6/2/2023

二十四小时后，我收到考试结果，得知自己没有通过。我在考试时遗漏了一些小细节，也仍然存在一些知识盲点。
