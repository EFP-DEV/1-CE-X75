# **Introduction to Database Concepts**

## **1. What is a Database?**
A **database** is an organized collection of data that is stored and managed electronically. Databases allow users to efficiently store, retrieve, and manipulate data using specialized software known as **Database Management Systems (DBMS).**

### **Types of Databases**
- **Relational Databases (RDBMS):** Use structured tables to store data and support SQL queries.
- **NoSQL Databases:** Store data in a variety of formats such as key-value, document, or graph-based structures.

## **2. Tables in a Database**
A **table** (or **relation**) is the fundamental building block of a relational database. A table consists of **rows (records)** and **columns (attributes).**

Example Table (Student Data):

```plaintext
| StudentID | Name  | Age | Major            |
|-----------|-------|-----|------------------|
| 101       | Alice | 21  | Computer Science |
| 102       | Bob   | 22  | Mathematics      |
```

## **3. Schema: The Structure of a Database**
A **schema** defines the structure of a database, including the organization of tables, columns, data types, and relationships between tables. The schema provides a blueprint for how data is stored and accessed.

## **4. Rows and Columns**
- **Row (Record or Tuple):** A single entry in a table that contains values for each column.
- **Column (Attribute):** A specific data field in a table that holds information of a particular type.

Example:
- In the `Student` table above, **each row represents a different student**.
- **Columns define the type of information stored** (e.g., Name, Age, Major).

## **5. Relationships Between Tables**
In relational databases, **relations** are established between tables to avoid data redundancy and ensure efficient data management.

### **Types of Relationships:**
- **One-to-One (1:1):** Each record in Table A maps to exactly one record in Table B.
- **One-to-Many (1:M):** A record in Table A can be associated with multiple records in Table B.
- **Many-to-Many (M:N):** Multiple records in Table A can be related to multiple records in Table B (requires a junction table).

Example Relationship:
- A `Students` table and an `Enrollments` table can be linked using a **StudentID** as a foreign key.

## **6. Keys in a Database**
### **Primary Key**
A **Primary Key** uniquely identifies each record in a table. It must be unique and cannot contain NULL values.

Example:
```sql
CREATE TABLE Students (
    StudentID INT PRIMARY KEY,
    Name VARCHAR(100),
    Age INT,
    Major VARCHAR(50)
);
```
- `StudentID` is the **primary key** in this table.

### **Foreign Key**
A **Foreign Key** establishes a relationship between two tables by referencing the **Primary Key** of another table.

Example:
```sql
CREATE TABLE Enrollments (
    EnrollmentID INT PRIMARY KEY,
    StudentID INT,
    CourseID INT,
    FOREIGN KEY (StudentID) REFERENCES Students(StudentID)
);
```
- `StudentID` in `Enrollments` references the `StudentID` in `Students`.

## **7. Indexes for Faster Queries**
An **index** is a database structure that improves the speed of data retrieval operations. Indexes function like a table of contents for a book, helping the database locate records efficiently.

### **Types of Indexes:**
- **Clustered Index:** Determines the physical order of data in a table (each table can have one).
- **Non-Clustered Index:** Creates a separate structure to improve query performance.

Example:
```sql
CREATE INDEX idx_student_name ON Students(Name);
```
- This index speeds up searches for students by `Name`.

## **8. Summary**
- A **database** is an organized system for storing and managing data.
- A **table** consists of **rows (records)** and **columns (attributes).**
- A **schema** defines the structure of a database.
- **Relationships** between tables help maintain data integrity.
- **Primary keys** uniquely identify records, while **foreign keys** establish relationships.
- **Indexes** improve query performance.



# Exercice

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

