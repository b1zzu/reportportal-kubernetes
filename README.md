# ReportPortal Kubernetes

This project is inspired by https://github.com/reportportal/kubernetes but uses kustomize instead of helm.

https://minikube.sigs.k8s.io/docs/handbook/addons/ingress-dns/

## Deployment

> Note: Jump to the minikube tutorial if you want to deploy it locally to http://reportportal.test

Prerequisites:

* [kubectl](https://kubectl.docs.kubernetes.io/)
* [ingress-nginx](https://github.com/kubernetes/ingress-nginx)

Deploy as it is to the `reportportal` namespace:

```shell
kubectl apply -k .
```

## Uninstall

```shell
kubectl delete namespace reportportal
```

## Kustomize

As this is a kustomize project it can be extend and kustomize further.

You can either fork this project, or create your own project and use this project as a resource.

If you want to use this project as a resource and overwrite only the parts you want create your `kustomization.yml` like
this:

```kustomization.yml
resources:      
 - github.com/b1zzu/reportportal-kubernetes?ref=v5.7.3
```

## Minikube

1. Start minikube

   ```shell
   minikube start
   ```

2. Install ingress and ingress-dns addons

   ```shell
   minikube addons enable ingress
   minikube addons enable ingress-dns
   ```

3. Deploy ReportPortal

   ```shell
   minikube kubectl apply -k .
   ```

4. Add the `minikube ip` as a DNS server: https://minikube.sigs.k8s.io/docs/handbook/addons/ingress-dns/#installation

5. Open http://reportportal.minikube.local/
