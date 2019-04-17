## AKS configuration for Azure Cognitive services

# Computer Vision - Text Recognition

Instructions for accessing Azure Cognitive Services - Computer Vision - Text Recognition can be found in docs: https://docs.microsoft.com/en-us/azure/cognitive-services/computer-vision/computer-vision-how-to-install-containers

1. Create a Kubernetes secret named "acrsecret" in the cluster with Azure container registry private credentials

```
kubectl create secret docker-registry acrsecret --docker-server=containerpreview.azurecr.io --docker-username=<APP_ID> --docker-password=<APP_PASSWORD> --docker-email=<EMAIL>
```

2. Create an AKS deployment and a service as below
    ```
kubectl apply -f text-recognition-k8s.yaml
    ```

Note: 

By default, AKS service is exposed as ClusterIP. 
In case if the service needs to be exposed outside of the cluster to public, use type: LoadBalancer for the service.
If the service needs to be exposed outside of cluster but internal to Organization, Internal load balancer can be created as per doc: https://docs.microsoft.com/en-us/azure/aks/internal-lb
