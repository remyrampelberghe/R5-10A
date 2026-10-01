Question 1: On va les utilser plus tard lors des prochaines séance 

Question 2: Le service « redis » est celui qui n’a pas de volumes , ils sont supprimés lorsque le conteneur est arrêté .

Question 3 : Cette ligne effectue une redirection de ports. Le premier nombre (`15432`) est le port sur la machine hôte , et le deuxième est le port à l'intérieur du conteneur .

Question 4 : C'est acceptable ici car il s'agit d'un environnement de développement local

Question 5 : docker compose exec exécute une commande dans un conteneur actif. La commande redis-cli s'exécute donc directement à l'intérieur du conteneur pixelhub-redis, pas sur la machine hôte.

Question 6 : Ça fonctionne grâce à la redirection de ports : l'application tourne sur l'hôte et contacte localhost:15432, que Docker redirige vers le port 5432 du conteneur PostgreSQL.

Question 7 : Non, car le code vérifie si la table est vide (!db.Players.Any()). Les données étant déjà persistées dans le volume Docker de PostgreSQL, l'insertion n'est pas réexécutée.