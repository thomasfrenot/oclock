# Correction MCD

- les entités meritent d'être plus complète, exemple nom / prenom sur l'entité `User`
- Sur l'ensemble des entités, il faut définir un ou plusieurs attribut pour permettre d'identifié ton entité, on l'identifie avec un #


    *Exemple sur l'entité Adress*
    Address
        #id
        address
        city
        ...

- il manque un lien `Order` envoyer à `Address`, pour définier l'adresse de livraison de l'order
- pour la gestion du `Like` ManyToMany :
  - la cardinalité n'est pas correct, un produit peut être like par 0 ou n User et inversement
  - il faut définir des données dans la relation pour préciser le produit et le user
  cela permettrait également d'avoir plus d'information sur le LIKE, la date par exemple
    

    LIKE
        date

création d'une table associative.
