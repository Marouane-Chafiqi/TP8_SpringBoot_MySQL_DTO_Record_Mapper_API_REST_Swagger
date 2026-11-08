# TP 8 : Student API

Nom : [Nom et prénom]
Filière : [Filière]

## C'est quoi ce projet

Une petite API REST pour gérer des étudiants (ajouter, afficher, chercher par id, modifier, supprimer). Elle est faite avec Spring Boot et les données sont enregistrées dans MySQL. On teste tout avec Swagger.

Un étudiant a : id, prénom, nom, email, filière, âge.

## Outils utilisés

- Java 17 et Maven
- Spring Boot 3.5.11 (Web, Data JPA, Validation)
- MySQL (avec XAMPP et phpMyAdmin)
- Swagger UI (springdoc)
- IntelliJ IDEA

## Organisation du code

```
controller   -> reçoit les requêtes
service      -> la logique
repository   -> parle avec la base
mapper       -> passe de l'entité au DTO et inversement
dto          -> les objets envoyés et reçus (records)
entity       -> la table students
exception    -> les erreurs (404, 400, 500)
```

## Comment lancer

1. Démarrer MySQL dans XAMPP.
2. Ouvrir le projet dans IntelliJ.
3. Vérifier `src/main/resources/application.properties` (le mot de passe root est vide chez moi).
4. Lancer `StudentApiApplication`.
5. Ouvrir Swagger : http://localhost:8080/swagger-ui/index.html

La base `student_db` et la table `students` sont créées toutes seules.

## Les routes

| Méthode | URL | Ce que ça fait |
|---|---|---|
| POST | /api/students | ajouter un étudiant (201) |
| GET | /api/students | afficher tous les étudiants |
| GET | /api/students/{id} | chercher un étudiant |
| PUT | /api/students/{id} | modifier un étudiant |
| DELETE | /api/students/{id} | supprimer un étudiant (204) |

## Mes tests

### 1. La table au départ

Au début la table `students` est vide dans phpMyAdmin.

<img width="681" height="338" alt="Capture d&#39;écran 2026-11-08 161822" src="https://github.com/user-attachments/assets/130b8daf-f370-450d-9d3f-0e95df2b9e36" />


### 2. Chercher un étudiant qui n'existe pas

Comme la table est vide, `GET /api/students/1` renvoie une erreur 404 avec le message "Étudiant introuvable avec l'id : 1".

<img width="1008" height="488" alt="Capture d&#39;écran 2026-11-08 162004" src="https://github.com/user-attachments/assets/1c8b684f-113c-4434-a792-059f58787b3b" />


### 3. Ajouter un étudiant

Avec `POST /api/students` j'ajoute Zineb Halim. Le serveur répond 201 (Created) et renvoie l'étudiant avec son id (7).

<img width="1036" height="324" alt="Capture d&#39;écran 2026-11-08 162406" src="https://github.com/user-attachments/assets/016cfedb-82d1-47e8-936b-29ed023ec12e" />


### 4. Chercher un étudiant par id

`GET /api/students/6` renvoie 200 avec les infos d'Amine Samed.

<img width="1019" height="512" alt="Capture d&#39;écran 2026-11-08 162423" src="https://github.com/user-attachments/assets/640e3265-0808-4b3a-892e-015e3ebc2692" />


### 5. La table après les tests

Dans phpMyAdmin on voit les étudiants enregistrés dans MySQL.

<img width="807" height="288" alt="Capture d&#39;écran 2026-11-08 162505" src="https://github.com/user-attachments/assets/3420de8c-77c2-4cd7-9d7e-b4382a852e79" />



