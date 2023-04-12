#### Create or update the kubeconfig

1. Create or update cubeconfig
```
aws eks update-kubeconfig --region region-code --name my-cluster
```

There can be multiple kubeconfigs. To set the default one:
```
export KUBECONFIG=$KUBECONFIG:~/.kube/config
```

