# Gestion d'une flotte de taxis électriques autonomes

## Description du projet

Ce projet présente un système de gestion pour une flotte de taxis électriques autonomes. Nous détaillons ici les différentes parties du projet et les algorithmes utilisés pour mettre en œuvre ce système.

Le projet se déroule en plusieurs étapes :

1. **Récupération des données** : Nous collectons les données nécessaires telles que la liste des appels des clients prévus à l'avance, le réseau routier utilisé, et les caractéristiques des véhicules.
2. **Recherche de trajet** : Nous utilisons l'algorithme de Dijkstra pour calculer les itinéraires optimaux dans le réseau routier.
3. **Simulation de la gestion de la flotte** : Nous simulons la gestion de la flotte et évaluons les performances du système. Les indicateurs clés incluent le nombre d'appels non desservis, l'état de recharge des véhicules, les bénéfices réalisés, etc.

## Structure du projet

Le dossier fourni contient les fichiers suivants :

- **structure.h** : Déclare les structures et les fonctions utilisateurs du projet (149 lignes de code).
- **structure.c** : Définit les fonctions utilisateurs (646 lignes de code).
- **main.c** : Contient la fonction principale du projet (270 lignes de code).
- **Makefile** : Gère la compilation du projet.

Le projet inclut également des fichiers de données pour la simulation :

- `rete.txt` : Données du réseau routier.
- `veicoli.txt` : Données des véhicules.
- `chiamate.txt` : Données des appels des clients.

## Compilation et exécution

### Compilation

Pour compiler le projet, utilisez le **Makefile** fourni. Si vous souhaitez utiliser d'autres fichiers de données pour la simulation, vous pouvez modifier les fichiers utilisés dans le code du makefile.

Voici le contenu du **Makefile** utilisé pour la compilation :

```makefile
CC = gcc
CFLAGS = -Wall -Wextra -std=c99

all: programme

programme: structure.o main.o
	$(CC) $(CFLAGS) -o programme structure.o main.o

structure.o: structure.c structure.h
	$(CC) $(CFLAGS) -c structure.c

main.o: main.c structure.h
	$(CC) $(CFLAGS) -c main.c

default-run:
	./programme 02-rete.txt 02-veicoli.txt 02-chiamate.txt

clean:
	rm -f *.o programme


1. compilez le projet avec la commande : make 
2. lancer la simulation en utilisant : make default-run

Vous pouvez remplacer les fichiers de données (02-rete.txt, 02-veicoli.txt, 02-chiamate.txt) par vos propres fichiers si nécessaire.
