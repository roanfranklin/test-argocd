
### Requisitos

- git
- helm
- kubectl
- minikube, k3s, kind, EKS, GKE, AKS, etc...


### Install ArgoCD

```bash
kubectl create namespace argocd

kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

>Atenção:
>Os manifestos de instalação incluem recursos ClusterRoleBinding que fazem referência ao namespace argocd. Se você estiver instalando o Argo CD em um namespace diferente, certifique-se de atualizar a referência do namespace.

**Port-Forward**

```bash
kubectl -n argocd port-forward svc/argocd-server -n argocd 8080:443
```

http://localhost:8080

**Login: admin**

O login padrão é admin e uma senha aleatória será gerada. Para obtê-la, execute o seguinte comando em outro terminal:

```bash
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```

OBS.: Após logar, vocẽ pode e deve mudar a senha do admin, acessando a URL: https://localhost:8080/user-info?changePassword=true

