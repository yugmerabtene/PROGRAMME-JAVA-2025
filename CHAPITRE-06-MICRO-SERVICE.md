# Architecture Microservices avec Spring Boot

## 1. Introduction à l’architecture microservices

* Définition : découpage d’un système en services autonomes
* Différences avec une architecture monolithique
* Avantages : scalabilité, indépendance, déploiement isolé
* Inconvénients : complexité, gestion des communications, sécurité
* Patterns essentiels : API Gateway, Registry, Circuit Breaker, CQRS, Saga

## 2. Architecture technique d’un projet microservices

* Services indépendants : `auth-service`, `product-service`, `order-service`, etc.
* Communication via HTTP REST et/ou Kafka
* Utilisation d’une base de données par microservice (pattern Database per Service)
* Centralisation des logs, configuration, monitoring
* Gestion des erreurs distribuées

## 3. Communication synchrone – API REST

* Exposition des services via `@RestController`
* Consommation de services via `RestTemplate` ou `WebClient`
* Gestion des erreurs HTTP entre services
* DTO, mapping, et validation d’entrées/sorties

## 4. Communication asynchrone – Kafka

* Présentation de Kafka : producer, consumer, broker, topic, partition
* Installation locale ou Docker de Kafka + Zookeeper
* Dépendances `spring-kafka`
* Configuration du producer et du consumer
* Sérialisation JSON avec Kafka
* Pattern Event-Driven : envoi d’événement `OrderCreated`, `ProductReserved`, etc.
* Gestion de la redondance, de l’offset, des erreurs
* Monitoring avec Kafka UI ou Confluent Control Center

## 5. Spring Cloud (Eureka, Config, Gateway)

* **Eureka Server** (service discovery)

  * Démarrage d’un serveur Eureka
  * Enregistrement de services clients
  * Résolution automatique de l’URL d’un service distant
* **Spring Cloud Config**

  * Centralisation de la configuration
  * Stockage dans un dépôt Git
  * Rafraîchissement à chaud avec Actuator
* **API Gateway**

  * Routage des requêtes via Spring Cloud Gateway
  * Filtres : ajout d’en-têtes, validation, authentification
  * Intégration avec Eureka

## 6. Sécurité des microservices

* Authentification via un service `auth-service`
* JWT (JSON Web Token) pour sécuriser les échanges entre services
* Filtrage des requêtes à la Gateway
* `SecurityFilterChain`, `OncePerRequestFilter`, `BearerTokenAuthenticationFilter`
* Gestion des rôles, des claims, des scopes
* Communication sécurisée inter-services avec JWT transmis dans les headers
* CORS, CSRF, sessions stateless

## 7. Base de données et persistance

* Chaque microservice possède sa propre base : PostgreSQL, MySQL, MongoDB, etc.
* Configuration des connexions (`application.yml`)
* Utilisation de JPA, Spring Data, MongoRepository, etc.
* Versionnement de schéma avec Flyway ou Liquibase
* Pattern Outbox (Kafka + base de données pour fiabilité)

## 8. Gestion des erreurs, logs et traçabilité

* Logger centralisé avec ELK (Elasticsearch, Logstash, Kibana) ou Grafana Loki
* Ajout de trace ID/correlation ID dans chaque requête
* Propagation du contexte via Kafka et HTTP
* Gestion des exceptions globales avec `@ControllerAdvice`
* Monitoring via Prometheus + Grafana
* Spring Boot Actuator pour métriques internes

## 9. Tests et validation

* Tests unitaires et d’intégration avec Spring Boot
* Test Kafka avec `EmbeddedKafka`
* Test des endpoints REST avec `MockMvc` et `TestRestTemplate`
* Utilisation de WireMock pour simuler des services externes
* Intégration dans la CI avec JUnit et Docker Compose

## 10. Déploiement et CI/CD

* Dockerisation des microservices (Dockerfile, docker-compose)
* Fichier `docker-compose.yml` : PostgreSQL, Kafka, services, gateway
* CI/CD avec GitHub Actions, GitLab CI, Jenkins
* Exécution des tests, build des images, push sur DockerHub
* Déploiement sur :

  * VPS (Nginx, Docker, Traefik)
  * Kubernetes (Minikube, k3s, GKE, AKS…)
* Configuration et secrets avec Vault, AWS Parameter Store ou Kubernetes Secrets

## 11. Avancées et scalabilité

* Détection d’anomalies et gestion de la résilience

  * Circuit breaker avec Resilience4j ou Spring Cloud Circuit Breaker
  * Retry, fallback, timeouts
* Load balancing (Spring Cloud LoadBalancer, NGINX, Kubernetes)
* Partitionnement Kafka pour haute performance
* Scaling horizontal des services selon charge
* Messaging avancé : Kafka Streams, kSQL, Schema Registry
