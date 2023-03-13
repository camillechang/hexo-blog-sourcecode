---
title: cks-cluster
date: 2023-03-01 15:08:00
tags:
---

## Install k8s cluster on ubuntu

- Install three ubuntu servers, one is master, the other two are workers
- Config /etc/hosts and /etc/hostname

```
cat << EOF | sudo tee /etc/modules-load.d/containerd.conf
overlay
br_netfilter
EOF

sudo modprobe overlay
sudo modprobe br_netfilter

```

```
cat <<EOF | sudo tee /etc/sysctl.d/99-kubernetes-cri.conf
net.bridge.bridge-nf-call-iptables  = 1
net.ipv4.ip_forward                 = 1
net.bridge.bridge-nf-call-ip6tables = 1
EOF

```

- reload system config
  `sudo sysctl --system`
- Install containerd
  `sudo apt-get update && sudo apt-get -y install containerd`
- Create a directory and configure containerd

```
sudo mkdir -p /etc/containerd
sudo containerd config default | sudo tee /etc/containerd/config.toml
sudo systemctl restart containerd

sudo swapoff -a
sudo apt-get install -y apt-transport-https curl
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
```

- Config repository
  `echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee /etc/apt/sources.list.d/kubernetes.list`
- Update apt package index, install kubelet, kubeadm and kubectl, and make sure not auto update

```
sudo apt-get update
sudo apt-get install -y kubelet kubeadm kubectl
sudo apt-mark hold kubelet kubeadm kubectl
```

```
sudo kubeadm init --pod-network-cidr 192.168.0.0/16 --kubernetes-version 1.26.2

  mkdir -p $HOME/.kube
  sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
  sudo chown $(id -u):$(id -g) $HOME/.kube/config
```

- Install network plugin Calico
  https://docs.tigera.io/calico/3.25/getting-started/kubernetes/self-managed-onprem/onpremises

- Join worker node, then apply the output to other worker nodes
  `kubeadm token create --print-join-command`
- In master node, `kubectl get nodes`

### error:

1. ![kubeadm error](../../imgs/cluster-error1.jpg) Install docker, https://docs.docker.com/engine/install/ubuntu/
   fix the error: https://forum.linuxfoundation.org/discussion/862825/kubeadm-init-error-cri-v1-runtime-api-is-not-implemented
