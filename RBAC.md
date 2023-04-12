### Basics

**ApiVersion**:  **rbac.authorization.k8s.io/v1**

**ServiceAccount**: Used when other k8 component or pod proxess needs access to the cluster or AWS.
- You can map the service account to an AWS Identity and Access Management identity to grant that access.


#### Role and RoleBinding
Basic Example of a Role:
```yml
kind: Role
apiVersion: rbac.authorization.k8s.io/v1
metadata:
  namespace: dev
  name: PodsReaderRole
rules:
- apiGroups: ["*"]
  resources: ["*"]
  verbs: ["Read"]
```

Basic Example of RoleBinding:

```yml
kind: RoleBinding
apiVersion: rbac.authorization.k8s.io/v1
metadata:
  name: listPodsRoleBinding
  namespace: dev
subjects:
- kind: ServiceAccount
  name: podsAccessSA
  apiGroup: ""
roleRef:
  kind: Role
  name: PodsReaderRole
  apiGroup: ""
```
> We can Bind Role to a Principal created from different namespace as well.

> But, ClusterRole is not namespaced. But if it is binded using RoleBinding, it can be namespaced.

### Differences between Role and ClusterRole

| Role  | ClusterRole  |
|---|---|
| The permissions in the role are limited in a single namespace.  |  The permissions are across the namespace.   |



##### Summary:
- Roles and role bindings must exist in the same namespace.
- Role bindings can exist in separate namespaces to service accounts.
- Role bindings can link cluster roles, but they only grant access to the namespace of the role binding.
- Cluster role bindings link accounts to cluster roles and grant access across all resources.
Cluster role bindings can not reference roles
[Octopus helpful link](https://octopus.com/blog/k8s-rbac-roles-and-bindings)