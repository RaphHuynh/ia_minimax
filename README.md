# ia_renforcement_minimax

# IA par renforcement from scratch

Le but de cette ia est de trouver par la méthode du renforcement.

## Règle du jeu

Le jeu consiste à remplir le plus de case possible sur le plateau avec O voici les contraintes :
Quand O est posé on ne peut plus poser de O sur la même ligne / colonne et diagonales.

## Solution

### Choix de librairie
- copy
Pour réaliser de la recherche en profondeur sur mon arbre de mes solutions générés.

- concurrent.futures
Pour faire du multithreader afin d'accélérer le temps de calcul du programme.

### Explication des méthodes de la classe plateau

- __init__(self, n): 

Le constructeur de la classe Plateau. Il initialise un plateau de taille n avec des cases vides.

- __str__(self): 

Méthode pour afficher le plateau sous forme de chaîne de caractères.
Les O sont affichés en vert et les X en rouges.
Les O représentent les coups jouer.
Les X représentent les cases ne pouvant plus être joués.

- joue(self, x, y): 

Méthode qui permet de jouer un coup en plaçant un "O" à la position (x, y) sur le plateau. Elle met également à jour les cases "X" sur la ligne, la colonne et les diagonales de la case jouée.

- cases_vides(self): 

Méthode qui renvoie la liste des coordonnées des cases vides du plateau.

- afini(self): 

Méthode qui vérifie si le plateau est entièrement rempli, c'est-à-dire s'il n'y a plus de cases vides.
Renvoie True si remplie
Renvoie False si non remplie

- compteur_O(self): 

Méthode qui retourne le nombre de "O" sur le plateau.

- symetrique(self, other): 

Méthode qui vérifie si le plateau actuel est symétrique par rapport à un autre plateau.

- minimax(self, coupsPossibles, alpha, beta): 

Algorithme Minimax avec élagage alpha-bêta pour trouver le meilleur coup à jouer. Il évalue chaque coup possible en appelant evaluate_coup() et retourne le meilleur coup trouvé.

- evaluate_coup(self, coup, alpha, beta): 
Méthode qui évalue un coup donné en calculant un score basé sur heuristique_formation_L. Elle utilise la méthode heuristique_formation_L() pour évaluer la formation de "L" optimales.

- heuristique_formation_L(self, position, coup): 
Méthode qui calcule un score basé sur la formation de "L" optimales autour du coup donné.
Elle permet évalue la formation de "L" optimales autour d'un coup donné. Elle examine les cases voisines du coup et attribue un score en fonction de l'efficacité de la formation en L.

- nouveaux_coups(self, x, y): 
Méthode qui renvoie une liste des nouveaux coups possibles après avoir joué un coup à la position (x, y).

### Définition 

- Heuristique :

Qui procède par approches successives en éliminant progressivement les alternatives et en ne conservant qu'une gamme restreinte de solutions tendant vers celle qui est optimale. -> https://www.cnrtl.fr/definition/heuristique#:~:text=Qui%20procède%20par%20approches%20successives,Méthode%20heuristique%20p.

- Elagage alpha-bêta :
L'élagage alpha-bêta est une technique utilisée dans l'algorithme Minimax pour réduire le nombre de nœuds explorés dans l'arbre de recherche. L'idée principale est de ne pas explorer les branches de l'arbre qui ne sont pas susceptibles de donner de meilleures solutions que celles déjà trouvées. Cela permet d'optimiser l'algorithme du minimax classique et de gagner en temps de calcul.
