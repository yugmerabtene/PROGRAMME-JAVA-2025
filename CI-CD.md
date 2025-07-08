# CI/CD, Docker et Kubernetes pour les applications Java

## 1. Introduction à l’intégration et au déploiement continus

* Définition CI (Intégration Continue) : automatisation des tests et builds à chaque commit
* Définition CD (Déploiement Continu / Delivery) : mise en production automatisée
* Objectifs : fiabilité, rapidité, rollback, collaboration
* Pipeline typique : build → test → image Docker → push → déploiement Kubernetes

---

## 2. Docker – Conteneurisation des applications Java

### 2.1 Concepts de base

* Conteneurs, images, registres (Docker Hub, GitHub Container Registry, GitLab Registry)
* Portabilité, légèreté, reproductibilité

### 2.2 Dockerfile pour Spring Boot

```dockerfile
FROM openjdk:17-jdk-slim
ARG JAR_FILE=target/*.jar
COPY ${JAR_FILE} app.jar
ENTRYPOINT ["java", "-jar", "/app.jar"]
```

* Utilisation d’`openjdk` ou `distroless`
* Utilisation de `.dockerignore`
* Variables d’environnement (`ARG`, `ENV`)

### 2.3 Docker Compose

* Définir une architecture complète (`docker-compose.yml`)

  * Microservices, PostgreSQL, Kafka, Zookeeper, Redis, Gateway, Prometheus
* Gestion des dépendances entre services (`depends_on`)
* Réseaux personnalisés, ports exposés
* Persistences des données (volumes)

---

## 3. CI/CD avec GitHub Actions et GitLab CI

### 3.1 GitHub Actions

* Fichier : `.github/workflows/ci.yml`
* Étapes typiques :

  * Checkout du dépôt
  * Compilation avec Maven ou Gradle
  * Tests unitaires (`mvn test`)
  * Construction de l’image Docker (`docker build`)
  * Push vers Docker Hub ou GHCR (`docker push`)
  * Déploiement (optionnel) via SSH ou `kubectl`

**Exemple de structure :**

```yaml
name: Build and Deploy
on:
  push:
    branches: [main]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Set up JDK 17
        uses: actions/setup-java@v3
        with:
          java-version: '17'
      - name: Build with Maven
        run: mvn clean package
      - name: Docker Build & Push
        run: |
          docker build -t dockerhub_user/app:latest .
          echo ${{ secrets.DOCKER_PASSWORD }} | docker login -u ${{ secrets.DOCKER_USERNAME }} --password-stdin
          docker push dockerhub_user/app:latest
```

---

### 3.2 GitLab CI/CD

* Fichier `.gitlab-ci.yml`
* Runners Docker préinstallés sur GitLab ou runners auto-hébergés
* Étapes classiques : build, test, package, deploy
* Variables d’environnement (`CI_REGISTRY`, `CI_COMMIT_REF_NAME`, etc.)
* Intégration avec GitLab Container Registry

**Exemple de pipeline :**

```yaml
stages:
  - build
  - test
  - docker
  - deploy

variables:
  MAVEN_OPTS: "-Dmaven.repo.local=.m2/repository"

build-job:
  stage: build
  image: maven:3.9.4-eclipse-temurin-17
  script:
    - mvn clean compile

test-job:
  stage: test
  image: maven:3.9.4-eclipse-temurin-17
  script:
    - mvn test

docker-job:
  stage: docker
  image: docker:latest
  services:
    - docker:dind
  script:
    - docker build -t $CI_REGISTRY_IMAGE:$CI_COMMIT_SHORT_SHA .
    - echo $CI_REGISTRY_PASSWORD | docker login -u $CI_REGISTRY_USER $CI_REGISTRY --password-stdin
    - docker push $CI_REGISTRY_IMAGE:$CI_COMMIT_SHORT_SHA

deploy-job:
  stage: deploy
  image: alpine/kubectl:1.27.2
  script:
    - kubectl apply -f k8s/
  only:
    - main
```

---

## 4. Kubernetes – Orchestration de conteneurs

### 4.1 Concepts fondamentaux

* Pods, ReplicaSets, Deployments
* Services (`ClusterIP`, `NodePort`, `LoadBalancer`)
* ConfigMaps, Secrets
* Volumes persistants
* Namespaces, RBAC (droits par rôle)

### 4.2 Déploiement d’une application Spring Boot

* Fichiers :

  * `deployment.yaml` : image, ports, env, réplication
  * `service.yaml` : exposition dans le cluster
* Ingress Controller (NGINX ou Traefik)
* Cert-manager pour HTTPS (Let’s Encrypt)

### 4.3 Helm – Templates de déploiement

* Structure d’un chart Helm
* Fichier `values.yaml` pour les environnements
* Commandes Helm : `install`, `upgrade`, `rollback`, `uninstall`
* Variables dynamiques et substitutions

### 4.4 Monitoring et observabilité

* Spring Boot Actuator + Prometheus + Grafana
* Logging centralisé avec Loki ou ELK
* APM (ex. : Zipkin, Jaeger pour les traces)
* Alerts avec Alertmanager

---

## 5. Sécurité du pipeline

* Analyse de sécurité des images Docker (Trivy, Snyk)
* Contrôle des secrets (`.env`, GitHub/GitLab Secrets, Vault, SSM)
* RBAC pour l’accès à Kubernetes
* Signatures d’images avec Cosign
* Sécurisation des endpoints CI (webhooks, token, context)

---

## 6. Déploiement multi-environnements

* Utilisation de GitLab CI environments ou GitHub Actions Matrix
* Configurations séparées : `dev`, `staging`, `prod`
* Séparation des fichiers Helm (`values-dev.yaml`, etc.)
* Promotion manuelle entre environnements
* Canary deploy, Blue/Green deploy avec labels et selectors
