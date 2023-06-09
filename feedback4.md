# Feedback Triple Triad

Hello Capucine,

Tu sembles un peu perdu. Pour ma part ce que je fais quand je ne sais pas trop comment faire, je pose tout je prend un papier et je note étape par étape ce que je dois faire afin d'arriver à mon but. 

Dans ton cas nous voulons dans un premier temps  afficher les détails d'une carte, pour cela il nous faut :

- Créer une route pour accèder à une carte (ce que tu as fait) mais cette route doit contenir un ID. Il faut le rajouter. 
- Créer la requête SQL dans le mapper. (c'est fait) Mais tu as également oublié l'id. Tu as peut être des soucis à comprendre comment transmettre des données entre les fonctions  ?
- Transmettre les données à la vue. 

Une fois que tu as toutes ces étapes, s'il y a des choses qui te semble abstraite, je t'invite à les tester une à une.

## Un mini exercice. 

Parfois un exemple visuel peut aider à comprendre le fonctionnement des choses.
 
Je suppose que tu as des difficultés à faire transiter les données à la vue ou entre les fonctions. Dans ce petit exercice on ne s'occupe pas de la base de données. Nous voulons juste afficher l'id passer en paramètre dans l'url dans la vue.  J'ai modifié ta fonction ci-dessous : 

```javascript
   cardPage: async (req, res) =>{
    try {
      // const card = await dataMapper.getCard();
      const cardId = parseInt(req.params.id, 10) // On récupére l'id on utilise parseint afin de s'assurer qu'on a bien un entier
      //res.render('card',{}); 
      res.render('card',{cardId}); // on passe cette variable à la vue
    } catch(error) {
      console.error(error);
      res.status(500).send(`An error occured with the database :\n${error.message}`);
    }
  }
```
J'ai commenté ton code original afin que tu puisses comparer, lorsque tu auras fini cet exercice. Ainsi tu pourras identifier ce qu'il te manque pour finir l'étape 1.

Ton but à toi, dans cet exercice, c'est de copier l'adresse <http://localhost:port/card/1> dans ton navigateur, et juste d'afficher le **1** (l'id de la carte) dans la vue.

Ce que tu dois faire : 

- Tu dois modifier fichier router.js tu dois rajouter quelque chose (un petit truc) à la route pour prendre en compte l'id. 
- Modifier la vue en consquénce (card.ejs). Note que dans ce cas, le nom de la variable à afficher dans la vue doit être le même que celui que j'ai mis dans la fonction ci-dessus. (destructuring assignment, mais pour le moment ne t'attarde pas trop dessus, je te réexpliquerai) 



Si tu arrives à faire fonctionner ma fonction correctement tu auras toutes les clés en mains pour finir cette étape l'app. 

A savoir : 
- au lieu d'afficher l'id, tu dois te servir cette id pour interroger la base de donnée.
- transmettre les informations de la bdd à la vue. 

Si tu as des questions n'hésite pas