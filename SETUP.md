`k delete namespaces erpnext --force`

`k create namespace erpnext`

`kubens erpnext`

**Enable createSite,change domain name**

`helm repo add frappe https://helm.erpnext.com`

`helm install frappe-bench -n erpnext -f custom-values.yaml frappe/erpnext`

`helm template frappe-bench -n erpnext frappe/erpnext -f custom-values.yaml -s templates/job-create-site.yaml > create-new-site-job.yaml`


`kubectl apply -f create-new-site-job.yaml`

`k get pod`

`k logs frappe-bench-erpnext-new-site-20240424140450-jgtrn`

`k logs frappe-bench-mariadb-0 -f`

`k get pod`

`kubectl apply -f create-new-site-job.yaml`

`k get pod`

**Enable Ingress in custom-values.yaml file**

`helm template frappe-bench -n erpnext frappe/erpnext -f custom-values.yaml -s templates/ingress.yaml > ingress.yaml`

```bash
helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
helm repo update
helm install nginx-ingress ingress-nginx/ingress-nginx
```

`k apply -f ingress.yaml`

`k get svc`

`k get ingress`


```
aes.erpnext.com
user: Administrator
password: changeit
```

[ERP-NEXT](https://github.com/frappe/helm/tree/main/erpnext#migrate-site)

