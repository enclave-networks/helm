# Nginx with Enclave sidecar

This `yaml` defines a single pod called `pod-with-sidecar-deployment` and injects two containers, a primary `nginx:1.7.9` container and an enclave sidecar container `enclavenetworks/enclave:latest`.

Note that this pod is not exposed for ingress traffic.

## Pod management

```
$ kubectl apply -f pod.yaml
$ kubectl delete -f pod.yaml
```

## Enclave connectivity

Until enclave supports auto-join keys, connect a terminal to the sidecar and run `enclave` to control connectivity.

```
kubectl exec --stdin --tty pod-with-sidecar-deployment-7cc5c988-gnrpz -c sidecar-container -- /bin/bash
```