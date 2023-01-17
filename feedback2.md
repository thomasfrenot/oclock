# Apprenant 2
**En bonne voie**

L'étudiant est sur la bonne voie, ce qui est mis en place est encouragent.
Peut être l'étudiant a manqué de temps ou d'organisation dans son travail, de la confiance ?
Proposer d'avancer étape par étape pour ne pas se perdre dans ce qui est produit.

Comprendre ce qui peut bloquer ? L'étudiant semble s'être arrêté à l'ajout d'un professeur, peut-être n'a t'il pas
compris l'utilisation des formulaires et des méthodes POST pour récupérer les informations.
L'accompagner dans ce sens :
- une route pour afficher le formulaire (GET)


    class TeacherController extends CoreController
    {
        public function addGet() {
          //code pour afficher la page d'ajout d'un professeur
          $this->show('teachers/teachers_add');
        }
    }
    

- une route pour traiter le formulaire (POST)


    class TeacherController extends CoreController
    {
        public function addPost() {
            // récupérartion des données POST

            // traitement de la données et vérification

            // tout ok, création du nouveau Teacher() et save()
        }
    }
  - récupération des données postées (voir les consignes de l'exercice filter_input / $_POST)
  - vérification des données
  - mise en place d'une méthode pour inserer le nouveau professeur

la fonction input_filter https://www.php.net/manual/fr/function.filter-input.php

Récupérer le contenu via $_GET ou $_POST https://www.pierre-giraud.com/php-mysql-apprendre-coder-cours/recuperer-manipuler-donnee-formulaire/

Ensuite pour les prochaines routes POST, les updates par exemple, on a besoin de l'id en paramètre pour savoir quel professeur 
est modifié, pour cela dans le routing (index.php), on ajoute un param `[i:id]` voir doc AltoRouter https://altorouter.com/usage/mapping-routes.html

    $router->map(
      'GET',
      '/teacher/[i:teacherid]/delete',
      [
          'method' => 'maMethodDupdate',
          'controller' => TeacherController::class
      ],
      'teacher_delete'
    );
