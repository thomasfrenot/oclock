# Apprenant 3
**Incompréhension au niveau du templating / controller**

L'étudiant semble avoir quelques diffcultés à mettre en place ses controllers
et ne semble pas avoir compris le passage controlleur -> vue ainsi que la gestion des routes.

La base n'est pas en place alors l'étudiant c'est perdu en chemin.
Il faudrait revenir au point de départ et réexpliquer le cheminement.

On tombe systématiquement sur une 404 au moment des tests navigateur, la navigation n'est pas faite, 
ce qui empêche de tester en naviguant.
Tout cela apporte de la confusion sur l'avancement.

Il faudrait procéder par étapes :
- mise en place du layout html (OK)
- affichage de la page home, revoir la route */* et non */home*
        
index.php

        $router->map(
            'GET',
            '/'
            [
                'method' => 'home',
                'controller' => MainController::class // On indique le FQCN de la classe
            ],
            'main-home'
        );

app/views/home.tpl.php

        <li class="nav-item">
            <a class="nav-link" href="<?= $router->generate('main-home') ?>">Accueil</a>
        </li>
        <li class="nav-item">
            <a class="nav-link" href="<?= $router->generate('teachers') ?>">Profs</a>
        </li>
        <li class="nav-item">
            <a class="nav-link" href="<?= $router->generate('students') ?>">Etudiants</a>
        </li>
        <li class="nav-item">
            <a class="nav-link" href="./appuser/list.html">Utilisateurs</a>
        </li>
        <li class="nav-item">
            <a class="nav-link" href="/logout">Se déconnecter</a>
        </li>
permet d'avoir une route qui répond à l'url http://127.0.0.1/ et affiche l'accueil de l'outil.

- création de la route pour afficher les profs (OK)
- renseigner la route dans le code html au niveau du header (OK)
- s'assurer d'avoir le templates complet (header / content / footer) sur la liste, découper le layout pour avoir un header et un footer

creer app/views/partials/header.tpl.php

        <!DOCTYPE html>
        <html lang="en">
        <head>
            ...
        </head>
        
        <body>
            <nav class="navbar sticky-top navbar-expand-lg navbar-dark bg-dark">
                <div class="container">
                    <a class="navbar-brand" href="./index.html">Skoule</a>
                    <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent"
                        aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
                        <span class="navbar-toggler-icon"></span>
                    </button>
        
                    <div class="collapse navbar-collapse" id="navbarSupportedContent">
                        <ul class="navbar-nav mr-auto">
                            <li class="nav-item">
                                <a class="nav-link" href="./index.html">Accueil</a>
                            </li>
                            <li class="nav-item">
                                <a class="nav-link" href="<?= $router->generate('teachers') ?>">Profs</a>
                            </li>
                            <li class="nav-item">
                                <a class="nav-link" href="<?= $router->generate('students') ?>">Etudiants</a>
                            </li>
                            <li class="nav-item">
                                <a class="nav-link" href="./appuser/list.html">Utilisateurs</a>
                            </li>
                            <li class="nav-item">
                                <a class="nav-link" href="/logout">Se déconnecter</a>
                            </li>
                        </ul>
                    </div>
                </div>
            </nav>

creer app/views/partials/footer.tpl.php

            <!-- And for every user interaction, we import Bootstrap JS components -->
            <script src="https://code.jquery.com/jquery-3.4.1.slim.min.js"
                integrity="sha384-J6qa4849blE2+poT4WnyKhv5vZF5SrPo0iEjwBvKU7imGFAV0wwj1yYfoRSJoZ+n" crossorigin="anonymous">
            </script>
            <script src="https://cdn.jsdelivr.net/npm/popper.js@1.16.0/dist/umd/popper.min.js"
                integrity="sha384-Q6E9RHvbIyZFJoft+2mJbHaEWldlvI9IOYy5n3zV9zzTtmI3UksdQRVvoxMfooAo" crossorigin="anonymous">
            </script>
            <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.4.1/js/bootstrap.min.js"
                integrity="sha384-wfSDF2E50Y2D1uUdj0O3uMBJnjuUD4Ih7YwaYd1iqfktj0Uod8GCExl3Og8ifwB6" crossorigin="anonymous">
            </script>
        </body>
        
        </html>

app/Controllers/MainController.php dans la method show() ajouter le `header.tpl.php` et `footer.tpl.php`

    require_once __DIR__ . '/../views/partials/header.tpl.php';
    require_once __DIR__ . '/../views/' . $viewName . '.tpl.php';
    require_once __DIR__ . '/../views/partials/footer.tpl.php';

- afficher la liste des professeurs
- puis passer à la liste des étudiants
