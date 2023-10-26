# Corrections des exercices 2, 4, 5 et 6 MCD et MLD de GT Toit

---

## MCD

### Solution 1

![1](./img/hotel.svg)

---

Ici, je généralise un service et une chambre dans une entité nommée Prestation dans le but de vous montrer plus efficacement les contraintes qu'on peut avoir au niveau de l'héritage.

![2](./img/solution_2.svg)

---

## MLD

### Transformation de la solution 1 du MCD en MLD

Pour la transformation du MCD en MLD cf les règles de transformation dans le [cours](../../../cours/pdf/merise.pdf)
Dans le MCD, un attribut ou nom d'association doit être unique, cependant, il est toléré de garder les mêmes noms pour les clé-primaires et les clé-étrangères.
1. Prestation(**id_prestation**, desc_prestation)
- Clé primaire (PK) : **id_prestation**
2. Article(**id_article**, date_consommation, heure_consommation, *client*)
- PK : **id_article**
- clé étrangère (FK) : **client** fait référence à la PK **id_client** de Client
3. Chambre(**id_chamb**, nom_chamb)
- PK : **id_chamb**
4. Reservation(**id_reservation**, date_debut, date_fin, montant_acompte, date_acompte, *chambre*)
- PK : **id_reservation**
- FK : *chambre* fait référence à **id_chambre** de Chambre
5. Categorie(**id_cat**, nom_cat)
- PK : **id_cat**
6. Hotel(**id_hotel**, nom_hotel,tel_hotel, *classe*)
- PK : **id_hotel**
- FK : *classe* fait référence à **id_classe** de Classe
7. Classe(**id_classe**, nb_etoile)
- PK : **id_classe**
8. Client(**id_client**, nom_client, prenom_client, numero_rue_client, nom_rue_client, code_postale_client, ville_client)
- - PK : **id_client**
9. PrestationArticle(**prestation**,**article**, **quantite**)
- PK : couple **prestation** et **article**
- FK : *prestation* fait référence à la PK **id_prestation** de Prestation
- FK : *article* fait référence à la PK **id_article** de Article
10. PrestationHotel(**offre_prestation**, **hotel**, prix_unit)
- PK : couple **offre_prestation** et **hotel**
- FK : *offre_prestation* fait référence à la PK **id_prestation** de Prestation
- FK : *hotel* fait référence à la PK **id_hotel** de Hotel
11. ReservationClient(**reservation**, **client**)
- PK : couple **reservation** et **client**
- FK : **reservation** fait référence à la PK **id_reservation** de Reservation
- FK : **client** fait référence à la PK **id_client** de Client
12. CategorieChambre(**chambre**, **categorie**, tarif_unit_chambre)
- PK : couple **chambre** et **categorie**
- FK : **chambre** fait référence à **id_chambre** de Chambre
- FK : **categorie** fait référence à **id_cat** de Categorie
13. Adresse(**id_adress**, numero_adress, nom_adress, code_postal_adresse, ville_adress)
- PK : **id_adress**
14. AdresseClient(**id_adress**, **id_client**)
- PK : couple (**id_adress**, **id_client**)
- FK : **id_adress** fait référence à la PK **id_adress** de Adresse
- FK : **id_client** fait référence à la PK **id_client** de Client

### Transformation de la solution 2 du MCD en MLD

- Similaire à la solution 1 sauf le cas spécifique de l'héritage. Nous avons vu en cours comment procéder et les différentes solutions possibles.
- Autre particularité, le CIF entre Client et Reservation donnera lieu à une FK dans Reservation qui fera référence à la PK de Client. Grâce à la CIF on évite d'avoir une table d'association composé du couple des PK de chaque entité.


---

## Corrections travaux stagiaires

### Commentaires généraux

- Attention à la syntaxe (formalisme MERISE) à respecter même lorsque vous utilisez les outils qui ne sont pas adaptés de base à la méthode comme par exemple draw.io. Appuyez-vous sur un modèle ou une documentation pour respecter la syntaxe de MERISE.
- Vous pouvez émettre des hypothèses pour concevoir votre MCD. Pensez à les valider ou à les infirmer avec la partie métier (client).
- Ajoutez des DF entre entités et CIF uniquement lorsque c'est pertinent que cela permet de simplifier une association impliquant plus de 2 entités. Pour les relations 1,1 à 1,N, généralement il n'est pas nécessaire de l'indiquer car à la fin dans tous les cas on aura une clé étrangère du côté 1,1.
- Essayez de respecter toutes les règles métiers ou de gestion (RG).
- Itérez plusieurs fois sur votre MCD en vérifiant que toutes les RG sont respectées.
