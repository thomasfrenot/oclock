# Apprenant 4
**Non fonctionnel avec erreur Fatal**

Le rendu n'est pas fonctionnel, des erreurs PHP (fatal) apparaissent.
Il manque des fichiers notamment MainController et CoreController pourtant attendus.
Tout cela au niveau des controllers, la gestion des class côté model est ok.

L'utilisation d'une class abstraite semble acquise mais l'apprennant n'a sans doute pas compris 
le principe de controller, l'utilité et l'usage.

Revoir également l'instanciation d'une class :

    $studentsModel = new Students
    students();
    //problème ici

Revenir sur les base de la POO permettrait de corriger des erreurs dans le code et s'assurer de la bonne compréhension.
