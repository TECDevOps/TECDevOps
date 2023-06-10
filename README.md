# Rancher
## installation

1. Add the Helm Chart Repository
```sh
helm repo add rancher-stable https://releases.rancher.com/server-charts/stable
```
2. Create a Namespace for Rancher
```sh
create namespace cattle-system
```
3. Choose your SSL Configuration
Install cert-manager
# If you have installed the CRDs manually instead of with the `--set installCRDs=true` option added to your Helm install command, you should upgrade your CRD resources before upgrading the Helm chart:
```sh
kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.11.0/cert-manager.crds.yaml
```
# Add the Jetstack Helm repository
```sh
helm repo add jetstack https://charts.jetstack.io
```
# Update your local Helm chart repository cache
```sh
helm repo update
```
# Install the cert-manager Helm chart
```sh
helm install cert-manager jetstack/cert-manager \
  --namespace cert-manager \
  --create-namespace \
  --version v1.11.0
  ```
Once you’ve installed cert-manager, you can verify it is deployed correctly by checking the cert-manager namespace for running pods:
```sh
kubectl get pods --namespace cert-manager
```
5. Install Rancher with Helm and Your Chosen Certificate Option
helm install rancher rancher-stable/rancher \
  --namespace cattle-system \
  --set hostname=rancher.theeducloud.com \
  --set bootstrapPassword=admin

6. Verify that the Rancher Server is Successfully Deployed
kubectl get ns
kubectl get pods -n cattle-system
kubectl get service -n cattle-system
kubectl get ingress -n cattle-system
kubectl delete ingress rancher -n cattle-system
=================================================================================================================================================================================================
# commands
## Installation
```sh
helm repo add rancher-stable https://releases.rancher.com/server-charts/stable
create namespace cattle-system
kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.11.0/cert-manager.crds.yaml
helm repo add jetstack https://charts.jetstack.io
helm repo update
helm install cert-manager jetstack/cert-manager --namespace cert-manager --create-namespace --version v1.11.0
kubectl get pods --namespace cert-manager
helm install rancher rancher-stable/rancher --namespace cattle-system --set hostname=rancher.theeducloud.com --set bootstrapPassword=admin
# Verify
kubectl get ns
kubectl get pods -n cattle-system
kubectl get service -n cattle-system
kubectl get ingress -n cattle-system
```
=================================================================================================================================================================================================


