`creating a shell demo`

curl -o- [https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh](https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh) | bash
kubectl apply -f [https://k8s.io/examples/application/shell-demo.yaml](https://k8s.io/examples/application/shell-demo.yaml)
kubectl exec -it shell-demo -- /bin/bash

kubectl delete pod shell-demo

