kubectl create secret generic mysql-pass –from-literal=password=YOUR_PASSWORD
kubectl create -f mysql-deployment.yaml
kubectl create -f Wordpress-apache.yaml
