# Framework Spring et Spring Boot

## 1. Introduction à Spring Framework

* Objectifs du framework Spring : légèreté, modularité, injection de dépendance
* Architecture modulaire (Spring Core, Spring MVC, Spring Data, Spring Security…)
* Comparaison avec Java EE / Jakarta EE
* Inversion de contrôle (IoC) et injection de dépendances

## 2. Spring Core – IOC Container

* Notion de **bean**, **container**, **contexte**
* Configuration via :

  * Fichier XML (`applicationContext.xml`)
  * Java config avec `@Configuration` et `@Bean`
  * Annotation `@Component`, `@Service`, `@Repository`, `@Controller`
* Injection de dépendance :

  * Par constructeur (`@Autowired`)
  * Par setter
  * Qualifiers (`@Qualifier`, `@Primary`)
* Cycle de vie des beans (`@PostConstruct`, `@PreDestroy`)

## 3. Spring Boot – Démarrage simplifié

* Objectifs de Spring Boot : zéro configuration, opinionated defaults
* Structure d’un projet Spring Boot
* Démarrage avec `@SpringBootApplication`
* Auto-configuration et starters (`spring-boot-starter-*`)
* Fichier `application.properties` ou `application.yml`
* Profils de configuration (`@Profile`)
* Intégration avec Maven/Gradle

## 4. Spring MVC – Développement Web

* Architecture MVC avec Spring
* Contrôleurs REST (`@RestController`)
* Routing avec `@RequestMapping`, `@GetMapping`, `@PostMapping`, etc.
* Injection des paramètres (`@PathVariable`, `@RequestParam`, `@RequestBody`)
* Gestion des statuts HTTP (`ResponseEntity`)
* Filtres, interceptors, exceptions personnalisées (`@ExceptionHandler`)
* CORS, logs, validation d’entrée

## 5. Spring Data JPA – Persistance des données

* Intégration JPA avec Spring Boot
* Configuration de la datasource
* Définition des entités avec `@Entity`
* Repositories Spring Data (`JpaRepository`, `CrudRepository`)
* Méthodes dérivées (`findByEmail`, `deleteByName`)
* Requêtes personnalisées (`@Query`)
* Pagination et tri (`Pageable`)
* Gestion des transactions (`@Transactional`)

## 6. Spring Validation

* Utilisation des annotations : `@NotNull`, `@Size`, `@Email`, etc.
* Intégration avec `@Valid` dans les contrôleurs
* Messages d’erreurs personnalisés
* Gestion des erreurs de validation globales

## 7. Spring Security – Sécurité

* Principes de base : authentification, autorisation
* Sécurisation des routes avec `@PreAuthorize`, `@Secured`, `@RolesAllowed`
* Intégration avec `UserDetailsService`, `PasswordEncoder`
* Filtres de sécurité (`OncePerRequestFilter`, `SecurityFilterChain`)
* CSRF, CORS, JWT
* Login avec formulaire, Basic Auth, ou token JWT

## 8. Spring REST + JSON/XML

* Sérialisation/désérialisation avec Jackson (`@JsonProperty`, `@JsonIgnore`)
* Formatage des dates, objets imbriqués, `@JsonView`
* Retour JSON par défaut avec Spring Boot
* Conversion automatique JSON ↔ Objet Java

## 9. Spring Boot Actuator

* Monitoring et diagnostic des applications
* Endpoints exposés (`/actuator/health`, `/metrics`, `/env`, `/beans`, etc.)
* Activation/configuration des endpoints
* Sécurisation des accès à l’Actuator

## 10. Spring Boot Test & JUnit

* Tests unitaires avec `@SpringBootTest`, `@DataJpaTest`, `@WebMvcTest`
* Mocking avec `@MockBean`, `Mockito`
* Tests des REST controllers avec `MockMvc`
* Tests de repository avec H2 in-memory
* Tests de sécurité (mock user)

## 11. Configuration avancée

* Utilisation de `@Value`, `@ConfigurationProperties`
* Gestion des fichiers `.properties` et `.yml` par environnement
* Utilisation de `CommandLineRunner` et `ApplicationRunner`
* Injection conditionnelle avec `@Conditional`, `@Profile`

## 12. Intégration avec d'autres composants

* Intégration avec Kafka, RabbitMQ, Redis, MongoDB, Elasticsearch, etc.
* Cache avec `@Cacheable`, `@EnableCaching`
* Job scheduling avec `@Scheduled`
* Envoi de mail avec Spring Mail (`JavaMailSender`)
* API externes : consommation via `RestTemplate` ou `WebClient` (Spring WebFlux)
