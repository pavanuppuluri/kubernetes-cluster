# kubernetes-cluster
This repo contains step to create a simple Kubernetes cluster

* Login to https://labs.play-with-k8s.com
* Create 3 instances (1 Master, 2 Worker Nodes)
* Now configure master
  * kubeadm init --apiserver-advertise-address $(hostname -i)
* Now to start kubectl run below commands
  * mkdir -p $HOME/.kube
  * sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
  * sudo chown $(id -u):$(id -g) $HOME/.kube/config
