* [X] Redimensionner Avatar
* [X] Convertir en WebP Avatar/Logo/article Vierge
* [ ] Ajouter site propulsé dans footer
* [ ] Bloquer menu (fixed top)
* [ ] Ajouter la modification via GitHub
* [ ] Shortcode lien Forum HACF.
* [X] Catégorie en Capitalise
* [X] Tags en lowercase
* [X] Dates FR
* [X] Rendre tags et catégories cliquable dans la barre latérale
* [ ] Analyse via [Matomo](https://fr.matomo.org/) presentation [ici](https://zestedesavoir.com/tutoriels/2508/matomo-analytics/)
* [ ] Monitoring Via [UpTimeRobot](uptimerobot.com)
* [ ] Afficher HeroImg du Front Matter
* [X] index.html : ne lister que les articles.
* [ ] Créer template "series"
* [ ] Categories : hauteur constante
* [ ] ~~Workflow : transfert vers ftp site officiel [Deploy ftp](https://github.com/marketplace/actions/ftp-deploy)~~
* [ ] Vérifier les cookies.
* [X] Workflow Github pages
* [ ] Workflow envoi vers sftp
```
name: Deploy to Github Pages

# run when a commit is pushed to "source" branch
on:
  push:
    branches:
    - source

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
        hugo-version: '0.90.0'
        extended: true

    # build website
    - name: Build
      run: hugo --minify

    # push the generated content into the `main` (former `master`) branch.
    - name: Deploy
      uses: peaceiris/actions-gh-pages@v3
      with:
        github_token: ${{ secrets.GITHUB_TOKEN }}
        publish_branch: main # if your main branch is `master` use that here.
        publish_dir: ./public
    - name: "Deploy"
      uses: milanmk/actions-file-deployer@master
      with:
        remote-protocol: "sftp"
        remote-host: ${{ secrets.SFTP_HOST }}
        remote-port: ${{ secrets.SFTP_PORT }}
        remote-user: ${{ secrets.SFTP_USER }}
        remote-password: ${{ secrets.SFTP_PASSWD }}
        remote-path: "/"
```
* [x] Images : Ajouter shortcodes Gallery + image processing `{{< gallery folder="infos" >}}` infos=le nom du dossier contenant les images
* [x] Images : Cumuler Render image et traitement responsive multiformat auto Image webP + alternative
* [ ] Liste article avec hero [ici](https://www.markuptag.com/hero-banner-html-design-in-bootstrap-5/)
* [x] Shortcode Alerte. `{{< alert "Message **succees**" success >}}` danger/sucess/warning/info.
* [ ] Ajouter les options (affichage menu etc [ici](https://github.com/razonyang/hugo-theme-bootstrap/tree/master/layouts/partials/sidebar))
* [X] Render-Link
* [x] Corriger lien mail dans partials rs
* [x] Ajouter target_blank dans partial RS rel="noreferrer"
* [x] Partials SocialShare Ajouter Whatsapp
* [x] Ajout du Head personalisé en fonction de la page (description et mots clés)
* [x] Correction de l'affichage des keywords (suppression [] remplacé par une ", ")
* [ ] Passage de bootstrap icon a Font Awesome ??
* [ ] Shortcode de citation `{{< quote "Message **citation**" "artiste **anonyme**" >}}`