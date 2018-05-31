## **Helm Charts in a practical way** ##

  **What is Helm:** Helm uses a packaging format called charts. A chart is a collection of files that describe a related set of Kubernetes resources.
  
  **Java Analogy:** A JAR (Java ARchive) is a package file format typically used to aggregate many Java class files and associated metadata and resources (text, images, etc.) into one file for distribution.

	
	https://docs.helm.sh/developing_charts/
## **Pre-Requisites** ##


- **Bringing up Single node Kubernetes Cluster on aws**
	- N.Virginia: ami-2ab2b550 or Oregon: ami-9957ece1, Minimum t2.medium, allow all TCP Inbound rules
	- ssh -i "xxx.pem" ubuntu@<Public-IP>
	- sudo su
	- ./init_master.sh
	- kubectl taint nodes --all node-role.kubernetes.io/master-
- **Setting up Helm on Kubernetes**
- 
	- curl https://raw.githubusercontent.com/kubernetes/helm/master/scripts/get > get_helm.sh
	- chmod 700 get_helm.sh
    - ./get_helm.sh
    - kubectl create clusterrolebinding permissive-binding --clusterrole=cluster-admin --user=admin --user=kubelet --group=system:serviceaccounts  

- **Helm Structure**
-
	https://docs.helm.sh/
	https://docs.bitnami.com/kubernetes/how-to/create-your-first-helm-chart/

## **Application without Helm chart - WordPress Example** ##
- Creating Application
	- Database
		- kubectl create secret generic mysql-pass –from-literal=password=YOUR_PASSWORD
		- kubectl create -f mysql-pv.yaml
		- kubectl create -f mysql-pvc.yaml
		- kubectl create -f mysql-svc.yaml
		- kubectl create -f mysql-deployment.yaml
	- Apache
		- kubectl create -f wp-pv.yaml
		- kubectl create -f wp-pvc.yaml
		- kubectl create -f wp-svc.yaml
		- kubectl create -f wp-deployment.yaml

- Deleting Application
	- kubectl delete deploy/wordpress
	- kubectl delete deploy/wordpress-mysql
	- kubectl delete svc/wordpress
	- kubectl delete svc/wordpress-mysql
	- kubectl delete secret mysql-pass

## **Application with Helm Chart - Wordpress Example** ##
- Creating Application
	- Helm install wordpress --name=wp
- Deleting the Application
	- Helm delete wp --purge

## **Helm Concepts** ##
Helm is a tool that streamlines installing and managing Kubernetes applications.
Think of it like apt/yum/homebrew for Kubernetes.

- Helm has two parts: a client (`helm`) and a server (`tiller`)
- Tiller runs inside of your Kubernetes cluster, and manages releases (installations)
  of your charts.
- Helm runs on your laptop, CI/CD, or wherever you want it to run.
- Charts are Helm packages that contain at least two things:
  - A description of the package (`Chart.yaml`)
  - One or more templates, which contain Kubernetes manifest files
- Charts can be stored on disk, or fetched from remote chart repositories
  (like Debian or RedHat packages)

