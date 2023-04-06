# Exercice Final Kubernetes

Build USER image

`docker build -t haryos/userapi users-api/`

Build AUTH image

`docker build -t haryos/authapi auth-api/`

Build TASKS image

`docker build -t haryos/tasksapi tasks-api/`

Push images

`docker push hanryos/[image-name]`

### Comment fonctionne le projet ?

##### Lancer les api

Appliquer l'environemment

`
kubectl apply -f .\environment.yml
`

Lancer l'api USER

`
kubectl apply -f .\user-deployment.yml,.\user-service.yml
`

Lancer l'api AUTH

`
kubectl apply -f .\auth-deployment.yml,.\auth-service.yml
`

Lancer l'api TASK

`
kubectl apply -f .\task-deployment.yml,.\task-service.yml
`
### Tester les api

Lancer les services minikube sur trois terminaux différents

`
minikube service ["Nom du service souhaité"]
`

Dans un client REST effectuer un POST sur l'addresse du service USER au /signup avec un bearer token "abc" et comme corps de la requête un JSON ayant pour structure:

```json
{
  "email": "test@example.com",
  "password": "password"
}
```

Dans le cas où l'API fonctionne, on aura une réponse ayant pour code de statut un **2xx** une réponse sous la forme d'un JSON, confirmant le bon fonctionnement de l'API.



Pour tester l'API des tâches, dans un client REST, réaliser un POST vers l'addresse du service TASK avec un Bearer token ayant pour valeur "abc" et comme corps de la requête un JSON ayant pour structure: 

```json
{
  "text": "Valeur de text",
  "title": "Valeur de title"
}
```

Le bonfonctionnement de l'API sera confirmé par un code de status **2xx** et une réponse sous la forme d'un JSON comme pour l'API précédente.

---
