# Meinen Learnings aus dem Arbeiten mit der Leocloud

## Kubernetes

Um Kubernetes zu entwicklen wollte ich zuerst den Shortcut gehen und einfach drauf los Konfigurieren aber davor muss man ein grundsätzliches Verständnis von Kubernites haben. Ohne dem Verständnis, wie zum Beispiel die ganzen Komponenten heißen, ist es sehr schwer Kubernetes zu konfigurieren. Man sollte sich zumindest diese Website durchlesen: https://kubernetes.io/docs/tutorials/kubernetes-basics/.

Außerdem ist es wichtig seinen Namespace in der Leocloud zu Wissen und diesen zu beachten.
## Postgres Setup

```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: postgres-pvc
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 1Gi
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: herbert-database
  labels:
    app: herbert-database
spec:
  replicas: 1
  selector:
    matchLabels:
      app: herbert-database
  template:
    metadata:
      labels:
        app: herbert-database
    spec:
      containers:
        - name: postgres
          image: postgres:latest
          env:
            - name: POSTGRES_PASSWORD
              value: "postgres"
          ports:
            - containerPort: 5432
          volumeMounts:
            - mountPath: /var/lib/postgresql/data
              name: postgres-storage
      volumes:
        - name: postgres-storage
          persistentVolumeClaim:
            claimName: postgres-pvc
---
apiVersion: v1
kind: Service
metadata:
  name: postgres-service
spec:
  type: ClusterIP
  selector:
    app: herbert-database
  ports:
    - protocol: TCP
      port: 5432
      targetPort: 5432
```

Das ist die yaml Config, mit der unsere Postgres Datenbank auf der Leocloud läuft. Dieses File muss man einfach nur auf seine Bedürfnisse anpassen.

## Secrets

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: app-secrets
  namespace: # TODO: Change namespace
type: Opaque
data:
  OPENAI_KEY: <Key-Base64-Encoded>
  ```

Was mich auch sehr viel Zeit und Nerfen gekostet hat sind die Secrets und der Secret access. Hier muss man das Prinzip hinter Kubernetes Secrets verstehen. Auch das Auslesen von Secrets hat für mich sehr lange gedauert. Man macht es wie so:
```csharp
builder.Configuration.AddEnvironmentVariables();

Environment.GetEnvironmentVariable("MAIL_ADDRESS")
```

Außerdem ist es noch wichtig die Kubernetes Secrets in der App Deploment file unter der env Section zu verlinken.
```yaml
- name: OPENAI_KEY
  valueFrom:
    secretKeyRef:
      name: app-secrets
      key: OPENAI_KEY
```

## Image on Dockerhub

Kubernetes muss sich die Images von Dockerhub ziehen. Um das Docker Image dort zu veröffentlichen braucht man einen GH-Action. Dafür habe ich dieses teilweise veraltetetes Tutorial benutzt. https://medium.com/@kova98/automating-net-deployment-with-github-actions-and-docker-d43109d34f88

Hier ist meine Action:

```yaml
name: Build and Deploy C# Project to Docker Hub

on:
  push:
    branches: [ "main" ]
  pull_request:
    branches:
      - main

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout Code
      uses: actions/checkout@v3

    - name: Setup .NET
      uses: actions/setup-dotnet@v3
      with:
        dotnet-version: '8.x'

    - name: Restore Dependencies
      working-directory: Backend
      run: dotnet restore

    - name: Build Project
      working-directory: Backend
      run: dotnet build --configuration Release --no-restore

    - name: Publish Project
      working-directory: Backend
      run: dotnet publish --configuration Release --no-build --output ./publish

    - name: Build Docker Image
      working-directory: .
      run: docker build . -t ${{ secrets.DOCKERHUB_USERNAME }}/herbert-backend:latest

    - name: Log into Docker Hub
      uses: docker/login-action@v2
      with:
        username: ${{ secrets.DOCKERHUB_USERNAME }}
        password: ${{ secrets.DOCKERHUB_TOKEN }}

    - name: Push Docker Image
      run: docker push ${{ secrets.DOCKERHUB_USERNAME }}/herbert-backend:latest
```
