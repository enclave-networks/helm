# Nginx with Enclave sidecar

This `yaml` defines a single pod called `pod-with-sidecar-deployment` and injects two containers, a primary `nginx:1.7.9` container and an enclave sidecar container `enclavenetworks/enclave:latest`.

Note that this pod is not exposed for ingress traffic.

## Pod management

Set a valid `ENCLAVE_ENROLMENT_KEY` environment variable in your `pod.yaml` file and apply to your cluster.

```
$ kubectl apply -f deployment.yaml
$ kubectl delete -f deployment.yaml
```

## Sidecar

Using kubectl you can drop into a specific pod with a bash shell to maniulate the `enclave` agent inside that container if necessary.

```
kubectl exec --stdin --tty pod-with-sidecar-deployment-7cc5c988-gnrpz -c sidecar-container -- /bin/bash
```
