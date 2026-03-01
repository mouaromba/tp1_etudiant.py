Développement d’une API REST de Gestion des Étudiants avec Flask

Ce tp consiste à développer une API REST en Python permettant la gestion d’une liste d’étudiants.
L’API a été développée avec le framework Flask, un micro-framework léger et flexible largement utilisé pour la création de services web.
Ce projet permet de comprendre les principes fondamentaux des architectures REST ainsi que la manipulation des méthodes HTTP.

1. Contexte et Problématique
Les applications modernes nécessitent des systèmes capables de communiquer entre eux de manière standardisée.
Les API REST sont aujourd’hui largement utilisées pour :
- Les applications mobiles
- Les applications web
- Les systèmes distribués
- Les architectures microservices

La problématique de ce projet est la suivante :
Comment concevoir et implémenter une API REST simple permettant la gestion des étudiants en utilisant Flask ?


2- Objectifs du Projet
Les objectifs pédagogiques sont :
- Comprendre l’architecture REST
- Manipuler les méthodes HTTP (GET, POST, PUT, DELETE)
- Manipuler le format JSON
- Créer des endpoints dynamiques
- Tester une API avec un outil comme Postman


3.  Présentation des API REST
Définition
REST (Representational State Transfer) est un style architectural basé sur le protocole HTTP.
Principes REST
- Architecture client-serveur
- Stateless (sans état)
- Utilisation des méthodes HTTP
- Manipulation des ressources via URL
- Format JSON pour les échanges

4. Méthodes HTTP utilisées

<img width="292" height="253" alt="image" src="https://github.com/user-attachments/assets/d5ab5049-dd2d-4e7e-9bb6-de6ef4cefa64" />

5. Architecture Générale du Système
 Architecture Simplifiée
L’architecture est basée sur un modèle Client–Serveur.

<img width="305" height="189" alt="image" src="https://github.com/user-attachments/assets/b2433aa7-6eea-41ca-a678-b8c2592bfcc8" />

6. Technologies Utilisées

<img width="337" height="304" alt="image" src="https://github.com/user-attachments/assets/6073610b-ec1e-4c0e-b146-09fab161bac3" />

7. Implémentation Technique
Initialisation de l’Application

<img width="333" height="52" alt="image" src="https://github.com/user-attachments/assets/df7898eb-8ea8-4f50-a93b-7ae740c326b2" />

- Flask() initialise l’application
- jsonify() transforme les objets Python en JSON
- request.get_json() récupère les données envoyées par le client

8. Base de Données Simulée
Les données sont stockées en mémoire (structure temporaire). Les étudiants sont stockés dans une liste Python :

<img width="357" height="126" alt="image" src="https://github.com/user-attachments/assets/65350889-0b2d-47bd-bfc1-725423dca7fb" />

Il s’agit d’un stockage temporaire en mémoire (pas de base de données réelle)

9. Description Détaillée des Endpoints
Tester si le serveur fonctionne: @app.route('/')
Méthode : GET
URL : http://localhost:5000/

<img width="1353" height="688" alt="image" src="https://github.com/user-attachments/assets/88eabc13-6df2-4987-9b2e-c17788b31a2b" />

Réponse : Bienvenue dans l'API de gestion des étudiants

<img width="734" height="251" alt="image" src="https://github.com/user-attachments/assets/c9ca30a7-70ad-4e96-9021-085d06308e02" />


Lister tous les étudiants:

<img width="304" height="36" alt="image" src="https://github.com/user-attachments/assets/6229ab28-c533-4afd-b269-200f745281f3" />

- URL : GET http://localhost:5000/students
- Réponse :

<img width="479" height="432" alt="image" src="https://github.com/user-attachments/assets/7d2fa1de-0027-48e7-89b7-12b2b656b102" />


Ajouter un étudiant

<img width="334" height="38" alt="image" src="https://github.com/user-attachments/assets/877278ff-4c1e-4e28-9c81-e1a0adea5377" />

URL :
POST http://localhost:5000/students
Corps JSON :
{
  "name": "Ali",
  "age": 20
}

Réponse :

{
  "id": 5,
  "name": "Ali",
  "age": 20
}

Code retour : 201 (Created)

Afficher un étudiant par ID

<img width="377" height="39" alt="image" src="https://github.com/user-attachments/assets/065ed3ef-cc69-4b28-bea2-b0f391af6084" />

Exemple :
GET http://localhost:5000/students/1

Réponse :

{
  "id":1,
  "name":"Shama",
  "age":21
}

Si l’étudiant n’existe pas :

{
  "erreur": "L'étudiant n'existe pas"
}

Code retour : 404

Modifier un étudiant

<img width="374" height="37" alt="image" src="https://github.com/user-attachments/assets/3a4d4347-1806-4355-8800-d045fc09cd99" />

Exemple :
PUT http://localhost:5000/students/1

Corps JSON :

{
  "name": "Nouveau Nom",
  "age": 22
}

Réponse :

{
  "id":1,
  "name":"Nouveau Nom",
  "age":22
}

Supprimer un étudiant

<img width="390" height="41" alt="image" src="https://github.com/user-attachments/assets/72202aa0-612e-4c39-b5b4-6eabc9c8ea3e" />

Exemple :
DELETE http://localhost:5000/students/1
Réponse :

{
  "message": "Etudiant supprimé"
}

 10. Résumé de méthodes (la partie 9 est très longue donc je l'ai résumé pour une meilleure compréhension)
  
- Route Racine : GET /
- Permet de vérifier que le serveur fonctionne.
- Lister les étudiants : GET /students
- Retourne la liste complète au format JSON.
- Ajouter un étudiant :POST /students
   Reçoit un JSON :
  
{
  "name": "Schama",
  "age": 21
}

- Retourne l’étudiant créé avec un identifiant automatique. Code HTTP : 201
- Afficher un étudiant par ID: GET /students/<id>
- Retourne un étudiant spécifique ou une erreur 404.
- Modifier un étudiant: PUT /students/<id>
- Met à jour les données d’un étudiant.
- Supprimer un étudiant: DELETE /students/<id>
- Supprime l’étudiant correspondant.

11. Tests et Validation
Les tests ont été réalisés avec Postman.
- Test GET : Retour correct des données JSON.
- Test POST : Ajout réussi avec code 201.
- Test PUT: Modification effective des données.
- Test DELETE: Suppression confirmée.

12. Lancement de l’Application
À la fin du fichier :
if __name__ == '__main__':
    app.run(debug=True

Etapes pour exécuter :
- Installer Flask : pip install flask
- Lancer le fichier : python TP1_etdt.py
- Accéder à : http://localhost:5000

13. Analyse des Résultats
L’API fonctionne correctement :
- Toutes les routes répondent correctement.
- Les codes HTTP sont respectés.
- Les données sont correctement sérialisées en JSON.
- Les erreurs sont gérées avec des codes appropriés.


14. Limites du Projet
- Les données ne sont pas persistantes.
- Pas de base de données réelle.
- Pas de validation avancée.
- Pas d’authentification.
- Pas de gestion des exceptions avancées.

15.  Perspectives d’Amélioration
Intégration d’une base de données (SQLite, MySQL)
- Ajout d’un ORM (SQLAlchemy)
- Validation avec Marshmallow
- Authentification JWT
- Documentation Swagger
- Déploiement sur un serveur distant

Ce tp met en pratique les concepts fondamentaux des API REST à travers le framework Flask.
Nous avons appris à travers cela :
- Structurer une API
- Manipuler les méthodes HTTP
- Utiliser JSON
- Tester un service web
- Comprendre l’architecture client-serveur
Ce travail constitue une base pour le développement d’applications web modernes et de systèmes distribués.
