# kubernetes-cluster
This repo contains step to create a simple Kubernetes cluster

* Login to https://labs.play-with-k8s.com
* Create 3 instances (1 Master, 2 Worker Nodes)
* Now configure master
  * kubeadm init --apiserver-advertise-address $(hostname -i)
* Now to start using kubectl run below commands
  * mkdir -p $HOME/.kube
  * sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
  * sudo chown $(id -u):$(id -g) $HOME/.kube/config
* Now configure networking
  * kubectl apply -n kube-system -f "https://cloud.weave.works/k8s/net?k8s-version=$(kubectl version | base64 |tr -d '\n')"
* Now execute below command in each worker node to join the Kubernetes cluster
  *  kubeadm join 192.168.0.8:6443 --token lmnc8w.6v8mih12m2vmptr7 
             --discovery-token-ca-cert-hash sha256:dbeba2f61cc3c894b58fd7a063d020b2734b5c11d22421321a7bdd16266c06d7
             
* Now both the worker nodes joined Kubernetes cluster. Check it using command
  * <b>kubectl get nodes</b>  
   ![Screenshot](img/get_nodes.png)
* Now deploy sample nginx application
  * <b>kubectl apply -f https://raw.githubusercontent.com/kubernetes/website/master/content/en/examples/application/nginx-app.yaml</b>
  * <b>kubectl get pods</b>  
   ![Screenshot](img/get_pods.png)
  


