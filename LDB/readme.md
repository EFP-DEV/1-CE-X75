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
| StudentID | Name  | Age | Major            |
|-----------|-------|-----|------------------|
| 101       | Alice | 21  | Informatique     |
| 102       | Bob   | 22  | Mathématiques    |
```

## **3. Schéma : La Structure d'une Base de Données**
Un **schéma** définit la structure d'une base de données, y compris l'organisation des tables, des colonnes, des types de données et des relations entre les tables. Le schéma fournit un plan directeur pour le stockage et l'accès aux données.

## **4. Lignes et Colonnes**
- **Ligne (Enregistrement ou Tuple) :** Une entrée unique dans une table qui contient des valeurs pour chaque colonne.
- **Colonne (Attribut) :** Un champ de données spécifique dans une table qui contient des informations d'un type particulier.

Exemple :
- Dans la table `Student` ci-dessus, **chaque ligne représente un étudiant différent**.
- **Les colonnes définissent le type d'information stockée** (par exemple, Nom, Âge, Filière).

## **5. Relations Entre les Tables**
Dans les bases de données relationnelles, des **relations** sont établies entre les tables pour éviter la redondance des données et assurer une gestion efficace des données.

### **Types de Relations :**
- **Un-à-Un (1:1) :** Chaque enregistrement de la Table A correspond à exactement un enregistrement de la Table B.
- **Un-à-Plusieurs (1:M) :** Un enregistrement de la Table A peut être associé à plusieurs enregistrements de la Table B.
- **Plusieurs-à-Plusieurs (M:N) :** Plusieurs enregistrements de la Table A peuvent être liés à plusieurs enregistrements de la Table B (nécessite une table de jonction).

Exemple de Relation :
- Une table `Students` et une table `Enrollments` peuvent être liées en utilisant un **StudentID** comme clé étrangère.

## **6. Clés dans une Base de Données**
### **Clé Primaire**
Une **Clé Primaire** identifie de manière unique chaque enregistrement dans une table. Elle doit être unique et ne peut pas contenir de valeurs NULL.

Exemple :
```sql
CREATE TABLE Students (
    StudentID INT PRIMARY KEY,
    Name VARCHAR(100),
    Age INT,
    Major VARCHAR(50)
);
```
- `StudentID` est la **clé primaire** dans cette table.

### **Clé Étrangère**
Une **Clé Étrangère** établit une relation entre deux tables en référençant la **Clé Primaire** d'une autre table.

Exemple :
```sql
CREATE TABLE Enrollments (
    EnrollmentID INT PRIMARY KEY,
    StudentID INT,
    CourseID INT,
    FOREIGN KEY (StudentID) REFERENCES Students(StudentID)
);
```
- `StudentID` dans `Enrollments` référence le `StudentID` dans `Students`.

## **7. Index pour des Requêtes Plus Rapides**
Un **index** est une structure de base de données qui améliore la vitesse des opérations de récupération de données. Les index fonctionnent comme une table des matières pour un livre, aidant la base de données à localiser les enregistrements de manière efficace.

### **Types d'Index :**
- **Index Clusterisé :** Détermine l'ordre physique des données dans une table (chaque table peut en avoir un).
- **Index Non-Clusterisé :** Crée une structure séparée pour améliorer les performances des requêtes.

Exemple :
```sql
CREATE INDEX idx_student_name ON Students(Name);
```
- Cet index accélère les recherches d'étudiants par `Name`.

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

### **Données à Modéliser**
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

