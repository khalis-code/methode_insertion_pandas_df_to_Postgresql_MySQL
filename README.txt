Méthodes le plus rapides pour insérer données en masse Pandas dans PostgreSQL et MySQL 

Nous allons utiliser 
-PostgreSQL 
-MySQL Workbench 

Si vous souhaitez travailler avec moi, vous devez d'abord créer les table dans la base 
de données Postgres et MySQL Workbench 

--------------------------------------------------------------------------------------

-- Table Clients
CREATE TABLE Clients (
    client_id SERIAL PRIMARY KEY,
    nom VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE,
    adresse VARCHAR(255) NOT NULL
);

-- Table Produits
CREATE TABLE Produits (
    produit_id SERIAL PRIMARY KEY,
    nom_produit VARCHAR(100) NOT NULL,
    description TEXT,
    prix NUMERIC(10, 2) NOT NULL CHECK (prix >= 0)
);

-- Table Commandes
CREATE TABLE Commandes (
    commande_id SERIAL PRIMARY KEY,
    client_id INT NOT NULL,
    produit_id INT NOT NULL,
    quantite INT NOT NULL CHECK (quantite > 0),
    date_commande DATE NOT NULL,
    FOREIGN KEY (client_id) REFERENCES Clients(client_id),
    FOREIGN KEY (produit_id) REFERENCES Produits(produit_id)
);