# Plan détaillé du module LBB (bases relationnelles uniquement)

## **Séance 1 : Introduction et positionnement**
- Présentation des objectifs du module.
- Historique des bases de données et rôle des SGBD.
- Introduction au **modèle relationnel** et ses principes (entités, attributs, relations).

**Supports et exercices**  
- [Théorie](session_1.md)  
- [Exercices](session_1_exo.md)  

---

## **Séance 2 : CRUD – Premières manipulations en SQL**
- Introduction au **langage SQL**.
- Explication des **commandes CRUD** :
  - `INSERT INTO`, `SELECT`, `UPDATE`, `DELETE`
- Installation de **MySQL + PHPMyAdmin**.
- Exercices pratiques avec **PHPMyAdmin**.

**Supports et exercices**  
- [Théorie](session_2.md)  
- [Exercices](session_2_exo.md)  

---

## **Séance 3 : Modélisation conceptuelle (MCD - Modèle Entité-Association)**
- Introduction aux **diagrammes Entité-Association**.
- Méthodologie de conception et **notation MERISE**.
- Cas pratique : **modélisation d'un domaine réel**.

**Supports et exercices**  
- [Théorie](session_3.md)  
- [Exercices](session_3_exo.md)  

---

## **Séance 4 : Passage du MCD au modèle relationnel et normalisation**
- Transformation du **MCD en modèle logique relationnel**.
- Explication des **3 premières formes normales** (1NF, 2NF, 3NF).
- Exemples et exercices de normalisation.

**Supports et exercices**  
- [Théorie](session_4.md)  
- [Exercices](session_4_exo.md)  

---

## **Séance 5 : Clés, relations et intégrité référentielle**
- Définition et rôle des **clés primaires, étrangères et index**.
- Contraintes d’intégrité (`FOREIGN KEY`, `ON DELETE CASCADE`).
- Exercices sur la **gestion des relations**.

**Supports et exercices**  
- [Théorie](session_5.md)  
- [Exercices](session_5_exo.md)  

---

## **Séance 6 : Jointures et manipulation avancée des données**
- `INNER JOIN`, `LEFT JOIN`, `RIGHT JOIN`, `UNION`, `GROUP BY`, `HAVING`.
- Indexation et optimisation des requêtes (`EXPLAIN`).
- Cas pratiques d’optimisation.

**Supports et exercices**  
- [Théorie](session_6.md)  
- [Exercices](session_6_exo.md)  

---

## **Séance 7 : Sécurité et bonnes pratiques en bases de données**
- Prévention des **attaques SQL Injection**.
- Gestion des **utilisateurs et permissions** (`GRANT`, `REVOKE`).
- Sauvegardes (`mysqldump`) et restaurations de bases.

**Supports et exercices**  
- [Théorie](session_7.md)  
- [Exercices](session_7_exo.md)  

---

## **Séance 8 : Connexion aux bases avec PHP & PDO**
- Introduction à **PDO** (Connexion, Requêtes préparées).
- Sécurisation des requêtes (`bindParam`).
- Manipulation des résultats (`fetch`, `fetchAll`).
- Mini-projet : Création d’un CRUD en PHP.

**Supports et exercices**  
- [Théorie](session_8.md)  
- [Exercices](session_8_exo.md)  

---

## **Séance 9 : Projet pratique – Conception et implémentation**
- Étude de **cahier des charges** et conception d’une base relationnelle.
- Travail en **groupe** : Création du MCD, MLD, requêtes SQL.
- Revue et corrections collectives.

**Supports et exercices**  
- [Théorie](session_9.md)  
- [Exercices](session_9_exo.md)  

---

## **Séance 10 : Examen final et validation des acquis**
- Test écrit et pratique sur la modélisation et SQL.
- Présentation et soutenance des projets.
- Discussion sur les bonnes pratiques.

**Supports et exercices**  
- [Théorie](session_10.md)  
- [Exercices](session_10_exo.md)  
