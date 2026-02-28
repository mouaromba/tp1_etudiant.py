Développement d’un Web Service SOAP en Java

Ce projet a pour objectif la conception et l’implémentation d’un service web SOAP en utilisant la technologie JAX-WS en Java. Le service a été développé sous l’environnement IntelliJ IDEA et testé à l’aide de l’outil SoapUI.

1. Objectifs du Projet
- Comprendre le fonctionnement des services web SOAP
-  Implémenter un service web avec JAX-WS.
-  Publier un endpoint via la classe Endpoint
-  Tester les opérations via SoapUI.
-  Manipuler des objets complexes (classe Etudiant)
-  Comprendre l’architecture des services web SOAP
-  Implémenter un Web Service en Java
-  Générer et exploiter un fichier WSDL
-  Manipuler les annotations JAX-WS
-  Tester un service SOAP avec SoapUI
-  Comprendre la sérialisation d’objets Java

2. Présentation des Services Web
Un Web Service est un système permettant la communication entre différentes applications via un réseau.
SOAP (Simple Object Access Protocol)
SOAP est un protocole basé sur XML qui permet l’échange structuré d’informations entre systèmes distribués.

Caractéristiques :
- Basé sur XML
- Utilise HTTP comme protocole de transport
- Génère un fichier WSDL
- Standard robuste et formel

3. Technologies Utilisées et rôle
   
<img width="337" height="289" alt="image" src="https://github.com/user-attachments/assets/c45a6004-24d6-442e-9097-fb9ab69a28c0" />


4. Architecture du Système
Le système repose sur une architecture client-serveur. Le service SOAP est publié localement à
l’adresse http://localhost:8888/. Le client (SoapUI) consomme le service via le fichier WSDL généré
automatiquement.

<img width="268" height="187" alt="image" src="https://github.com/user-attachments/assets/564d0197-f555-4dec-a743-40d8d440b301" />

5. Description des Classes
Application.java : Publie le service web via Endpoint.publish().
- MonserviceWeb.java : Contient les méthodes exposées (conversion, somme, getEtudiant)
   Classe MonserviceWeb
Contient les méthodes exposées :
 conversion(double mt)
Multiplie une valeur par 0.9.
public double conversion(double mt){
    return mt * 0.9;
} 

somme(double a, double b)
Retourne la somme de deux nombres.
public double somme(double a, double b){
    return a + b;
}

 getEtudiant(int identifiant)
Retourne un objet Etudiant.
public Etudiant getEtudiant(int identifiant){
    return new Etudiant(identifiant, "Mario", 19);
}

- Etudiant.java : Classe modèle sérialisable représentant un étudiant.
 Classe Etudiant
Classe représentant un étudiant.
Attributs :
private int identifiant;
private String nom;
private double moyenne;
Elle implémente :
implements Serializable
Pourquoi ?Pour permettre la sérialisation de l’objet en XML lors de l’échange SOAP.

-  Main.java : Classe de test console.
   lasse Application
Permet de publier le service :
Endpoint.publish("http://localhost:8888/", new MonserviceWeb());
URL du WSDL :
http://localhost:8888/?wsdl

6. Fonctionnalités Implémentées
- conversion(double mt) : applique un coefficient multiplicatif.
- - somme(double a, double b) :retourne l’addition de deux nombres.
- getEtudiant(int identifiant) : retourne un objet Etudiant.

7. Déploiement du Service
Étapes :
Ouvrir le projet dans IntelliJ
Exécuter Application.java
Vérifier le message :


7. Tests et Validation
Les tests ont été réalisés avec SoapUI en important le WSDL. Chaque méthode a été exécutée
avec différents paramètres afin de valider le bon fonctionnement du service.
Le service web est déployé
Accéder à :
http://localhost:8888/?wsdl
Tests avec SoapUI
Étapes :
Ouvrir SoapUI  
Créer un nouveau projet SOAP  
Importer l’URL WSDL  
Tester les méthodes
Exemple Test conversion
Entrée :
<mt>100</mt>
Résultat :
90.0

Exemple Test somme
Entrée :
<a>5</a>
<b>3</b>
Résultat :
8

Exemple Test getEtudiant
Entrée :
<identifiant>1</identifiant>
Sortie :
<return>
   <identifiant>1</identifiant>
   <nom>Mario</nom>
   <moyenne>19</moyenne>
</return>

 Résultats et Analyse
Le service fonctionne correctement :
Les méthodes sont accessibles
Le WSDL est généré automatiquement
Les objets sont correctement sérialisés
Les tests SoapUI sont concluants
Cela démontre une bonne compréhension des services SOAP et de JAX-WS.

<img width="1332" height="600" alt="image" src="https://github.com/user-attachments/assets/47202746-0428-4bcc-af49-4780315fdc16" />

<img width="1349" height="722" alt="image" src="https://github.com/user-attachments/assets/134efeb5-4345-4f2c-891e-4054f18c65bf" />

<img width="952" height="442" alt="image" src="https://github.com/user-attachments/assets/d8c0b1b3-1ff3-4357-802f-45e120eb67b1" />


Difficultés Rencontrées
Configuration du JDK compatible JAX-WS
Compréhension du WSDL
Gestion des annotations
Débogage des erreurs de déploiement

 Améliorations Possibles
Ajouter une base de données
Implémenter la gestion des exceptions SOAP
Ajouter une authentification
Comparer avec une version REST
Déployer sur un serveur applicatif (Tomcat)

Il constitue une base solide pour comprendre les architectures distribuées et les communications inter-applicatives.

Conclusion
Ce projet a permis de comprendre les principes fondamentaux des services web SOAP,notamment la publication d’un endpoint, la génération automatique du WSDL et la communication
client-serveur en XML. Il constitue une base solide pour l’étude des architectures orientées
services. Ce projet nous a permis de :
Comprendre l’architecture des services web SOAP
Implémenter un Web Service avec JAX-WS
Générer et exploiter un fichier WSDL
Tester un service avec SoapUI




