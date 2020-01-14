# Basic Kubernetes Deployments Using Harness #

### Lab 1 - Familiarizing yourself with the training environment.


Each student has a dedicated single-server Kubernetes cluster based on upstream K8s and Centos. You will run your deployments on this server throughout the rest of the training. It's basically just a K8s master node with plenty of resources and the master taint removed so you can run non-admin workloads on it. 

Steps:

1: SSH in to your training server. Your instructor will have given you the IP address and the password on the lab sheet handed out at the start of class. 

````ssh centos@<training server IP>````

2. Examine your kubernetes environment. kubectl is installed and configured for the centos user. Run a few kubectl commands to get to know your install.

````kubectl get pods -n kube-system````

````kubectl get nodes````

````kubectl get ns````

3. 
