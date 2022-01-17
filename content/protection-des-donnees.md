---
title: "Protection des données"
date: 2021-11-19T23:28:02+01:00
lastmod:
draft: false
layout : a-propos
---
{{< alert "Cette page est en cours de rédaction, elle est complétée au fur à mesure." warning >}}

Actuellement, le site n'installe aucun cookie, sauf, si vous décidez de ne pas participer à l'analyse (même conforme RGPD). 
Il y a maintenant, des moyens de suivre son audience en respectant la vie privée de ses utilisateurs et cela va être mon défi. 
Je ne peux pas vous parler "respect de la vie privée" si je vous piste via les médias que j'utilise.

La RGPD est quand même une usine à gaz, mais pour une fois que cela va dans le sens de l'utilisateur... .

Pour aider les webmasters au respect de la vie privée de leurs visiteurs, la CNIL a écrit [différents articles concernant la gestion des cookies](https://www.cnil.fr/fr/cookies-et-autres-traceurs) et autres données privées pouvant être recueillis lors de vos sessions web.

Voici les informations du concernant l'analyse du blog.

## Construction du blog.
Le blog est construit via un générateur de page statique.
Pour simplifier, à chaque nouveau contenu que j'ajoute, il régénère chaque page html. 
Cela permet de ne pas utiliser de :
* Serveur PHP, 
* Base de données,
Rien qui puisse adapter l'affichage du blog en fonction de l'utilisateur.

Plusieurs articles seront sûrement écrits sur cette technologie qui, je pense, suffirait à la majorité des sites personnels.

## Analyse de l'audience du site web.
L'analyse d'audience est le nerf de la guerre sur un site web professionnel, mais pour un particulier ?

La plupart des services d'analyse d'audience s'adapte au grand publique dans l'optique de récupérer un maximum d'informations sur les visiteurs qui serviront à leur clientèle pro. 
Ils vous fournissent, en échange quelques informations, un service qui dans la plupart des cas n'est peu, voir pas analysé par les webmasters amateurs.

Voici une [liste des services d'audience pouvant être exempté du bandeau de gestion de cookie](https://www.cnil.fr/fr/cookies-solutions-pour-les-outils-de-mesure-daudience) en respectant le guide de configuration associé.

Pour le suivi du blog, j'utilise [Matomo](https://matomo.org/) en respectant le [guide fourni par la CNIL](https://www.cnil.fr/sites/default/files/atoms/files/matomo_analytics_-_exemption_-_guide_de_configuration.pdf).
Cela me permet de ne  pas avoir besoin d'afficher de bandeau de gestion de cookie.
Ce dernier est très utile pour prendre conscience de la traque organisée, mais (je trouve) très pénible lorsque l'on navigue sur un site et qu'il s'affiche en bloquant toute possibilité de voir l'article.

Cet outil remplace Google Analytics tout en gardant les données récoltées a l'endroit ou il est installé. Aucune donnée sur vos visiteurs n'est envoyée, échangée ou **vendue**.

Personnellement, je n'ai pas besoin de savoir où vous avez cliqué ni combien de temps vous avez laissé votre souris au même endroit.

Je découvre encore cet outil et je ne peux donc pas vous en dire plus pour le moment.

{{< alert "Si vous souhaitez analyser le comportement des sites que vous visitez je vous recommande l'outil de la CNIL [CookieViz](https://github.com/LINCnil/CookieViz). Je prépare un article pour bientôt." info >}}

## Fonction de partage sur les réseaux sociaux.
Pour vous permettre de partager mes articles sur les différents réseaux sociaux, j'utilise une fonction html  brut et non une API ou autres services fournissant un code tout fait incluant une ribambelle de pisteurs.

## L'utilisation des médias sociaux.
Malheureusement, j'utilise aussi des services "avaleurs de données" qui ont pignon sur rue (YouTube, Facebook, Twitter).
J'essaye de les doubler avec leurs alternatives libres (PeerTube, Mastodon, Mobilizon, etc. 


{{< alert "Cette page est en cours de rédaction, elle est complétée au fur à mesure." warning >}}
