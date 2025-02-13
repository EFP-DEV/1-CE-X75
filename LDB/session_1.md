# **Introduction aux Concepts de Bases de Données**

## **1. Qu'est-ce qu'une Base de Données ?**
Une **base de données** est une collection organisée de données stockées et gérées électroniquement. Les bases de données permettent aux utilisateurs de stocker, récupérer et manipuler des données de manière efficace en utilisant un logiciel spécialisé appelé **Système de Gestion de Base de Données (SGBD).**

### **Types de Bases de Données**
- **Bases de Données Relationnelles (SGBDR) :** Utilisent des tables structurées pour stocker les données et prennent en charge les requêtes SQL.
- **Bases de Données NoSQL :** Stockent les données dans une variété de formats tels que clé-valeur, document ou structures basées sur des graphes.

## **2. Tables dans une Base de Données**
Une **table** (ou **relation**) est l'élément fondamental d'une base de données relationnelle. Une table est composée de **lignes (enregistrements)** et de **colonnes (attributs).**

Exemple de Table (Données des Étudiants) :

```plaintext
| id  | name  | age | major            |
|-----|-------|-----|------------------|
| 101 | Alice | 21  | Informatique     |
| 102 | Bob   | 22  | Mathématiques    |
```

## **3. Schéma : La Structure d'une Base de Données**
Un **schéma** définit la structure d'une base de données, y compris l'organisation des tables, des colonnes, des types de données et des relations entre les tables. Le schéma fournit un plan directeur pour le stockage et l'accès aux données.

## **4. Lignes et Colonnes**
- **Ligne (Enregistrement ou Tuple) :** Une entrée unique dans une table qui contient des valeurs pour chaque colonne.
- **Colonne (Attribut) :** Un champ de données spécifique dans une table qui contient des informations d'un type particulier.

Exemple :
- Dans la table `student` ci-dessus, **chaque ligne représente un étudiant différent**.
- **Les colonnes définissent le type d'information stockée** (par exemple, `name`, `age`, `major`).

## **5. Relations Entre les Tables**
Dans les bases de données relationnelles, des **relations** sont établies entre les tables pour éviter la redondance des données et assurer une gestion efficace des données.

### **Types de Relations :**
- **Un-à-Un (1:1) :** Chaque enregistrement de la Table A correspond à exactement un enregistrement de la Table B.
- **Un-à-Plusieurs (1:M) :** Un enregistrement de la Table A peut être associé à plusieurs enregistrements de la Table B.
- **Plusieurs-à-Plusieurs (M:N) :** Plusieurs enregistrements de la Table A peuvent être liés à plusieurs enregistrements de la Table B (nécessite une table de jonction).

Exemple de Relation :
- Une table `student` et une table `enrollment` peuvent être liées en utilisant un `student_id` comme clé étrangère.

## **6. Clés dans une Base de Données**
### **Clé Primaire**
Une **Clé Primaire** identifie de manière unique chaque enregistrement dans une table. Elle doit être unique et ne peut pas contenir de valeurs NULL.

Exemple :
```sql
CREATE TABLE student (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    age INT,
    major VARCHAR(50)
);
```
- `id` est la **clé primaire** dans cette table.

### **Clé Étrangère**
Une **Clé Étrangère** établit une relation entre deux tables en référençant la **Clé Primaire** d'une autre table.

Exemple :
```sql
CREATE TABLE enrollment (
    id INT PRIMARY KEY,
    student_id INT,
    course_id INT,
    FOREIGN KEY (student_id) REFERENCES student(id)
);
```
- `student_id` dans `enrollment` référence le `id` dans `student`.

## **7. Index pour des Requêtes Plus Rapides**
Un **index** est une structure de base de données qui améliore la vitesse des opérations de récupération de données. Les index fonctionnent comme une table des matières pour un livre, aidant la base de données à localiser les enregistrements de manière efficace.

Exemple :
```sql
CREATE INDEX idx_student_name ON student(name);
```
- Cet index accélère les recherches d'étudiants par `name`.

## **8. Résumé**
- Une **base de données** est un système organisé pour stocker et gérer des données.
- Une **table** est composée de **lignes (enregistrements)** et de **colonnes (attributs).**
- Un **schéma** définit la structure d'une base de données.
- Les **relations** entre les tables aident à maintenir l'intégrité des données.
- Les **clés primaires** identifient de manière unique les enregistrements, tandis que les **clés étrangères** établissent des relations.
- Les **index** améliorent les performances des requêtes.

# **LDB - Exercices**

## **Tables Simples**

### **Objectif**
Nous allons modéliser différentes tables afin de se familiariser avec les concepts de **champs (colonnes), nommage et types de données**.

Cet exercice est à la fois une **investigation conceptuelle** et une **modélisation concrète**.

---

## **Processus de Modélisation d'une Base de Données**

### **1. Comprendre le Domaine d'Application**
Avant de commencer la modélisation d’une base de données, il est essentiel de comprendre **le contexte réel**. Cela implique :
- L’identification des **entités principales**.
- La compréhension des **informations à stocker**.
- L’analyse des **contraintes métier**.

Exemple : Pour un **site de cinéma**, nous avons besoin d’informations sur les **films**, les **acteurs**, et leurs caractéristiques.

---

### **2. Identification des Entités et des Attributs**
Chaque **entité** correspond généralement à une **table**. Pour chaque entité, nous devons lister :
- Les **attributs** pertinents (colonnes).
- Leur **type de données**.
- Leur **nécessité** (obligatoire ou optionnel).

Exemple pour un film :
| Attribut      | Type        | Obligatoire |
|--------------|------------|------------|
| id           | INT        | Oui        |
| title        | VARCHAR(255) | Oui        |
| year         | INT        | Oui        |
| genre        | VARCHAR(100) | Non        |

---

### **3. Définition du Schéma de la Base de Données**
Le **schéma** définit la structure et l’organisation des tables. Il inclut :
- Les **noms des tables**.
- Les **relations** entre elles (non incluses ici).
- Les **contraintes** appliquées sur les colonnes (unicité, valeurs non nulles, etc.).

Exemple de définition SQL :
```sql
CREATE TABLE film (
    id INT PRIMARY KEY,
    title VARCHAR(255) NOT NULL,
    year INT NOT NULL,
    genre VARCHAR(100)
);
```

---

### **4. Structuration des Données**
Une fois les entités définies, nous devons :
1. **Créer les tables** dans un SGBD (ex: MySQL, PostgreSQL).
2. **Vérifier l’intégrité des données**.
3. **Remplir avec des exemples de données** pour tester le modèle.

Exemple d’insertion de données :
```sql
INSERT INTO film (id, title, year, genre) 
VALUES (1, 'Inception', 2010, 'Science-fiction');
```

---

## **Données à Modéliser**
Vous devez modéliser les données suivantes :

1. **Cinéma** : Films & Acteurs
2. **Librairie** : Livres & Auteurs
3. **Blog** : Articles & Éditeurs
4. **Transport** : Pays & Villes
5. **Langues** : Toutes les langues du monde
6. **Magasin en ligne** : Clients & Produits
7. **Hôpital** : Médecins & Patients
8. **École** : Étudiants & Cours

---

## **Instructions pour chaque exercice**
Pour chaque ensemble de données, vous devez :

1. **Nommer les tables**
2. **Lister les données à stocker**
3. **Définir chaque champ** :
   - Nom
   - Type (**Nombre, Chaîne de caractères, Texte, Date**)
   - **Obligatoire ou optionnel**
   - Pour les **chaînes de caractères**, préciser la **taille maximale**
4. **Déterminer l'identifiant unique** de chaque table (**clé primaire**)
5. **Créer la table en SQL**
6. **Exporter les tables dans un fichier SQL**

---

## **Critères d'évaluation**
Vous serez évalué sur les critères suivants :

- **Exhaustivité** : Votre investigation doit couvrir tous les aspects pertinents.
- **Cohérence des conventions** : Les noms de champs et tables doivent suivre une convention unique et logique.
- **Justification des champs optionnels** : L’optionalité doit être expliquée.
- **Utilisation de sources et standards existants** (si applicable, avec justification).
- **Fichier SQL exporté** : Doit inclure **votre nom** et le **sujet traité**.

---

## **Structure suggérée pour l'exercice**

| Table | Nom | Commentaire | Identifiant(s) |
|-------|-----|------------|---------------|
| Nom de la table | Description de la table | Explication | Clé primaire |

### **Champs**
| Nom | Type | Longueur | Obligatoire | Commentaire |
|------|------|---------|------------|------------|
| Nom du champ | Type de donnée | Taille max | Oui/Non | Explication |

---

Ce format vous aidera à structurer vos exercices et à bien organiser vos tables SQL.
