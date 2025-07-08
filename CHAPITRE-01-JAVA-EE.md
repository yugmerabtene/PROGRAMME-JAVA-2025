# Programme Complet – Apprentissage Java EE (Jakarta EE)

## Chapitre 1 – Introduction à Java EE

* Présentation de Java EE / Jakarta EE
* Différences entre Java SE et Java EE
* Architecture n-tiers (client – serveur – base de données)
* Conteneurs Java EE (Tomcat, WildFly, Payara, GlassFish)
* Déploiement de WAR et EAR
* Outils de développement (Maven, Gradle, IntelliJ, Eclipse EE)
* Serveurs d’application vs serveurs web

## Chapitre 2 – Java Servlet API

* Introduction aux servlets
* Cycle de vie d’un servlet
* Méthodes `doGet`, `doPost`, `doPut`, `doDelete`
* Objets `HttpServletRequest`, `HttpServletResponse`
* Redirection, forward, gestion des statuts HTTP
* Utilisation des sessions HTTP (`HttpSession`)
* Gestion des cookies
* Filtres (`Filter`) et écouteurs (`Listener`)
* Mécanisme d’initialisation (`init-param`, `context-param`)
* Mapping et annotation `@WebServlet`, `@WebFilter`

## Chapitre 3 – JavaServer Pages (JSP)

* Syntaxe JSP, directives, balises
* Expressions, déclarations, scriptlets (à éviter en pratique)
* Utilisation des objets implicites (`request`, `response`, `session`, `application`)
* JSTL (Java Standard Tag Library)
* Fichiers `.jspf` (fragments)
* Séparation logique : modèle MVC
* Inclusion dynamique vs statique (`<jsp:include>`, `<%@ include %>`)

## Chapitre 4 – JavaServer Faces (JSF)

* Introduction à JSF et composants UI
* Fichier `faces-config.xml`
* Beans managés (`@ManagedBean`, `@ViewScoped`, etc.)
* Navigation et validation
* Expression Language (EL)
* JSF avec Facelets (`.xhtml`)
* Messages et gestion d’erreurs dans l’interface
* Intégration avec CDI (JSF + CDI)

## Chapitre 5 – Java Persistence API (JPA)

* Architecture ORM
* Entités (`@Entity`), identifiants (`@Id`)
* Mapping des attributs (`@Column`, `@Embedded`, `@Enumerated`)
* Relations entre entités (`@OneToOne`, `@OneToMany`, `@ManyToOne`, `@ManyToMany`)
* Contexte de persistance (`persistence.xml`)
* Transactions (`@Transactional`, `EntityTransaction`)
* JPQL (Java Persistence Query Language)
* Requêtes dynamiques et nommées (`@NamedQuery`)
* Injections de `EntityManager`
* Chargement paresseux et eager

## Chapitre 6 – Enterprise JavaBeans (EJB)

* Présentation des EJBs
* Types d’EJBs : Session Beans (stateless, stateful, singleton)
* Annotations : `@Stateless`, `@Stateful`, `@Singleton`
* Injection avec `@EJB`
* Cycle de vie et gestion des ressources
* Transactions déclaratives et programmatiques
* Timers (planification avec `@Schedule`)
* Sécurité avec EJB
* EJB remote et local interfaces

## Chapitre 7 – Contexts and Dependency Injection (CDI)

* Présentation de CDI
* Injection avec `@Inject`
* Scope des beans : `@RequestScoped`, `@SessionScoped`, `@ApplicationScoped`
* Qualifiers (`@Named`, `@Qualifier`)
* Producteurs (`@Produces`)
* Alternatives et `@Default`
* Intercepteurs (`@Interceptor`)
* Décorateurs et événements CDI

## Chapitre 8 – Java API for RESTful Web Services (JAX-RS)

* Principes du REST
* Création d’un service REST avec `@Path`, `@GET`, `@POST`, `@PUT`, `@DELETE`
* Manipulation des objets `Request`, `Response`
* Production et consommation de JSON/XML (`@Produces`, `@Consumes`)
* JAX-RS Client API (client REST)
* Injections contextuelles (`@Context`)
* Paramètres de chemin, query, header (`@PathParam`, `@QueryParam`, etc.)
* Filtres JAX-RS (`ContainerRequestFilter`, `ContainerResponseFilter`)

## Chapitre 9 – Sécurité des applications Java EE

* Authentification et autorisation (déclarative et programmatique)
* Fichiers `web.xml`, rôles (`<security-role>`)
* Sécurité des EJB (`@RolesAllowed`, `@PermitAll`, `@DenyAll`)
* Gestion des utilisateurs (realm, JAAS)
* CSRF, XSS, injection SQL : bonnes pratiques
* HTTPS et certificats SSL
* Gestion des accès via annotations ou fichiers de configuration

## Chapitre 10 – Validation avec Bean Validation (JSR 380/403)

* Intégration avec JPA, JSF, REST
* Contraintes standards (`@NotNull`, `@Size`, `@Email`, `@Pattern`, etc.)
* Validation personnalisée (`@Constraint`)
* Message d’erreur personnalisé (`ValidationMessages.properties`)
* Intégration avec les formulaires (`h:message`, `ValidationException`)

## Chapitre 11 – Java Messaging Service (JMS)

* Architecture de la messagerie asynchrone
* Queue vs Topic
* Producteur et consommateur de message
* JMS Context, `MessageProducer`, `MessageConsumer`
* Types de messages (`TextMessage`, `ObjectMessage`, etc.)
* Gestion des listeners asynchrones (`@MessageDriven`)
* Transaction JMS

## Chapitre 12 – Packaging et déploiement

* WAR (Web ARchive) : structure, contenu, `web.xml`
* EAR (Enterprise ARchive) : structure, `application.xml`
* Gestion des dépendances (Maven, Gradle)
* Déploiement sur WildFly, GlassFish, Payara, etc.
* Hot deployment et configuration serveur

## Chapitre 13 – Intégration avec Maven

* Structure de projet standard avec Maven (`src/main/java`, `src/main/resources`)
* Fichier `pom.xml` : dépendances, plugins
* Compilation, tests, packaging avec Maven
* Plugins utiles : `maven-war-plugin`, `maven-compiler-plugin`, `maven-dependency-plugin`
* Gestion des profils et environnements

## Chapitre 14 – Tests et intégration continue

* Tests unitaires avec JUnit 5
* Tests d’intégration avec Arquillian ou Jakarta EE Embedded
* Tests REST avec REST-assured
* Mocks et doubles avec Mockito
* Introduction à l’intégration continue (Jenkins, GitLab CI, GitHub Actions)
* Packaging et déploiement automatisé
