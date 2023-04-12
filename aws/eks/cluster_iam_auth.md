### EKS IAM cluster authenication

![AWS DOCS](https://docs.aws.amazon.com/eks/latest/userguide/add-user-role.html)


### Notable points
- Check kubeconfig for the cluster name and username. If this user created cluster the user has access to eks with `system:master` role.


#### Find out the users already in cluster
 We can see which users have access to the cluster from the configMap **aws-auth**
```bash
kubectl describe -n kube-system configmap/aws-auth
```

#### About OIDC authentication

- Cannot disable the IAM authenticator
- OIDC authencator should have public endpoint.
- Does not work with self signed certs


##### Buitl cluster roles in EKS roles

```
kubectl get clusterroles | grep eks
```


#### How to bind k8 service account with IAM role
[AWS Docs Link](https://docs.aws.amazon.com/eks/latest/userguide/associate-service-account-role.html)