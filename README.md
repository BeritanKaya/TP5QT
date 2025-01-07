# TP5QT


# Requête SQL - Interface Graphique Dynamique

Créer une interface graphique dynamique avec lecture et écriture de données depuis/vers une BDD
Ce projet est une application basée sur Qt qui permet de lire, afficher et modifier les données d'une base de données MySQL via une interface graphique dynamique. L'objectif est de proposer une solution intuitive et interactive pour gérer les données stockées dans une base de données.


---

##  Objectif

Créer une interface graphique dynamique avec les fonctionnalités suivantes :
- Connexion à une base de données MySQL.
- Lecture et affichage des données d'une table sous forme de tableau.
- Modification des données directement dans l'interface.
- Mise à jour automatique des données dans la base après modification.

---

##  Fonctionnalités

-  Connexion à une base de données MySQL avec des paramètres configurables.
-  Interface graphique intuitive construite avec **Qt Designer**.
-  Affichage des données dans un tableau interactif (**QTableWidget**).
-  Édition des cellules du tableau et mise à jour automatique dans la base de données.

---

### Prérequis
- **Qt** (version 5 ou supérieure).
- Un compilateur compatible **C++17**.
- **MySQL** installé et configuré.

### Configuration de la base de données
1. Créez une base de données nommée `test`.
2. Ajoutez une table nommée `jeu` avec les colonnes suivantes :
   - **`id`** : Identifiant unique (int, clé primaire).
   - **`Nom`** : Nom de l'élément (varchar).
   - **`club`** : Club associé (varchar).
   - **`note`** : Note associée (int).

   Exemple de requête SQL pour créer la table :
   ```sql
   CREATE TABLE jeu (
       id INT PRIMARY KEY AUTO_INCREMENT,
       Nom VARCHAR(255),
       club VARCHAR(255),
       note INT
   );
   ```
   
Exemple de requête SQL pour inserez des données dans la table :
   ```sql
   INSERT INTO jeu (Nom, club, note) VALUES
   ('Ronaldo', 'Madrid', 10),
   ('Grizou', 'barca', 3)
```

Extrait de code main.cpp pour etablir une connexion avec la bdd Mysql :
```
#include <QtSql/QSqlDatabase>
#include <QtSql/QSqlError>
#include <QDebug>

// Créer une connexion à la base de données MySQL
QSqlDatabase db = QSqlDatabase::addDatabase("QMYSQL");
db.setDatabaseName("test");  // Nom de la base de données
db.setHostName("127.0.0.1");  // Hôte MySQL
db.setPort(3306);  // Port MySQL
db.setUserName("etudiant");  // Nom d'utilisateur
db.setPassword("Passciel2");  // Mot de passe

// Ouvrir la connexion
if (db.open()) {
    qDebug() << "Connexion réussie à la base de données !";
} else {
    qDebug() << "Erreur de connexion :" << db.lastError().text();
}
```

Code pour mettre sa bdd dans Github :
```
mysqldump -u etudiant -p test > test.sql

```


