Learning Helm Charts in a practical way
  Helm uses a packaging format called charts. A chart is a collection of files that describe a related set of Kubernetes resources.
  Java Analogy: A JAR (Java ARchive) is a package file format typically used to aggregate many Java class files and associated metadata and resources (text, images, etc.) into one file for distribution.

Pre-Requisites
1. Bringing up Kubernetes Cluster
   a. N. Virginia: ami-2ab2b550 or Oregon: ami-9957ece1
   b. >= t2.medium, allow all TCP Inbound rules
   c. ssh as ubuntu user
   d. sudo su; ./init_master.sh
2. Setting up Helm on Kubernetes
   curl https://raw.githubusercontent.com/kubernetes/helm/master/scripts/get > get_helm.sh
   chmod 700 get_helm.sh
   ./get_helm.sh
   kubectl create clusterrolebinding permissive-binding --clusterrole=cluster-admin --user=admin --user=kubelet --group=system:serviceaccounts  

Application without Helm chart - WordPress Example


Application with Helm Chart - Wordpress Example
