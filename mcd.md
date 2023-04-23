# Correction MCD
Salut Lisa, 
Je viens de prendre connaissance de ton mcd. 

Dans l'ensemble c'est bien, on peut accepter de voir les choses comme ça voici comment je lis ton MCD :

- Un utilisateur a 0 ou N adresses et une adresse à un seul utilisateur. (**many to one**)

- Un utilisateur génère 0 ou N commandes et une commande est générée par un utilisateur.  (**many to one**)

- Une commande contient 1 ou N produits et un produit peut être contenu dans 0 ou N commandes (*many to many**)

- Un utilisateur aime 1 un produit et un produit est aimé par 1 utilisateur (**one to one**)

Tu constates que **ce n'est pas** ce que l'ont veut sur la dernière phrase nous souhaitons que : 

- Un utilisateur aime 0 ou N produit et un produit est aimé par 0 ou N utilisateurs (**many to many**)

Ta cardinalité côté utilisateur est donc **0-N** et de l'autre côté **0-N** aussi. 

## Quelques conseils

Lorsque tu réfléchis aux cardinalités, le sens de tes phrases doit être **interrogative**. 

Personnellement je le fais de cette façon :

Je me pose **2 questions par tables**, une pour definir le **minimum**, l'autre pour définir le **maximum**. J'y répond, si ma réponse est **positive** (oui) alors c'est ma cardinalité.

J'**impose** à ma **question** et à ma **reponse** qu'elles soient construites dans l'ordre suivant:

- TableA -> Liaison -> TableB

> Un **utilisateur** (TableA) peut-il n'avoir jamais **aimer/like** (liaison) un **produit** (TableB) ? 
>>Oui, un **utilisateur**  (TableA) peut avoir **like** (liaison) 0 produit (TableB).

>Un **utilisateur** peut-il avoir **aimer** plus d'un **produit** ? 
>> Oui un **utilisateur** peut avoir **like** N **produits**.

> Un **produit** peut il être **aimé** par 0 **utilisateur** ? 
>> Oui un **produit** peut être **aimé** par 0 **utilisateur**.

> Un **produit** peut il être **aimé** par plus d'un **utilisateur** ?
>> Oui un **produit** peut être **aimé** par N **utilisateurs**.


Par ailleurs, je trouve que ton mcd est difficile à lire (notamment pour les cardinalitsé). Tu peux utiliser les outils suivants :
* draw.io (app google drive) il intègre tout ce qu'il faut.
* <https://dbdiagram.io/>
