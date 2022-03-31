Snake
====================

Infos importante :

* Serpent
  * Tete -> (posX, posY, nouvelle_direction, (ancienne_direction))
  * Queue -> (posX, posY, (direction))
  * La direction du serpent par 1,2,3,4 pour droite, gauche, haut, bas (ou des tuples ?, ou one hot encoding ?)
  * Faire une variable binaire pour la tête et la queue ? ou pour le corps ?
* Pomme -> (posX, posY)
  * Les pommes par -1
  * Liste des cases dispo ? (pour povoir facilement créer une nouvelle pomme)
  * Si la tête est sur la position de la pomme, la pomme est mangée, on n'actualise pas la queue, ce qui permet de faire un serpent plus long et on tire une position aléatoire dans la liste des cases dispo pour la nouvelle pomme
  * On ajoute 1 à la longueur du serpent (qui pourra être utilisé pour le score)
* Plateau -> array(tailleX, tailleY)
  * Les cases vides sont représentées par 0
  * Au déplacement, la tête se déplace en fonction de la direction d'entrée, il suffit de déplacer la tête (et donc d'update la position) de la direction de la position actuelle et de mettre la nouvelle direction dans la nouvelle case de la tête
  * Pour la queue, il suffit d'update la position en fonction de la direction, puis de supprimer l'ancienne position de la queue (en mettant 0)
* Réseau de neurones
  * Ainsi l'input du réseau sera :
    * Le serpent qui est un vecteur (posXTete, posYTete, posXQueue, posYQueue)
    * La position de la pomme
    * Le board des directions vectorisées
  * Mettre un layer d'embedding des directions ?
  * Faire un réseau standard avec plusieurs couches cachées
  * L'output est un vecteur de taille 4 (droite, gauche, haut, bas)
  * Suivi d'une fonction d'activation pour récuperer la direction finale
* L'apprentissage
  * Apprentissage par reinforcement learning
  * Il faut donc simuler une partie pour pouvoir évaluer les performances du modèle
  * On doit choisir la taille de la population
  * Le score peut être la longueur totale du serpent
  * Il est possible de pénaliser un peu la défaite si rencontre avec le mur ?
* Alternative
  * Possible de changer la nature du réseaux en utilisant un CNN 3D (2D pour le plateau, et 1D pour les directions, l'indicateur de la tête, le corps, la queue et la pomme)
