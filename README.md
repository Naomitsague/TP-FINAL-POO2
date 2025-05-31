# TP-FINAL-POO2
gestion des evenements
## Architecture & Conception

Le système repose sur une modélisation orientée objet claire et modulaire, respectant les bonnes pratiques et favorisant l’évolutivité.

- **Evenement (classe abstraite)**  
  Cette classe représente un événement générique avec les attributs communs suivants :  
  - `id` (String) : identifiant unique  
  - `nom` (String) : nom de l'événement  
  - `date` (LocalDateTime) : date et heure de l'événement  
  - `lieu` (String) : lieu de déroulement  
  - `capaciteMax` (int) : capacité maximale de participants  
  - `participants` (List<Participant>) : liste des participants inscrits  
  - `annule` (boolean) : indicateur d’annulation  
  Elle définit également des méthodes essentielles comme l’ajout d’un participant (`ajouterParticipant`), l’annulation (`annuler`) et une méthode abstraite `afficherDetails()` que les sous-classes doivent implémenter pour afficher les détails spécifiques.

- **Conference et Concert (classes concrètes)**  
  Deux types spécifiques d’événements héritent de `Evenement` :  
  - *Conference* : inclut des attributs supplémentaires comme `theme` et une liste d'`intervenants`.  
  - *Concert* : contient des attributs comme `artiste` et `genreMusical`.  
  Chaque classe surcharge la méthode `afficherDetails()` pour afficher les informations spécifiques.

- **Participant et Organisateur**  
  - *Participant* : représente un utilisateur inscrit aux événements, avec `id`, `nom` et `email`. Il agit aussi en tant qu’observateur dans le pattern Observer, recevant des notifications.  
  - *Organisateur* : hérite de Participant et gère une liste d’événements qu’il administre, ayant des droits étendus (création, modification, annulation).

- **GestionEvenements (Singleton)**  
  Cette classe assure la gestion centralisée des événements.  
  - Implémentée selon le pattern Singleton, elle garantit une instance unique accessible globalement.  
  - Elle stocke les événements dans une `Map<String, Evenement>` pour un accès efficace.  
  - Expose des méthodes pour ajouter, supprimer, rechercher et lister les événements.  
  - Gère les conflits (événements dupliqués) via des exceptions personnalisées.

- **Design Patterns utilisés**  
  - *Observer* : pour notifier en temps réel les participants lors des changements d’état d’un événement (ex : annulation).  
  - *Singleton* : pour le gestionnaire unique d’événements.  
  - *Factory* : pour la création flexible des objets événementiels (possibilité d’extension facile).  
  - *Strategy* : pour gérer différentes stratégies d’envoi de notifications (immédiates ou différées).

---

## Technologies

- **Java 17+** : langage principal pour le développement.  
- **Bibliothèques JSON** : Gson ou Jackson pour la sérialisation/désérialisation des données en format JSON.  
- **JUnit 5** : framework utilisé pour l’écriture et l’exécution des tests unitaires.

---

## Installation et utilisation

1. **Cloner le dépôt GitHub**  
```bash
git clone https://github.com/Naomitsague/TP-FINAL-POO2.git
