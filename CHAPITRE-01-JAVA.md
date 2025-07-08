# Programme Complet – Apprentissage Java SE

## Chapitre 1 – Introduction et environnement

* Présentation de Java : JVM, JRE, JDK
* Historique du langage et évolutions (Java 5 à Java 21)
* Installation de l’environnement (JDK, IDE : IntelliJ, Eclipse, VSCode)
* Compilation et exécution avec `javac` et `java`
* Structure d’un programme Java
* Système de fichiers et conventions de nommage

## Chapitre 2 – Types, variables et opérateurs

* Types primitifs : `int`, `long`, `double`, `float`, `char`, `boolean`, `byte`, `short`
* Autoboxing et unboxing
* Variables locales, d’instance et de classe (`static`)
* Portée des variables
* Constantes (`final`)
* Opérateurs : arithmétiques, relationnels, logiques, bit à bit, conditionnels, affectation
* Conversion de types, casting explicite et implicite
* Type inference avec `var` (Java 10+)

## Chapitre 3 – Structures de contrôle

* Instructions conditionnelles : `if`, `else if`, `else`, `switch` (et `switch` amélioré depuis Java 14)
* Boucles : `for`, `while`, `do-while`, `foreach`
* Instructions de contrôle de flux : `break`, `continue`, `return`, `label`

## Chapitre 4 – Tableaux et chaînes de caractères

* Tableaux unidimensionnels et multidimensionnels
* Initialisation, accès, parcours
* Manipulation de chaînes : `String`, `StringBuilder`, `StringBuffer`
* Méthodes utiles : `substring`, `split`, `replace`, `indexOf`, etc.
* Notion d’immuabilité

## Chapitre 5 – Programmation orientée objet

* Définition de classes et objets
* Attributs et méthodes
* Constructeurs et surcharge
* Méthodes statiques vs d’instance
* Visibilité : `public`, `private`, `protected`, package-private
* Encapsulation et bonnes pratiques
* Méthodes spéciales : `toString`, `equals`, `hashCode`
* Initialisation statique et blocs d’initialisation

## Chapitre 6 – Héritage et polymorphisme

* Héritage simple, usage de `super`
* Surcharge vs redéfinition de méthodes
* Classes abstraites
* Notion de polymorphisme dynamique
* Casts et `instanceof`

## Chapitre 7 – Interfaces

* Définition et implémentation
* Interface fonctionnelle
* Méthodes `default` et `static`
* Différence avec classes abstraites

## Chapitre 8 – Classes imbriquées

* Classes internes (non statiques)
* Classes statiques imbriquées
* Classes anonymes
* Classes locales

## Chapitre 9 – Packages et modularité

* Organisation du code en packages
* Importations (`import`)
* Modules Java (`module-info.java`, Java 9+)
* Accès inter-modules : `exports`, `requires`

## Chapitre 10 – Gestion des erreurs et exceptions

* Notion d’exception, pile d’appel
* `try`, `catch`, `finally`
* Exceptions vérifiées et non vérifiées
* Hiérarchie (`Throwable`, `Exception`, `RuntimeException`)
* Création d’exceptions personnalisées
* Utilisation de `throws` et `throw`
* Bloc `try-with-resources`

## Chapitre 11 – Généricité

* Définition et usage de types génériques
* Génériques bornés (`<T extends Number>`)
* Génériques avec `?`, `? extends`, `? super`
* Sécurité de type et compilation

## Chapitre 12 – Collections Java

* Framework Collections
* Interfaces : `List`, `Set`, `Map`, `Queue`, `Deque`
* Implémentations : `ArrayList`, `LinkedList`, `HashSet`, `TreeSet`, `HashMap`, `TreeMap`, `PriorityQueue`
* Comparateurs : `Comparable`, `Comparator`
* Parcours : itérateur, boucle `foreach`, `forEach`

## Chapitre 13 – Expressions Lambda

* Syntaxe des lambdas
* Références de méthodes et constructeurs
* Interfaces fonctionnelles : `Predicate`, `Function`, `Consumer`, `Supplier`
* Utilisation avec les collections

## Chapitre 14 – API Stream

* Streams séquentiels et parallèles
* Opérations intermédiaires : `map`, `filter`, `sorted`, `distinct`
* Opérations terminales : `collect`, `forEach`, `count`, `reduce`, `min`, `max`, `anyMatch`
* Collecteurs : `toList`, `toMap`, `groupingBy`, `partitioningBy`
* `Optional` et gestion d’absence de valeur

## Chapitre 15 – Entrées/Sorties (IO/NIO)

* API `java.io` : `File`, `InputStream`, `OutputStream`, `Reader`, `Writer`
* API `java.nio.file` : `Path`, `Files`, `StandardOpenOption`
* Lecture/écriture de fichiers texte et binaire
* Sérialisation et désérialisation

## Chapitre 16 – API Date et Heure

* API `java.time` : `LocalDate`, `LocalTime`, `LocalDateTime`, `ZonedDateTime`, `Instant`
* Manipulations : ajout, retrait, comparaison
* `DateTimeFormatter`, `Period`, `Duration`

## Chapitre 17 – Programmation multithread

* Concepts de thread et concurrence
* Création de threads : `Thread`, `Runnable`, `Callable`, `Future`
* Synchronisation (`synchronized`, blocs synchronisés)
* `ExecutorService`, `ScheduledExecutorService`
* Collections concurrentes : `ConcurrentHashMap`, `CopyOnWriteArrayList`
* Verrous (`Lock`, `ReentrantLock`)
* `wait`, `notify`, `notifyAll`

## Chapitre 18 – Annotation et réflexion

* Annotations standard : `@Override`, `@Deprecated`, `@FunctionalInterface`
* Annotations personnalisées
* Réflexion : `Class`, `Method`, `Field`, `Constructor`
* Chargement dynamique de classes

## Chapitre 19 – Bonnes pratiques de codage

* Conventions de nommage
* Principes SOLID, DRY, KISS
* Organisation du code source
* Documentation avec `javadoc`
* Utilisation des standards de développement

## Chapitre 20 – Tests unitaires

* JUnit 5 : installation et structure
* Assertions classiques
* Tests paramétrés
* Organisation des classes de test
* Introduction à Mockito (mocks, stubs)

## Chapitre 21 – Accès aux bases de données avec JDBC

* Chargement du driver JDBC
* Connexion à une base de données
* Exécution de requêtes SQL
* Utilisation de `PreparedStatement`
* Parcours de `ResultSet`
* Gestion des transactions
* Fermeture des ressources
* Gestion des exceptions SQL

## Chapitre 22 – Internationalisation et localisation

* Utilisation de `Locale`
* Fichiers de propriétés multilingues
* Formatage de textes, dates et nombres
* Support d’affichage multi-langues
