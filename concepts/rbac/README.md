## Create User Certificate

[1] Generate private key

```
openssl genrsa -out testuser.key 2048
```

[2] Generate CSR

```
openssl req -new -key testuser.key -out testuser.csr -subj "/CN=testuser/O=testgroup"
```

[3] Generate CRT for CSR

```
openssl x509 -req -in testuser.csr -CA ~/.minikube/ca.crt -CAkey ~/.minikube/ca.key -CAcreateserial -out testuser.crt -days 500
```

[4] Set user entry in kubeconfig

```
k config set-credentials testuser --client-certificate=cert/testuser.crt --client-key=cert/testuser.key
```

Sample config:

```
users:
  user:
    client-certificate: ..\..\..\Github\kubernetes-examples\concepts\rbac\cert\testuser.crt
    client-key: ..\..\..\Github\kubernetes-examples\concepts\rbac\cert\testuser.key
```

[5] Set context entry in kubecongif

```
k config set-context testuser-context --cluster minikube --user=testuser
```

Sample config:

```
- context:
    cluster: minikube
    user: testuser
  name: testuser-context
```