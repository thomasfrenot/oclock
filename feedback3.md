# Apprenant 3
**Incompréhension au niveau du templating**

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
- création de la route pour afficher les profs (OK)
- renseigner la route dans le code html au niveau du header
- s'assurer d'avoir le templates complet (header / content / footer) sur la liste
- afficher la liste des professeurs
- puis passer à la liste des étudiants
