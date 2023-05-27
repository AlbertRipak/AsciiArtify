<a href="https://argo-cd.readthedocs.io/en/stable/">Argo CD</a> — це декларативний інструмент безперервної доставки GitOps для Kubernetes

Для того щоб розгорнути в локальному середовищі Argo CD, будемо використовувати k3d.
Інструкцію для налаштування k3d можна отримати в файлі <a href="https://github.com/AlbertRipak/AsciiArtify.git">README.md</a>.

# Create cluster
PS > k3d cluster create demo

PS > k3d cluster list
NAME   SERVERS   AGENTS   LOADBALANCER
demo   1/1       0/0      true
PS > kubectl create namespace argocd
PS > kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
PS > kubectl port-forward -n argocd svc/argocd-server 8080:443
PS > kubectl get secret argocd-initial-admin-secret -n argocd -o yaml
# Change the password from the yaml file to your password
PS > echo TkR4NUM5eEk0UWpOTUFGVw== | base64 -d