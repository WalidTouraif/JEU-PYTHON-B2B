Jeu de combat en Python (avec MongoDB)

Petit jeu en console fait en Python pour mon Bachelor Informatique à SupDeVinci. On choisit une équipe de 3 personnages et on affronte des monstres l'un après l'autre, jusqu'à la défaite. Les personnages et les monstres sont stockés dans une base de données MongoDB.

Comment ça marche
Le menu propose de jouer ou de quitter.
Le joueur choisit 3 personnages parmi ceux de la base de données (si le numéro tapé n'existe pas, le jeu redemande).
L'équipe affronte un monstre pris au hasard :
chaque personnage vivant attaque : dégâts = dégâts du personnage − défense du monstre (jamais en dessous de 0) ;
si le monstre survit, il attaque au hasard un personnage encore vivant, avec le même calcul ;
le combat s'arrête quand le monstre est vaincu ou que toute l'équipe est morte (« YOU DIED »).
Quand l'équipe gagne, le score augmente de 1 et l'équipe gagne l'or du monstre, puis un nouveau monstre arrive.
Quand l'équipe perd, la partie s'arrête et le score final s'affiche.
Les fichiers
Fichier	Rôle
main.py	Menu, choix de l'équipe et boucle de jeu (score et or)
jeu.py	Le combat : calcul des dégâts, attaque de l'équipe, attaque du monstre
db_init.py	Remplit la base jeu dans MongoDB : 5 personnages (classe, dégâts, défense, points de vie) et 5 monstres (dégâts, défense, points de vie, récompense en or)
utils.py	Lit les personnages et les monstres dans MongoDB et en fait des objets
modèles.py	Les classes Personnage et Monstre
Lancer le jeu

Il faut Python et MongoDB installés sur l'ordinateur, avec MongoDB démarré.

pip install pymongo
python db_init.py
python main.py

db_init.py se lance une seule fois pour remplir la base (il la vide d'abord, donc pas de doublons).

Ce que j'ai appris
organiser un programme Python en plusieurs fichiers, avec des fonctions et des classes ;
me connecter à une base MongoDB et lire / écrire des documents avec pymongo ;
utiliser Git et GitHub pour suivre mes modifications.
Ce que je pourrais améliorer
remettre les points de vie de l'équipe entre deux combats (aujourd'hui ils ne remontent pas) ;
utiliser l'or pour acheter des améliorations ;
enregistrer les meilleurs scores dans MongoDB.
