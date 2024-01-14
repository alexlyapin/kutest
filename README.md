### Setup Minikube

Follow the [guide](https://minikube.sigs.k8s.io/docs/start/).

### Setup ArgoCD

Follow the [guide](https://argo-cd.readthedocs.io/en/stable/getting_started/).

### Mount models

```shell
minikube mount path_to_models:/mnt/models
```

### Update hosts file, adding:

- 127.0.0.1 mythrion.local
- 127.0.0.1 api.mythrion.local
- 127.0.0.1 argocd.mythrion.local
- 127.0.0.1 pgadmin.mythrion.local
- 127.0.0.1 rabbit.mythrion.local

### DB migrations

PostgreSQL should be forwarded to allow alembic access it:

```shell
kubectl port-forward svc/postgresdb 5432:5432
```

In the db_utils project, run:

```shell
alembic upgrade head
```
