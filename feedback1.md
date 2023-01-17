# Apprenant 1
**Très bon avancement, très encouragent**

**Les petits détails à retoucher et intégrer**
- La class CoreController est étendue sur chacun des controller (User/Student/Teacher) et
ne doit pas pouvoir être instancié, en faire une class abstraite permettra de sécuriser son utilisation.

- De manière générale et pour gagner en lecture, bien commenter chaque méthode et
être concis sur le naming (ex : il n'est pas nécessaire de rappeler *teacher*UpdatePost dans le controller Teacher, 
updatePost suffit).

- Revoir le fonctionnement de la fonction extract, utilisée dans la méthod show() du CoreController,
elle n'est pas correctement exploitée dans les templates.

- Dernier point sur un comportement non fonctionnel qu niveau de l'update student et teacher,
il manque simplement une information dans l'appel de la route POST au niveau du formulaire


Le travail est juste et fonctionnel. 
Donc il faut continuer comme ça c'est très bien.

Bon acquis du PHP POO.

