# Stratégies de tests en Java avec Spring Boot

## 1. Objectifs des tests logiciels

* Vérifier le bon fonctionnement du code (fiabilité)
* Éviter les régressions lors des évolutions
* Faciliter la maintenance
* Documenter les comportements attendus
* Garantir la non-régression fonctionnelle

---

## 2. Types de tests

### 2.1 Test unitaire

* Cible : une méthode, une classe, isolée du reste
* Outils : JUnit 5 (`@Test`), Mockito (`@Mock`, `@InjectMocks`)
* Isolation des dépendances avec des mocks ou stubs
* Exemples :

  * Test d’une méthode de calcul
  * Mock du repository pour ne tester que la logique métier

### 2.2 Test d’intégration

* Cible : interaction entre plusieurs composants (ex. : controller + service + repository)
* Chargement partiel ou complet du contexte Spring
* Outils :

  * `@SpringBootTest`
  * `@DataJpaTest`, `@WebMvcTest`
  * Bases de test avec H2 en mémoire ou PostgreSQL Docker
* Exemple : vérification que la couche `Service` interagit bien avec la base

### 2.3 Test fonctionnel / bout-en-bout (End-to-End)

* Teste le comportement global d’une fonctionnalité du point de vue utilisateur
* Couvre plusieurs couches : UI → Controller → Service → DB
* Outils :

  * Spring MockMvc (`mockMvc.perform`)
  * Selenium, Cypress, Playwright (pour les tests front)
  * REST-assured (pour REST API automatisées)
* Exemple : test de création d’un utilisateur via HTTP POST

### 2.4 Test de non-régression

* Ensemble de tests automatisés existants qu'on relance à chaque modification
* Peut inclure des tests unitaires, d’intégration, fonctionnels
* But : détecter qu’un ancien bug ne réapparaît pas
* À exécuter dans la CI (GitHub Actions, GitLab CI…)

### 2.5 Test de performance (Load testing)

* Mesure de la rapidité, de la scalabilité, de la résilience
* Outils :

  * JMeter
  * Gatling
  * Artillery (REST)
* Exemple : 1 000 requêtes simultanées sur une API critique

### 2.6 Test de sécurité

* Tests automatiques ou manuels des vulnérabilités (OWASP Top 10)
* Outils :

  * OWASP ZAP
  * Burp Suite
  * Spring Security Test
  * Tests d'accès non autorisés (`403`, `401`)

---

## 3. Écosystème de test en Java Spring

* **JUnit 5** : framework principal pour les tests unitaires
* **Mockito** : mocking de dépendances
* **AssertJ / Hamcrest** : assertions fluides et lisibles
* **Spring Boot Test** :

  * `@SpringBootTest`
  * `@WebMvcTest`
  * `@DataJpaTest`
* **Testcontainers** :

  * Lancer PostgreSQL, Kafka, Redis, Mongo en Docker pendant les tests
  * Isolation et reproductibilité des tests d’intégration
* **H2 Database** : pour tests rapides en mémoire

---

## 4. Couverture de test (Code Coverage)

* Mesure du pourcentage de code exécuté par les tests
* Outils :

  * **JaCoCo** (Java Code Coverage)
  * Intégration avec Maven (`jacoco-maven-plugin`)
  * SonarQube (analyse qualité + couverture)
* Types de couverture :

  * Ligne
  * Instruction
  * Branche
  * Chemin
* Objectif : au moins **80 %** de couverture **utile** (pas du code mort ou auto-généré)

---

## 5. Stratégie de tests complète par couche

| Couche           | Type de test               | Objectif                                  |
| ---------------- | -------------------------- | ----------------------------------------- |
| Controller       | Test fonctionnel + MockMvc | Valider les routes HTTP, statut, payload  |
| Service (métier) | Test unitaire + mock repo  | Vérifier la logique métier                |
| Repository       | `@DataJpaTest`             | Vérifier le mapping entité/requête SQL    |
| API REST externe | Test d’intégration         | Tester la réponse, code, format           |
| Kafka Listener   | `@EmbeddedKafka`           | Simuler réception de message Kafka        |
| Sécurité         | Spring Security Test       | Test accès authentifié vs non authentifié |

---

## 6. Organisation des répertoires de test

* `src/test/java/...`

  * `controller/`
  * `service/`
  * `repository/`
  * `integration/`
  * `security/`
  * `utils/`
* Bonnes pratiques :

  * Un fichier de test par classe
  * Tests nommés clairement
  * `@DisplayName` pour lisibilité
  * Classes de configuration test dédiée si nécessaire

---

## 7. Automatisation des tests dans CI/CD

* Ajout dans pipeline GitHub Actions ou GitLab CI
* Étapes :

  * `mvn clean verify`
  * Génération du rapport Jacoco
  * Upload dans SonarQube ou HTML
* Blocage du merge si les tests échouent
* Notification Slack/Teams en cas d’échec
