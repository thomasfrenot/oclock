# Apprenant 1
**Très bon avancement, très encouragent**

**Les petits détails à retoucher et intégrer**
La class CoreController est étendue sur chacun des controller (User/Student/Teacher) et
ne doit pas pouvoir être instancié, en faire une class abstraite permettra de sécuriser son utilisation.


    abstract class CoreController

De manière générale et pour gagner en lecture, bien commenter chaque méthode et
être concis sur le naming (ex : il n'est pas nécessaire de rappeler *teacher*UpdatePost dans le controller Teacher, 
updatePost suffit).


    class TeacherController extends CoreController
    {
        public function add() {}
        public function update() {}
        ...
    }

Revoir le fonctionnement de la fonction extract, utilisée dans la méthod show() du CoreController,
elle n'est pas correctement exploitée dans les templates.


    $vars['hello'] = 'world!';
    extract($vars);
    echo $hello; // affiche "world!"

Dernier point sur un comportement non fonctionnel au niveau de l'update student et teacher,
il manque simplement une information dans l'appel de la route POST au niveau du formulaire.

Le travail est juste et fonctionnel. 
Donc il faut continuer comme ça c'est très bien.

Bon acquis du PHP POO.

