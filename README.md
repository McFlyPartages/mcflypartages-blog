* [X] Redimensionner Avatar
* [X] Convertir en WebP Avatar/Logo/article Vierge
* [X] Ajouter site propulsé dans footer
* [ ] Bloquer menu (fixed top)
* [X] Ajouter la modification via GitHub
* [X] Shortcode lien Forum HACF. 
```
Simple lien : 
{{< forumhacf "lien_vers_forum" "Titre_du_post">}} 
Multi liens : 
{{< multiforumhacf >}}
    {{< forumhacf "lien_vers_forum" "Titre_du_post">}}
    {{< forumhacf "lien_vers_forum" "Titre_du_post">}}
{{< /multiforumhacf >}}
```
* [X] Catégorie en Capitalise
* [X] Tags en lowercase
* [X] Dates FR
* [X] Rendre tags et catégories cliquable dans la barre latérale
* [X] Analyse via [Matomo](https://fr.matomo.org/) presentation [ici](https://zestedesavoir.com/tutoriels/2508/matomo-analytics/)
* [ ] Monitoring Via [UpTimeRobot](uptimerobot.com)
* [ ] Afficher HeroImg du Front Matter
* [X] index.html : ne lister que les articles.
* [ ] Créer template "series"
* [ ] Categories : hauteur constante
* [ ] ~~Workflow : transfert vers ftp site officiel [Deploy ftp](https://github.com/marketplace/actions/ftp-deploy)~~
* [ ] Vérifier les cookies.Aucun pour le moment
* [X] Workflow Github pages
* [X] Workflow envoi vers sftp en cour
* [X] Images : Ajouter shortcodes Gallery + image processing `{{< gallery folder="infos" >}}` infos=le nom du dossier contenant les images
* [X] Images : Cumuler Render image et traitement responsive multiformat auto Image webP + alternative
* [ ] list : Liste article avec hero [ici](https://www.markuptag.com/hero-banner-html-design-in-bootstrap-5/)
* [X] single : Shortcode Alerte. `{{< alert "Message **succees**" success >}}` danger/sucess/warning/info.
* [ ] theme : Ajouter les options (affichage menu etc [ici](https://github.com/razonyang/hugo-theme-bootstrap/tree/master/layouts/partials/sidebar))
* [X] link : Render-Link
* [X] theme : Corriger lien mail dans partials rs
* [X] link : Ajouter target_blank dans partial RS rel="noreferrer"
* [X] single : Partials SocialShare Ajouter Whatsapp
* [X] single : Ajout du Head personalisé en fonction de la page (description et mots clés)
* [X] single : Correction de l'affichage des keywords (suppression [] remplacé par une ", ")
* [ ] theme : Passage de bootstrap icon a Font Awesome ??
* [X] single : Shortcode de citation `{{< quote "Message **citation**" "artiste **anonyme**" >}}`
* [X] index : Ajouter la pagination page d'acceuil,https://glennmccomb.com/articles/how-to-build-custom-hugo-pagination/
* [ ] single : Ajouter les [articles en relation](https://bout2code.fr/tutos/creer-un-site-avec-hugo/comment-creer-un-site-avec-hugo-partie-7-ajouter-du-contenu-en-relation/)
* [ ] index : Exclure Page de la liste d'article
* [X] Shortcode user HACF et HACF `{{< userha "user" haoff >}}` option `hacf` ou `haoff`
* [X] Shortcode liens HA repositories et BluePrint `{{< haautoconfig bp "url" >}}` option `bp` pour blueprint ou `depot` pour repositories
* [ ] Image voir pour redimenssion max de la taill d'origine.
  
