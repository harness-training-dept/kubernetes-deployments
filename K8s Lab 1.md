# Basic Kubernetes Deployments Using Harness #

## Lab 1 - Familiarizing yourself with the training environment.


Each student has a dedicated single-server Kubernetes cluster based on upstream K8s and Centos. You will run your deployments on this server throughout the rest of the training. It's basically just a K8s master node with plenty of resources and the master taint removed so you can run non-admin workloads on it. 

**Steps:**

1: SSH in to your training server. Your instructor will have given you the IP address and the password on the lab sheet handed out at the start of class. 

````ssh centos@<training server IP>````

2. Examine your kubernetes environment. kubectl is installed and configured for the centos user. Run a few kubectl commands to get to know your install.

````kubectl get pods -n kube-system````

````kubectl get nodes````

````kubectl get ns````

3. Leave your SSH session open and go on to Lab 2.

## Lab 2 - Install the Harness Kubernetes Delegate

We need to install the Harness Kubernetes delegate on your training cluster. Download the installation yamls from the Harness App then install it. 

**Steps:**

1. Log in to https://app.harness.io with the login credentials provided on the student lab handout.

2. Navigate to the yaml download by following this path: Setup -> Harness Delegates -> Download Delegate -> Kubernetes Yaml. That will kick off a download of the tar.gz'ed yaml file to your local workstation. 

3. scp the downloaded file to your training server. 

````scp ./harness-delegate-kubernetes.tar.gz centos@<training server IP>:/home/centos/.````

Or you can also just unzip the file locally and then copy and paste the contents of harness-delegate.yaml to the same file name on your training server. 

4. If necessary ssh back in to your training server and run the following commands to unzip the yaml and then install the delegate:

````tar zxvf ./harness-delegate-kubernetes.tar.gz````

````kubectl apply -f ./harness-delegate-kubernetes/harness-delegate.yaml````
