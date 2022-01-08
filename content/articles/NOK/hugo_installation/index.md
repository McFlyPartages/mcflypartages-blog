---
title: "Hugo : Installation"
date: 2021-06-30
lastmod: 
draft: true

heroimg: images/articles-vierge.webp
#description: 
#keywords:

categories:
- hugo

series:
- hugo
  
tags:
- jamstack
- site statique
---

Si vous m'avez suivi lors de mes début sur le net, vous avez constaté que j'ai ete sur [plumexml](https://pluxml.org/), [Wordpress](https://fr.wordpress.org/), [PHPBoost](https://www.phpboost.com/) et me voila maintenant sur [Hugo](https://gohugo.io/), qui devrait être mon dernier transfert avant un long moment.

On choisi souvent la simplicité, mais celle-ci demande souvent des ressources qui sont surdimensionné pour l'objectif final.

As t- on besoin d'une base de donnée pour partager des articles ? d'un panneau d'administration complexe avec de multiple réglages ? des commentaires ? plein de choses qui demande d'investir dans une solution ou un hébergement avec un coût qui peut être supprimé.

Nous allons voir comment héberger gratuitement vos pages avec GitHub et la Jamstack Hugo pour un site statique "dynamique".

Pas besoin de Base de donnée, de PHP, de SQL, autant de choses pouvant ajouter son lot de vulnérabilités.

## Installation

Pour faciliter la chose, je passe par [VSCodium](https://vscodium.com/) qui est le binaire open-source de [Visual Studio Code](https://code.visualstudio.com/) donc sans le traçage de Microsoft.

>Toutes les étapes de ce tutoriel peuvent être réalisé avec [Visual Studio Code](https://code.visualstudio.com/).

Une fois VSCodium installé, il vous faut ajouter l'extension 'Hugo Helper'. Cette extension vous permet de lancer les commandes 'hugo' comme 'hugo serve' ou 'hugo new site nom_du_site.com'.

Créer un dossier puis ouvrez le avec VSCodium.

>Certaines extensions peuvent être intéressantes comme 'Markdown All in One', 'Hugo Snippets' ou 'Hugo Language and Syntax Support'.

## Création de votre site.

Nous allons maintenant créer l'architecture de notre site web.

Il vous faut aller dans le terminal de VSCodium puis taper le commande 'hugo new site mon_site.fr'

Vous devriez avoir tous les dossiers de l'architecture d'un site [Hugo](https://gohugo.io/).


## Architecture par défaut
Voici la structure de base d'un site hugo.

```txt
.
├── archetypes 
│   └── default.md
├── config.toml
├── content
├── data
├── layouts 
├── resources
│   └── _gen
│       ├── assets
│       └── images
├── static 

```

#### archetypes
Il contient les "Front Matter" par défaut des différents types de publication (articles, news, etc). Il peut être en .yml, .tom ou en .json la seul différence est le balisage. `---` pour le .toml, `+++` pour le .yaml.

Il est possible de créer un archétype par type de contenu. Ce que nous ferons.

Ex:
```
---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
draft: true
tags: ["hugo" , "tutoriels"]
---
```

#### config.toml .yaml
Ce fichier contient les paramètres généraux du futur site internet comme les menus, les paramètres des shortcodes etc.

#### content
Ce dossier contient tous les articles et news ou toutes les pages de contenu.
C'est le dossier le plus utilisé.
Il peut être composé de sous dossier qui ferons l'arborescence du site.
Dans notre cas pour le moment il sera composé du sous dossier "news" et "articles" par exemple.

La commande pour créer un nouveau contenu est `hugo new articles/mon_premier_article.md` par exemple amis garce a VSCodium pas besoin de code, il suffit d'aller dans 'Affichage', 'Palette de commandes', 'Hugo: create content'.

#### data
C'est un dossier qui peut servir a stocker des fichiers pouvant être réutilisé par Hugo.

#### layouts
Ce sont toutes les "structures/squelettes" ou "templates" HTML et CSS des différents type de contenus ex: news, articles, etc

##### _default
Dans `default` il y a trois fichiers:
* baseof.html : Template par défaut pour toutes les pages autres que l'index et celles liées aux contenus
* list.html : C'est le template par défaut d'affichage des listes (liste d'articles ou liste de news).
* single.html : C'est le template par défaut d'affichage du contenu (un article ou une news)

##### partials
Les partials sont des fichiers 'html' qui peuvent être repris dans n'importe quelle template, cela évite de devoir réécrire à chaque fois.

Il s'inclut avec le code suivant dans les templates.
`{{ partial "chemin-vers/mon-partial.html" . }}`

#### static
Ici se trouve toutes les données fixes comme le fichier CSS, JS, les images du site, etc

#### thème
Pas de miracle, on y retrouve le thème hahaha.

Si vous y regardez a deux fois vous verrez que c'est quasiment la même structure que celle du site.

Nous arrivons a la fin de cette brèves explication de l'architecture Hugo.

## Ajout d'un thème.

Hugo permet de bénéficier de [plusieurs thèmes gratuitement](https://themes.gohugo.io/), malheureusement nous ne pouvons pas changer de thème d'un claquement de doigt car ils ont chacun leurs spécificités.
Pour les connaitres, il vous suffit de lire la page associé au thème que vous avez choisi.

Pour ajouter un thème existant, il faut suivre les commandes données dans la page de presentation du thème.

## Création d'un thème.

Il est aussi possible de partir d'un thème vierge via la commande '`hugo new theme nomdutheme'.

A vous maintenant de créer vos template de page, de liste, de footer, de header, etc etc.

## Conclusion

Nous en avons terminé pour cette première partie liée à l'installation d'Hugo et à son architecture.