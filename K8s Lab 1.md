# Basic Kubernetes Deployments Using Harness #

## Lab 1 - Familiarizing yourself with the training environment.


Each student has a dedicated single-server Kubernetes cluster based on upstream K8s and Centos. You will run your deployments on this server throughout the rest of the training. It's basically just a K8s master node with plenty of resources and the master taint removed so you can run non-admin workloads on it. 

**Steps:**

1: SSH in to your training server. Your instructor will have given you the IP address and the password on the lab sheet handed out at the start of class. 

````ssh centos@<training server IP>````

2. Examine your kubernetes environment. kubectl is installed and configured for the centos user. Run a few kubectl commanduds to get to know your install.

````kubectl get pods -n kube-system````

````kubectl get nodes````

````kubectl get ns````

3. Leave your SSH session open and switch over to your Chrome web browser and login to https://app.harness.io with the user name and password from your lab sheet. 

4. Click around and explore the GUI. The main dashboard page will be more exciting later in the class once you and your fellow students have done a few more deployments. Please note depending on the user role you have in your organization's Harness implementation you may not have access to the menus and settings you see here in our training setu5p. 

5. We will be visiting the Setup menu most often during class. Click in there and explore the different connectors and setting options. 

6. Ask your instructor if you don't understand the use of any configuration or dashboard.

## Lab 2 - Install the Harness Kubernetes Delegate

We need to install the Harness Kubernetes delegate on your training cluster. Download the installation yamls from the Harness App then install it. 

**Steps:**

1. Point your Chrome web browser to https://app.harness.io and login with the credentials provided on the student lab handout.

2. Navigate to the Delegate download by following this path: Setup -> Harness Delegates -> Download Delegate -> Kubernetes Yaml. Fill out the form to give your delegate a name. This is how it will be listed in the Harness GUI, so please be sure to include your name / student number so you can easily identify it later. Leave the profile line blank. 

![Delegate Setup](/images/delegate_setup-2.png)

Click Submit and that will kick off a download of the tar.gz file to your local workstation. 

3. scp the downloaded file to your training server. 

````scp ./harness-delegate-kubernetes.tar.gz centos@<training server IP>:/home/centos/.````

Or you can also just unzip the file locally and then copy and paste the contents of harness-delegate.yaml to the same file name on your training server. 

4. If necessary ssh back in to your training server and run the following commands to unzip the yaml and then install the delegate:

````tar zxvf ./harness-delegate-kubernetes.tar.gz````

````kubectl apply -f ./harness-delegate-kubernetes/harness-delegate.yaml````

_Note if you did the copy and paste version of step 3, you only need to run the kubectl command above._

4. Verify that the Delegate is installed:

````kubectl get pods -n harness-delegate````

Once that command completes go back to the app.harness.io GUI and go to Setup -> Harness Delegates. There you should see your delegate as well as those of your fellow students. If you don't see it and the pod is ready on the command line, hit refresh on the browser - it will show.

![Delegate View](/images/delegate_view.png)

Feel free to add tags as in the picture. In the "real" world Delegate Tags are used to identify Delegates for both deployments and for Delegate specific configurations. Now that the Delegate is installed we can start to configure our first Deployment in subsequent labs. 

## Lab 3 - Setting Up Kubernetes Cloud Provider

## Lab 4 - Building Your First Kubernetes Deployment

**Steps**

1. Switch or login to your Harness GUI. Navigate to Setup at the top left. First we will need to setup an Application for our deployment. Then click + Add Application. Be sure to include your name in your Application name to find it easily.

![Application_name](/images/application_nm.png)

Click submit. Harness will create your Application and then take you its components. 

2. Now that we have an Application we can start to build our deployment. First up lets setup the Service we will be deploying. Click on Services then click on Add Service. Give your service a name and description, then make sure Deployment Type is set to Kubernetes. 
