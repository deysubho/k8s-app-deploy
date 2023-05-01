Prerequisites for deployment-
Update the system and install docker:
sudo apt update -y
sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker


Kubeadm installation(Both):
sudo curl -fsSLo /usr/share/keyrings/kubernetes-archive-keyring.gpg https://packages.cloud.google.com/apt/doc/apt-key.gpg
echo "deb [signed-by=/usr/share/keyrings/kubernetes-archive-keyring.gpg] https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee /etc/apt/sources.list.d/kubernetes.list
sudo apt update -y
sudo apt install kubeadm=1.20.0-00 kubectl=1.20.0-00 kubelet=1.20.0-00 -y


To connect with the cluster(for the master node):
sudo su
kubeadm init
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config
kubectl apply -f https://github.com/weaveworks/weave/releases/download/v2.8.1/weave-daemonset-k8s.yaml
kubeadm token create --print-join-command


To connect with the cluster(for the Worker node):
sudo su
kubeadm reset pre-flight checks
(*Paste the Join command on worker node and append `--v=5` at end*)
(*kubeadm token create --print-join-command*)


To verify cluster connection:-
kubectl get nodes


Let's dive into our deployment------>
1. Clone the repo:-
2. create the docker file
3. Check whether the nodes are ready or not!!
4. Check whether the pod is running or not: -
5. Run the taskmaster yml file:-
6. Scale the taskmaster:-
7.Run the taskmaster-svc.yml file
8 . Run the Mongo persistent volume file:-
9. Claim persistent volume:-
10 . Run the Mongo yml file:-
11. Run the Mongo svc file:-
15. Check whether the clusters are running or not.
16 . Change the inbound rules.

Finally, just copy the public IP of the worker node and check in Postman whether it's running on not!
!!!!!!!!!YOU DID IT!!!!!!!!!!!!!!!!!!

Thank you!

Follow for more!

