Tasks:
Q1. Create a Kubernetes cluster on GCP (GCP gives free credits on signup so those should suffice for this
exercise). If possible share a script / code which can be used to create the cluster.
A1. gcloud command to create a kubernetes cluster in GCP
Types of clusters
Zonal clusters
Regional cluster
Private cluster
Alpha cluster

Creating a single-zone cluster:
gcloud container clusters create example-cluster --zone us-central1-a --node-locations us-central1-a

Creating a multi-zone cluster
gcloud container clusters create example-cluster --zone us-central1-a --node-locations us-central1-a,us-central1-b,us-central1-c

Regional clusters
gcloud container clusters create example-cluster --region us-west1
gcloud container clusters create example-cluster --num-nodes 2 --region us-west1

Q2. Install nginx ingress controller on the cluster. For now, we consider that the user will add public IP of
ingress LoadBalancer to their /etc/hosts file for all hostnames to be used. So do not worry about DNS
resolution.


Q3. On this cluster, create namespaces called staging and production.
A3. 


Q4. Install guest-book application on both namespaces.
A4. 


Q5. Expose staging application on hostname staging-guestbook.mstakx.io
A5. Apologies!!  I was not able to create GCP account with my debit/credit card, may be I have used it many times.
As of now I am able to host it locally but DNS mapping with the service is pending.

Application running on 2 different environment.

Application GUI screen-shot for staging


Application GUI screen-shot for production



Q6. Expose production application on hostname guestbook.mstakx.io
A6. DNS mapping is pending, since I am not able to create GCP account so I have used minikube.

Q7. Implement a pod autoscaler on both namespaces which will scale frontend pod replicas up and down
based on CPU utilization of pods.
A7.
Created horizontal pod autoscaling for production and stage.
For production


For Staging


Mini pod=2
Max pod=5

CPU=50%





Q8. Write a script which will demonstrate how the pods are scaling up and down by increasing/decreasing load
on existing pods.
A8.
For generating load, I have installed apache bench.

Script for production
#!/bin/bash
while true
do
bench-rest -n 200 -c 20 http://192.168.99.112:30170/
sleep 60
Done

Similarly for Staging

#!/bin/bash
while true
do
bench-rest -n 200 -c 20 http://192.168.99.112:30170/
sleep 60
Done


One pod got autoscales after 200 tps


Output of the script:

Q9. Write a wrapper script which does all the steps above. Mention any pre-requisites in the README.md at
the root of your repo.
The evaluator will proceed by going over the steps mentioned in the README. So try to make this as
automated as possible.
In the context of above test, please explain the following:
What was the node size chosen for the Kubernetes nodes? And why?
What method was chosen to install the demo application and ingress controller on the cluster, justify the
method used
What would be your chosen solution to monitor the application on the cluster and why?
What additional components / plugins would you install on the cluster to manage it better?


