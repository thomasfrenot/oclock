# Apprenant 4
**Non fonctionnel avec erreur Fatal, problème class et routing**

Le rendu n'est pas fonctionnel, des erreurs PHP (fatal) apparaissent.
Il manque des fichiers notamment MainController et CoreController pourtant attendus.
Tout cela au niveau des controllers, la gestion des class côté model est ok.

Ajouter le CoreController qui doit être l'abstraction d'un controller, on veut que celui-ci permettre au controller 
qui l'utilise d'afficher la page via une méthode protégé `show()`


        <?php

        namespace App\Controllers;
        
        abstract class CoreController
        {
            /**
             * Méthode permettant d'afficher du code HTML en se basant sur les views
             *
             * @param string $viewName Nom du fichier de vue
             * @param array $viewData Tableau des données à transmettre aux vues
             * @return void
             */
            protected function show()
            {
                // ...
            }
        }

Ensuite la class MainController doit étendre CoreController comme tous les controllers et contenir les controllers des routes principales comme la home par exemple.

        <?php

        namespace App\Controllers;

        class MainController extends CoreController
        {
            /**
            * Méthode s'occupant de la page d'accueil
            * 
            * @return void
            */
            public function home()
            {
                // Appelle du template home
                $this->show('main/home');
            }
        }

L'utilisation d'une class abstraite semble acquise mais l'apprennant n'a sans doute pas compris 
le principe de controller, l'utilité et l'usage.

Revoir également l'instanciation d'une class :

    $studentsModel = new Students
    students();
    //problème ici

remplacer par

    $studentModel = new Students();

Revenir sur les base de la POO permettrait de corriger des erreurs dans le code et s'assurer de la bonne compréhension.

