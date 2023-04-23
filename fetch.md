# Retour Fetch
Jean, je te fais un petit retour suite afin que tu puisses avoir une explication sur fetch. 
#
## Fetch c'est quoi ? 


Fetch te permet d'aller chercher des données sur le réseau (sur ton serveur, internet...) et de manière asynchrone. Quand la requête est terminée fetch te retourne une promesse. 

Ca c'est en gros ce que dit la doc, mais de manière plus compréhensible pour un débutant, cela veut dire que tu peux, aller **chercher une ressource** (une image, du texte, un json, une page web...).
Bref tout ce qui est **accessible** via une requête http.

Tu as **énormement** de cas ou tu peux utiliser fetch, un exemple classique, qui utilise problablement fetch c'est sur les réseaux sociaux, au lieu de récupérer **toutes les données** d'un coup sur ton fil et d'avoir énormement de traitement à faire **tu récupères une partie des données**, et lorsque tu arrives en bas de la page, **d'autre données sont chargées**, et ainsi de suite. 

Dans ton métier tu seras régulièrement amené à **interroger des API**, (mais pas forcément ta propre API) pour :
- Récupérer des données d'un autre service (météo, films)
- Envoyer des informations (modifier, ajouter, supprimé)

Le fait de pouvoir aussi bien reçevoir des données ainsi que d'en envoyer te permet par exemple de **gérer l'authentification** d'un utilisateur et d'afficher le contenu sur ta page en conséquence.


Un fetch est généralement une requête effectuée de manière invisible pour un utilisateur, et ce sont (généralement) des données brutes (du texte/json) afin de pouvoir les traiter à notre guise (mise en forme...). 


Un autre point important fetch te permet d'ajouter des options, comme le type de requête (get/post/put...) (verb http) ainsi qu'évidemment headers, cookies... Néanmoins côté client fetch ignore les cookies envoyer par le serveur (sauf options, mais mauvaise pratique). Par exemple, lorsqu'on authentifie un utilisateur via une api, celle-ci renvoie un token d'identification, celui-ci devra être ajouté aux options dans les headers afin que l'utilisateur soit authentifier lors d'une requête.

Ce dernier point, est très important et te sera essentiel, lorsque tu commenceras à être à l'aise avec cette méthode.

## Alors comment on fait ? 

Notre application n'intégre pas d'API, néanmoins **nous pouvons récupérer une page complète** (code html).

Notre but est simple nous allons créer **notre propre page HTML, avec notre  propre code js**. (ceci est complètement indépendant l'application que tu viens de créer, bien qu'il faudra qu'elle soit démarrée). Notre page contiendra un bouton nommé "afficher la carte", et un input de type number. Nous effectuerons une requête avec fetch sur la route "/card/id" l'id étant le contenu de l'input, enfin nous afficherons les informations de la carte. 

#
Un petit pré-requis nécéssaire afin de ne pas être bloqué par ton navigateur. Je t'invite à installer le package "cors" via npm et de modifier ton index.js comme ci après :
```javascript
const cors = require('cors')
app.use(cors())
````

> Afin que tu ne mélange pas les notions, je ne m'attarderai pas sur ce qu'est le cors, mais grossièrement dans notre cas ce package permet d'envoyer un header en particulier afin que la requête ne soit pas bloquée par ton navigateur.
#
Voici le code que je te propose les explications sont en commentaires dans le code :
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <input id="number" type="number"  min="1" max="100" />
    <button id="show">Afficher la carte</button>
   
    <div id="txt"></div>
</body>
<script>
    const input = document.querySelector("#number")
    const btn = document.querySelector("#show")
    const div = document.querySelector("#txt")
    btn.addEventListener("click", (e) => {

        const number = input.value
        if (number) {
            const url = `http://localhost:5433/card/${number}` // url de destination   
            const config = { // on configure notre requête avec la méthode get    
                method: 'GET',
            }
            const pattern = /(?:<p>(.+?)<\/p>|<h1 .*>(.+?)<\/h1>)/gm // j'en profite pour faire un rappel sur les regex
            fetch(url, config) // on envoie la requête tu vois que fetch prend 2 paramètre, l'url, et sa configuration
                .then((response) => { // on utilise then afin d'executer notre callback lorsque la promesse est résolue
                    return response.text() // on récupère le texte de la page note qu'ici aussi la methode text renvoie une promesse
                })
                .then((text) => { // quand la seconde promesse est résolue on met à jour notre page 
                    div.innerHTML = text.match(pattern).join("")
                })
        }
    })
   
    
    
</script>
</html>
```

Tu remarqueras avec ce code que tu peux aller chercher des données ailleurs, et les afficher **sans** recharger ta page.

Voila je te laisse essayer de comprendre ce code si tu as des questions n'hésite pas.
