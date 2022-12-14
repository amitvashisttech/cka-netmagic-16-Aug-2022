#### Second Part: Time for Restrictive Policy

#### Prereq:

#### Step 0: Enable PodSecurityPolicy Admission Controller:
```sh
nano /etc/kubernetes/manifests/kube-apiserver.yaml
```
```sh
--enable-admission-plugins=PodSecurityPolicy
```
```sh
watch kubectl get pods -n kube-system
```






#### Step 1 - Create Restrictive PSP:
```sh
nano restrictive-psp.yaml
```
```sh
apiVersion: policy/v1beta1
kind: PodSecurityPolicy
metadata:
  name: restrictive-psp
  annotations:
    seccomp.security.alpha.kubernetes.io/allowedProfileNames: '*'
spec:
  privileged: false
  allowPrivilegeEscalation: true
  allowedCapabilities:
  - '*'
  volumes:
  - '*'
  hostNetwork: true
  hostPorts:
  - min: 0
    max: 65535
  hostIPC: true
  hostPID: true
  runAsUser:
    rule: 'RunAsAny'
  seLinux:
    rule: 'RunAsAny'
  supplementalGroups:
    rule: 'RunAsAny'
  fsGroup:
    rule: 'RunAsAny'
```
```sh
kubectl apply -f restrictive-psp.yaml
```
#### Step 2 - Create Cluster Role Restrictive Policy:
```sh
nano restrictive-psp-cluster-role.yaml
```
```sh
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRole
metadata:
  name: restrictive-cluster-role
rules:
- apiGroups: ['policy']
  resources: ['podsecuritypolicies']
  verbs:     ['use']
  resourceNames:
  - restrictive-psp
```
```sh
kubectl apply -f restrictive-psp-cluster-role.yaml
```
#### Step 3 - Rolebinding of no-priveleged cluster role in default namespace:
```sh
nano restrictive-psp-rolebind.yaml
```sh
apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
  name: restrictive-role-bind
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: ClusterRole
  name: restrictive-cluster-role
subjects:
  - kind: Group
    apiGroup: rbac.authorization.k8s.io
    name: system:authenticated
```
```sh
kubectl apply -f restrictive-psp-rolebind.yaml
```
### Till now, the cluster role and cluster role binding taking effect.

#### Step 4 - Restrict the permissive policy to a single namespace:
```sh
nano permissive-rolebind.yaml
```
```sh
apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
  name: permissive-rolebind
  namespace: kube-system
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: ClusterRole
  name: permissive-cluster-role
subjects:
  - kind: Group
    apiGroup: rbac.authorization.k8s.io
    name: system:authenticated
```
```sh
kubectl apply -f permissive-rolebind.yaml
```

#### Step 5 - Verification (Should Work):
```sh
su - john
```
```sh
nano privileged.yaml
```
```sh
apiVersion: v1
kind: Pod
metadata:
  name: privileged
spec:
  containers:
  - image: nginx
    name: demo-pod
    securityContext:
      privileged: true
```
```sh
kubectl apply -f privileged.yaml
```



#### Step 6 - Delete Cluster Level Role Binding:
```sh
kubectl delete clusterrolebinding permissive-psp-cluster-bind
```
#### Step 7 - Verification(Should Not work):
```sh
su - john
```
```sh
nano privileged.yaml
```
```sh
apiVersion: v1
kind: Pod
metadata:
  name: privileged
spec:
  containers:
  - image: nginx
    name: demo-pod
    securityContext:
      privileged: true
```
```sh
kubectl apply -f privileged.yaml
```

```
john@kmaster1:~$ kubectl apply -f privileged.yaml
Error from server (Forbidden): error when creating "privileged.yaml": pods "privileged" is forbidden: unable to validate against any pod security policy: [spec.containers[0].securityContext.privileged: Invalid value: true: Privileged containers are not allowed]
john@kmaster1:~$
```
