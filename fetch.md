# fetch

## Théorie
La fonction fetch en javascript, permet de faire une requête HTTP de manière **asynchrone**,
elle fonctionne avec les promesses javascript.

Je m'explique, quand on charge une page HTML, on renseigne une URL dans le navigateur, par exemple pour afficher
la liste des professeurs on appelle https://127.0.0.1:8000/teachers, cette requête est faite au serveur, et ce que tu as développé
retourne au navigateur de manière synchrone le contenu à afficher, la liste des professeurs.

Un fois le contenu affiché dans le navigateur, le contenu est "figé". En revanche le javascript va nous permet de 
modifier le HTML (via le DOM) pour faire évoluer le code et la structure de la page affichée.

C'est ici que *fetch* peut intervenir, c'est une méthode javascript qui nous permet de faire une requête de manière *asynchrone*,
c'est à dire en parallèle et de manière desynchronisée du reste (requête classique et affichage).
Généralement cette requête est faite après une action de l'utilisateur ou déclenchée par un événement quelconque, 
par exemple: le clique sur un bouton ou la fin de chargement de la page.

Documentation de la méthode : https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch

Syntax de la méthode (https://developer.mozilla.org/en-US/docs/Web/API/fetch) : 

    fetch('url_de_la_requête');

La méthode fetch prend en 1er paramètre (obligatoire) l'url de la requête HTTP que l'on souhaite faire.

La réponse à cette requête est une promesse (Promise), les promise possède deux méthodes à connaitre qui permettre 
de gérer le retour *then()* pour la réponse de la requête et *catch()* pour les potentielles erreurs pendant l'execution 
de la requête.

Pour utiliser la réponse de la requête asynchrone on utilisera donc la syntaxe suivante :

    fetch('url_de_la_requête')
        .then(response => {
            console.log(response);
        })
        .catch(error => {
            console.error(error);
        });

`response` représente la réponse de la requête, elle contient le header et le body.
A ce stade, on peut traiter pour récupérer le body et l'affiché dans notre page via un getElementById().innerHTML par exemple.

Enfin pour aller plus loin dans l'usage, un 2eme paramètre permet d'ajouter des options à notre requête.
Par exemple la méthode de la requête (GET / POST / PUT / DELETE), modifier le header pour diverse raison, communiquer des informations d'authentification par exemple.

## Pratique

Imaginons que nous souhaitons charger la liste des professeurs de manière asynchrone.

La requête mise en place est `https://127.0.0.1:8000/teachers`;

Ne devons trouver un déclencheur/événement, nous allons utiliser `DOMContentLoaded` qui est déclenché quand le navigateur a
chargé le HTML et que le DOM est construit.

    document.addEventListener("DOMContentLoaded", event => {
        //stop la propagation d'autres événement.
        event.preventDefault();

        //on requête la liste des professeurs
        feth('https://127.0.0.1:8000/teachers')
            //on traite la réponse
            .then(response => response.text())
            .then(body => { 
                //on injecte le contenu récupéré en asynchrone dans une div#content
                document.getElementById('content').innerHTML = body.content;
            })
            //on capte les possibles erreurs pour débuggé
            .catch(error => {
                console.log(error);
            });
    }));

Dès que le chargement de la page est faite, on requête de nouveau le serveur pour récupérer la liste des professeurs et on injecte la reponse dans une div#content.

Pour se faire, il faut s'assurer que la requête de base charge bien une div#content sans contenu particulier, c'est la requête fetch
qui va récupérer uniquement le contenu à afficher sans le layout.

