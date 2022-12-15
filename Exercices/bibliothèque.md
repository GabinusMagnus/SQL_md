Gabin Courdy                                                                                                         Décembre 2022

TG1

# SQL, Exercices bibliothèque

> 1. Quelles sont les anomalies dans le schéma précédent ?
>
> Abonne(Abonne_ID, Nom, Prenom, DateNaissance, Adresse, Ville, CodePostal)
>
> Livre(Livre_ID, Titre, Auteur, Genre, ISBN)
>
> Emprunt(Abonne_ID, Livre_ID, Livre_Titre, Livre_ISBN, DateEmprunt, DateRetourPrevu, DateRetourReel)

Pas de clé primaire (PRIMARY KEY),

> 2. Clés et contraintes
>    a. Proposer une clé primaire pour la table Emprunt.

Emprunt_ID, pour identifier les emprunts.

> b. Expliquer l’intérêt de la requête suivante :
> ALTER TABLE Emprunt
> ADD CONSTRAINT CHK_Emprunt_Date CHECK (DateEmprunt <= DateRetourReel)


`ALTER TABLE Emprunt` modifie la table Emprunt

`ADD CONSTRAINT CHK_Emprunt_Date CHECK (DateEmprunt <= DateRetourReel)` ajoute une contrainte (règle de la table) qui stipule que DateEmprunt est plus petite ou égale à DateRetourReel.

Ainsi, on ne pourra pas entrer dans DateEmprunt une date ultérieure à celle de DateRetourReel son retour. Que le livre a été emprunté après son retour...


> c. Quelles sont les conséquences de la requête suivante ?
> ALTER TABLE Emprunt
> CONSTRAINT FK_Emprunt_Abonne
> FOREIGN KEY(Abonne_ID) REFERENCES Abonne(Abonne_ID)


`ALTER TABLE Emprunt` modifie la table Emprunt

`CONSTRAINT FK_Emprunt_Abonne` établit une contrainte sur les clés étrangère des tables Emprunt et Abonne

`FOREIGN KEY(Abonne_ID) REFERENCES Abonne(Abonne_ID)` la clé étrangère Abonne_ID fait référence à Abonne_ID de la table Abonne


Ainsi, dans Abonne_ID d'Emprunt correspondra obligatoirement à Abonne_ID d'Abonne.


> d. Pourquoi l’ajout de la contrainte suivante serait-elle une mauvaise idée ?
> ALTER TABLE Emprunt
> MODIFY DateRetourReel DATE NOT NULL;


`ALTER TABLE Emprunt` modifie Emprunt

`MODIFY DateRetourReel DATE NOT NULL;` empêchera d'entrer une valeur non-nulle dans DateRetourReel.
