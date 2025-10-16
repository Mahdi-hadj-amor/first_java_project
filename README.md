# 📋 Gestion Facture

[![Java](https://img.shields.io/badge/Java-1.8+-blue.svg)](https://www.oracle.com/java/)
[![Swing](https://img.shields.io/badge/Swing-GUI-orange.svg)](https://docs.oracle.com/javase/tutorial/uiswing/)
[![SQL Server](https://img.shields.io/badge/Database-SQL%20Server-red.svg)](https://www.microsoft.com/en-us/sql-server)

Une application Java Swing moderne pour la gestion simplifiée des factures, clients et articles. Simplifiez vos transactions commerciales avec une interface utilisateur intuitive et une connexion sécurisée à une base de données SQL Server..

## ✨ Fonctionnalités

- 🔐 **Authentification sécurisée** : Connexion utilisateur avec vérification des identifiants.
- 🏠 **Tableau de bord** : Page d'accueil avec aperçu des fonctionnalités.
- 👥 **Gestion des clients** : Ajouter, modifier, supprimer et consulter les informations clients (nom, matricule fiscale, adresse, téléphone).
- 📦 **Gestion des articles** : Gérer le stock, les prix HTVA et les taux de TVA pour chaque article.
- 📊 **Interface table** : Affichage des données dans des tableaux interactifs avec double-clic pour modification.
- 🔄 **Mises à jour en temps réel** : Recharge automatique des données après chaque opération CRUD.
- 🎨 **Design moderne** : Interface Swing avec couleurs et layouts adaptés pour une expérience utilisateur fluide.

## 🛠️ Prérequis

Avant d'installer et d'exécuter l'application, assurez-vous d'avoir :

- **Java JDK 1.8 ou supérieur** : [Télécharger ici](https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html)
- **SQL Server** : Instance locale ou distante configurée.
- **Driver JDBC MSSQL** : Inclus dans le projet (`mssql-jdbc-12.10.0.jre8.jar`).
- **Eclipse IDE** (recommandé) : Pour l'importation et l'exécution du projet.

## 🚀 Installation

1. **Cloner ou télécharger le projet** :
   ```bash
   git clone https://github.com/votre-repo/GestionFacture.git
   cd GestionFacture
   ```

2. **Importer dans Eclipse** :
   - Ouvrez Eclipse.
   - Sélectionnez `File > Import > Existing Projects into Workspace`.
   - Choisissez le dossier `GestionFacture` et cliquez sur `Finish`.

3. **Configurer la base de données** :
   - Créez une base de données SQL Server nommée `DB_GestionFacture`.
   - Exécutez les scripts SQL suivants pour créer les tables :
     ```sql
     CREATE TABLE Utilisateur (
         Login VARCHAR(50) PRIMARY KEY,
         Password VARCHAR(50) NOT NULL
     );

     CREATE TABLE Client (
         Code_Client INT IDENTITY(1,1) PRIMARY KEY,
         Nom_Prenom VARCHAR(100) NOT NULL,
         Matricule_Fiscale VARCHAR(50) UNIQUE NOT NULL,
         Adresse VARCHAR(255),
         Num_Telephone VARCHAR(20)
     );

     CREATE TABLE Article (
         Code_Article INT IDENTITY(1,1) PRIMARY KEY,
         Nom_Article VARCHAR(100) NOT NULL,
         Qte_Stock INT NOT NULL,
         PUHTVA DECIMAL(10,2) NOT NULL,
         TVA DECIMAL(5,2) NOT NULL
     );
     ```
   - Insérez un utilisateur par défaut :
     ```sql
     INSERT INTO Utilisateur (Login, Password) VALUES ('admin', 'admin');
     ```

4. **Mettre à jour la connexion DB** :
   - Ouvrez `src/com/gestionfacture/DatabaseConnection.java`.
   - Modifiez l'URL de connexion si nécessaire :
     ```java
     private static final String URL = "jdbc:sqlserver://VOTRE_SERVEUR:1433;databaseName=DB_GestionFacture;integratedSecurity=true;trustServerCertificate=true";
     ```

5. **Compiler et exécuter** :
   - Dans Eclipse, faites un clic droit sur le projet > `Run As > Java Application`.
   - Sélectionnez `MainWindow` comme classe principale.

## 📖 Utilisation

1. **Démarrage** : Lancez l'application. La page de connexion s'affiche.
2. **Connexion** : Entrez vos identifiants (par défaut : `admin` / `admin`).
3. **Navigation** :
   - 🏠 **Accueil** : Vue d'ensemble de l'application.
   - 👥 **Gestion Client** : Ajoutez/modifiez/supprimez des clients via le formulaire et le tableau.
   - 📦 **Gestion Article** : Gérez les articles avec validation des champs (quantité > 0, prix > 0).
   - ℹ️ **À propos** : Informations sur l'application.
   - 🚪 **Déconnexion** : Retour à la page de connexion.
4. **Opérations CRUD** :
   - **Ajouter** : Remplissez les champs et cliquez sur "Ajouter".
   - **Modifier** : Double-cliquez sur une ligne du tableau, modifiez les champs, puis "Modifier".
   - **Supprimer** : Sélectionnez une ligne et cliquez sur "Supprimer" (confirmation requise).

## 🏗️ Architecture

- **MainWindow.java** : Fenêtre principale avec sidebar et gestion des panneaux.
- **ClientPanel.java** : Panneau dédié à la gestion des clients.
- **ArticlePanel.java** : Panneau dédié à la gestion des articles.
- **DatabaseConnection.java** : Classe utilitaire pour la connexion DB.
- **Base de données** : Tables `Utilisateur`, `Client`, `Article` pour persister les données.

## 🤝 Contribution

Les contributions sont les bienvenues ! Pour contribuer :

1. Forkez le projet.
2. Créez une branche pour votre fonctionnalité (`git checkout -b feature/nouvelle-fonction`).
3. Commitez vos changements (`git commit -m 'Ajout de nouvelle fonctionnalité'`).
4. Pushez vers la branche (`git push origin feature/nouvelle-fonction`).
5. Ouvrez une Pull Request.

## 📄 Licence

Ce projet est sous licence MIT. Voir le fichier `LICENSE` pour plus de détails.

## 📞 Support

Pour des questions ou des problèmes, ouvrez une issue sur GitHub ou contactez l'équipe de développement.

---

Développé avec ❤️ en Java Swing pour simplifier la gestion des factures.
