---
title: "Hugo : Déployer sur GitHub Pages"
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
- github
---

Nous avons vu comment [installer Hugo](../hugo_installation/hugo_installation.md) nous allons voir comment rendre notre site disponible avec GitHub Pages.

C'est un service gratuit mis à disposition par GitHub.

## Prérequis GitHub

Pour commencer il vous faut un compte GitHub puis il vous faut créer un 'repositories' publique que l'on nomme 'nomdevotresite.github.io' puis on lui ajoute avec un fichier 'readme'.

Ensuite nous allons créer deux branches supplémentaires 'source' et 'modif':
* 'main' : Contiendra le site généré,
* 'source' : Contiendra les fichiers/dossiers de votre site au format Hugo,
* 'modif' : sera votre branche de travail.

>Explication : vous travaillez sur 'modif' puis validez les changement sur 'source', ensuite grace aux GitHub Actions, quand il y a un changement sur la branche 'source' alors GitHub générera a nouveau votre site dans la branche 'main'.

Passer votre branche 'source' en branche ar défaut dans 'settings', 'branch' puis sélectionner 'source' à la place de 'main'.

## GitHub Pages

Nous avons notre 'repositories' puis nos trois branches, nous allons donc déclarer a GitHub Pages que notre branche par défaut est 'source' et plus 'main'.

Dans le 'settings' de votre repositories, rechercher 'Pages' dans le menu de gauche puis changer la source par défaut par 'source' puis laisser '/root', enfin cliquer sur 'save'.

## Github Actions
Les GitHub Actions sont une liste de tache a effectuer quand il y a un changement par exemple. Nous allons nous en servir pour effectuer des taches lorsqu'il y a un 'push' sur le branche 'source' pour régénérer le site.

Vérifiez dans 'settings', 'actions' de votre 'repositories' qu'il y a bien 'Allow all actions' de sélectionné.

Ensuite ajouter un nouveau fichier '.github/worflows/gh-pages.yaml'.
Coller le contenu suivant :
'''
name: Deploy to Github Pages

# run when a commit is pushed to "source" branch
on:
  push:
    branches:
    - source #branche a surveiller

jobs:
  deploy:
    runs-on: ubuntu-18.04
    steps:
    # checkout to the commit that has been pushed
    - uses: actions/checkout@v2
      with:
        submodules: true  # Fetch Hugo themes (true OR recursive)
        fetch-depth: 0    # Fetch all history for .GitInfo and .Lastmod
    
    # install Hugo
    - name: Setup Hugo
      uses: peaceiris/actions-hugo@v2
      with:
        hugo-version: '0.83.1'
        extended: true

    # build website
    - name: Build
      run: hugo --minify

    # push the generated content into the `main` (former `master`) branch.
    - name: Deploy
      uses: peaceiris/actions-gh-pages@v3
      with:
        github_token: ${{ secrets.GITHUB_TOKEN }}
        publish_branch: main #branche dans laquelle est générer le site
        publish_dir: ./public
'''

Maintenant a chaque fois qu'il y a un 'push' sur la branche 'source' le site sera automatiquement généré.

Faite le test et rendez vous sur https://nomdevotresite.github.io pour voir le résultat.

## Sources
* [Guide Theme Toha](https://toha-guides.netlify.app/)
* [GitHub Actions pour Hugo](https://github.com/peaceiris/actions-hugo)