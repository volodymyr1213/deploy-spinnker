# deploy-spinnker


Upgrade tiller version from 2.11 to 2.14
Volodymyr Khomenko edited this page 39 minutes ago · 1 revision
Downloading tiller version 2.14

curl https://storage.googleapis.com/kubernetes-helm/helm-v2.14.0-linux-amd64.tar.gz > ./helm.tar.gz
tar -xvf ./helm.tar.gz
mv linux-amd64/* .
./helm version
Setting up tiller namespace and initializing the helm

kubectl create ns tiller
kubectl --namespace tiller create sa tiller
kubectl create clusterrolebinding tiller-custom --clusterrole cluster-admin --serviceaccount=tiller:tiller
./helm init --tiller-namespace=tiller --service-account tiller
If you would like to see tiller has been deployed or not you can run following command

kubectl get pods -n tiller
To be able to use helm 2.14 now you will need to specify --tiller-namespace=tiller

./helm ls --tiller-namespace=tiller
./helm version --tiller-namespace=tiller
