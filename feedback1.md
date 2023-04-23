# Feedback Triple Triad

Salut Jean,
C'est très bien tout fonctionne. Mais je vais t'embêter un peu.

# 
## En ce qui concernerne ton code : 

- C'est une bonne pratique de découper le middleware dans un fichier séparé.

- Utilise plutôt `parseInt` au lieu de `Number`, en effet tu reçois une chaine de caractères et par mesure de cohérence personnellement, je préfère utiliser `parseInt` qui est un parser, afin de rechercher un nombre dans une chaine.

- Attention au `select *` dans les requêtes SQL lorsque tu selectionnes la liste des cartes, dans ce cas uniquement le nom de la carte t'intéresse ainsi que le path de l'image. 

Si tu souhaites améliorer l'app :

Tu peux par exemple arranger l'organisation du code.
Ton cardController contient aussi ton deck. Dans la réalité un deck est un ensemble de carte. C'est donc ton deck qui contient des cartes, et pas tes cartes qui contiennent ton deck.  Tu pourrais diviser ce controller en 2.

L'organisation de ton code, c'est **important**.
#

## ❌  Ce qu'il faut absolument éviter.


```javascript
    const valueColumn = `value_${direction.replace(/'/g, "''")}`;
      const query =
          `
            SELECT *
            FROM "card"
            WHERE ${valueColumn} = $1
          `;
```

C'est une **mauvaise** manière de faire. Il faut toujours garder le contrôle sur sa requête SQL, toujours garder un maximum de précaution, et ne pas donner l'opportunité aux petits malins de retourner autre chose que ce qui doit être retourné, là il y a une injection SQL, j'ai réussi à injecter ma propre requête. 

Voici un exemple d'un résultat non attendu : 

- <http://localhost:PORT/search/values?direction=east%20=%201%20or%20value_north&value=1>
Je t'invite à regarder la correction afin de faire les requêtes correctement.