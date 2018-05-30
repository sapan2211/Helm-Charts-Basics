## **Helm Charts in a practical way** ##

  **What is Helm:** Helm uses a packaging format called charts. A chart is a collection of files that describe a related set of Kubernetes resources.
  
  **Java Analogy:** A JAR (Java ARchive) is a package file format typically used to aggregate many Java class files and associated metadata and resources (text, images, etc.) into one file for distribution.

## **Pre-Requisites** ##



- **Bringing up Kubernetes Cluster on aws**
    1. N. Virginia: ami-2ab2b550 or Oregon: ami-9957ece1
	2. t2.medium, allow all TCP Inbound rules
    3. ssh as ubuntu user
    4. sudo su; ./init_master.sh
- **Setting up Helm on Kubernetes**
    1. curl https://raw.githubusercontent.com/kubernetes/helm/master/scripts/get > get_helm.sh
    3. chmod 700 get_helm.sh
    4. ./get_helm.sh
    5. kubectl create clusterrolebinding permissive-binding --clusterrole=cluster-admin --user=admin --user=kubelet --group=system:serviceaccounts  

## **Application without Helm chart - WordPress Example** ##


## **Application with Helm Chart - Wordpress Example** ##
