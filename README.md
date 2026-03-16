<h1 align="center">Système de gestion des données pour agence de voyage</h1> 

![Langage](https://img.shields.io/badge/Langage_-Java_23-d2b48c?style=for-the-badge&logo=openjdk&logoColor=white) 
![Base de données](https://img.shields.io/badge/Base_de_données-MySQL-00618E?style=for-the-badge&logo=mysql&logoColor=white) 
![Infrastructure](https://img.shields.io/badge/Conteneur-Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)

<p align="center">
  <img src="assets/banner.webp" alt="Banner" width="60%">
</p>

Cette application JavaFX est conçue comme un espace de travail dédié aux conseillers d'une agence de voyage.  
Elle leur permet de gérer facilement les réservations des clients, en accédant aux informations préremplies sur les vols et les compagnies aériennes, mises à jour par l'administration.  

L’application repose sur une **base de données MySQL relationnelle** et offre un accès différencié :  
- **Les conseillers** gèrent uniquement les clients et leurs réservations.  
- **L’administration** gère les vols, les compagnies aériennes et les conseillers.

---

## Téléchargement

Vous pouvez télécharger la version stable prête à l'emploi ici :

<p align="center">
  <a href="https://github.com/rmdair/Gestion_Reservations_JavaFX/releases/tag/v1.0.0">
    <img src="https://img.shields.io/badge/VOIR_LA_VERSION_V1.0.0-34495e?style=for-the-badge" alt="Version 1.0.0">
  </a>
</p>


## Modèle conceptuel de données (MCD)

Voici la structure des principales entités du projet :

<p align="center">
  <img src="docs/Modele_Conceptuel_Donnees.png" alt="MCD" width="80%">
</p>

Les réservations constituent l'élément central du modèle. 
Chacune d'entre elles est associée au client qui l'effectue, au conseiller qui la gère, ainsi qu’au vol correspondant.


## Fonctionnalités

Les conseillers peuvent :  
- Ajouter, modifier ou annuler une réservation pour un client  
- Consulter les vols disponibles et les compagnies opératrices  
- Accéder à une vue globale des réservations au format Excel  
- Gérer les clients et suivre leur historique de voyage  


## Arborescence du projet 

```plaintext
docker/                → Configuration du conteneur MySQL
├── docker-compose.yml → Déploiement de la base de données
├── initialization.sql → Script d'initialisation SQL

src/                   → Code source du projet
├── config/            → Gestion de la connexion MySQL
│   ├── DatabaseConnection.java
│   ├── test.java
├── models/            → Définition des entités 
│   ├── Client.java
│   ├── TravelAgent.java
│   ├── Airline.java
│   ├── Flight.java
│   ├── Reservation.java
├── dao/               → Accès aux données (CRUD)
│   ├── ClientDAO.java
│   ├── TravelAgentDAO.java
│   ├── AirlineDAO.java
│   ├── FlightDAO.java
│   ├── ReservationDAO.java
├── fx/                → Interface graphique en JavaFX
│   ├── ClientFX.java
│   ├── TravelAgentFX.java
│   ├── AirlineFX.java
│   ├── FlightFX.java
│   ├── ReservationFX.java
│   ├── ExcelViewFX.java
│   ├── Main.java      → Classe principale
```


## Commandes Docker

**Démarrer la base de données MySQL**  
```bash
docker-compose up -d
```

**Accéder à MySQL dans le conteneur**  
```bash
docker exec -it project_travel_agency mysql -u project_travel_agency -p      
```
ou
```bash
docker exec -it project_travel_agency mysql -u root -p
```

**Arrêter et supprimer le conteneur**  
```bash
docker-compose down
```


## Lancer l'interface JavaFX

### Méthode recommandée : exécution depuis Eclipse  
L'interface graphique peut être lancée directement depuis **l'IDE Eclipse**, ce qui constitue la solution la plus simple :  
1. **Ouvrir le projet dans Eclipse**  
2. **Ajouter les bibliothèques requises** :  
   - Télécharger **JavaFX SDK** depuis [le site officiel](https://openjfx.io/)  
   - Télécharger le **connecteur MySQL** depuis [le site officiel](https://www.mysql.com/products/connector/)  
   - Ajouter ces bibliothèques au projet via **Build Path → Configure Build Path → Add External JARs**  
3. **Sélectionner `Main.java` dans le package `fx`**  
4. **Cliquer sur Run** pour exécuter l'application  


### Exécution depuis le terminal  
L'application peut également être exécutée en dehors de l'IDE avec la commande suivante :  
```bash
java -p "javafx-sdk-23.0.1/lib" --add-modules javafx.controls,javafx.base,javafx.fxml,javafx.graphics,javafx.media,javafx.web --add-opens=javafx.graphics/javafx.scene=ALL-UNNAMED --add-exports javafx.base/com.sun.javafx.event=ALL-UNNAMED -jar executable.jar
```


## Documentation
Deux rapports détaillés du projet sont disponibles :  

**Version française** : [Lire le rapport en français](docs/gestion-donnees-reservations-FR.pdf)   
**Version anglaise** : [Read the report in English](docs/reservation-data-management-EN.pdf)  


## Aperçu de l'application

### Interface d'accueil
<p align="center">
  <img src="assets/update_client.webp" alt="Accueil" width="80%">
</p>

### Onglet des réservations
<p align="center">
  <img src="assets/update_reservation.webp" alt="Réservations" width="80%">
</p>

### Onglet des vols
<p align="center">
  <img src="assets/flights.webp" alt="Vols" width="80%">
</p>

### Onglet des compagnies aériennes
<p align="center">
  <img src="assets/airlines.webp" alt="Compagnies" width="80%">
</p>

### Onglet des conseillers
<p align="center">
  <img src="assets/travel_agents.webp" alt="Conseillers" width="80%">
</p>

### Onglet Excel
<p align="center">
  <img src="assets/excel_window.webp" alt="Excel" width="80%">
</p>


## Pour cloner et démarrer ce projet  

```bash
git clone https://github.com/rmdair/Gestion_Reservations_JavaFX.git

cd Gestion_Reservations_JavaFX

# Lancer l'application (vérifiez que le chemin du SDK JavaFX est correct)
java -p "javafx-sdk-23.0.1/lib" --add-modules javafx.controls,javafx.base,javafx.fxml,javafx.graphics,javafx.media,javafx.web --add-opens=javafx.graphics/javafx.scene=ALL-UNNAMED --add-exports javafx.base/com.sun.javafx.event=ALL-UNNAMED -jar executable.jar
```

