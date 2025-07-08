# Principes de conception et Design Patterns

## 1. Principes SOLID (orientés objets)

Les principes SOLID définissent les règles fondamentales pour concevoir un système orienté objet maintenable :

### S – Single Responsibility Principle (SRP)

**Une classe ne doit avoir qu’une seule raison de changer.**
Chaque classe doit assumer une responsabilité unique.

### O – Open/Closed Principle (OCP)

**Les entités logicielles doivent être ouvertes à l’extension mais fermées à la modification.**
On doit pouvoir ajouter des fonctionnalités sans modifier le code existant.

### L – Liskov Substitution Principle (LSP)

**Une classe dérivée doit pouvoir être utilisée comme sa classe parente sans altérer le fonctionnement.**

### I – Interface Segregation Principle (ISP)

**Il vaut mieux plusieurs interfaces spécifiques que quelques grosses interfaces générales.**

### D – Dependency Inversion Principle (DIP)

**Les modules de haut niveau ne doivent pas dépendre de modules de bas niveau.**
Ils doivent tous deux dépendre d’abstractions (interfaces).

---

## 2. Principes DRY et STUPID

### DRY – Don’t Repeat Yourself

**Éviter la duplication de code ou de logique.**
Chaque élément de logique métier doit être unique dans le code.

### STUPID – Mauvaises pratiques courantes à éviter

* **S**ingletons excessifs
* **T**ight Coupling (fort couplage entre classes)
* **U**ntestable code (code difficile à tester)
* **P**remature Optimization (optimiser trop tôt)
* **I**ndescriptive Naming (noms de variables peu explicites)
* **D**uplication (copier-coller au lieu de réutilisation)

---

## 3. Design Patterns (Patrons de conception)

Les Design Patterns sont des solutions standardisées à des problèmes récurrents en conception logicielle (Toujours se refer a ce site : https://refactoring.guru).

### 3.1 Patterns de création

* **Singleton**
  Garantit une seule instance d’une classe dans tout le programme.

* **Factory Method**
  Fournit une interface pour créer un objet sans exposer sa création.

* **Abstract Factory**
  Fournit une interface pour créer des familles d’objets liés.

* **Builder**
  Sépare la construction d’un objet complexe de sa représentation.

* **Prototype**
  Crée de nouveaux objets en clonant des objets existants.

### 3.2 Patterns structurels

* **Adapter**
  Permet d’utiliser une interface incompatible avec celle attendue.

* **Decorator**
  Ajoute dynamiquement des fonctionnalités à un objet.

* **Facade**
  Fournit une interface simplifiée à un ensemble de classes.

* **Composite**
  Organise des objets en structures arborescentes (ex : menus, arbres).

* **Proxy**
  Représente un objet avec un substitut pour contrôler l’accès.

### 3.3 Patterns comportementaux

* **Observer**
  Permet à des objets d’être notifiés automatiquement d’un changement d’état (utilisé en MVC, Kafka…).

* **Strategy**
  Définit une famille d’algorithmes interchangeables dynamiquement.

* **Command**
  Encapsule une requête comme un objet.

* **State**
  Permet à un objet de modifier son comportement selon son état.

* **Template Method**
  Définit le squelette d’un algorithme en laissant certaines étapes aux sous-classes.

* **Mediator**
  Gère la communication entre objets sans couplage direct.
