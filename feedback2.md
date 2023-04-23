# Feedback Triple Triad

Hello Marie,

C'est dans l'ensemble du bon travail.
#
## Quelques remarques

Bien que la correction ne le montre pas en effet, c'est une approche intéressante d'avoir rajouté controller pour card avec une vue. En effet, si l'application venait à être upgrade il serait aisé d'utiliser les cartes ailleurs. Néanmoins le fichier doit s'appeller **cardController** et non **cards**, car tu ne contrôle qu'une carte. (Attention au nommage)

Tu vérifies que la carte n'est pas déjà dans le deck, cependant tu **oublies** la limite de 5 cartes. Et on ne peut pas supprimer de carte. 

En ce qui concerne la recherche des éléments, je pense que tu as mal interprété la consigne. Dans ton cas tu selectionnes toutes les cartes, et ensuite tu effectues un filtre sur la recherche. Néanmoins, si tu avais 1 millions de cartes ce serait vraiment très lourd à traiter. Personnellement je ne connais pas ce jeu mais à la vue de la correction, je pense qu'il y a des personnages qui n'ont pas d'éléments, ce qui est attendu à mon avis, c'est construire la requête différement si on recherche un personnage sans élement.


Si tu dois retenir une chose reste vigilante face aux consignes. 

Si tu effectues les modifications et que tu termines l'app n'hésite pas à revenir vers moi =D. 

