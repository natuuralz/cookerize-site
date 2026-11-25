# Le site Cookerize — comment le mettre en ligne

Site **statique**, désormais **en trois langues** : français à la racine, anglais
dans `en/`, espagnol dans `es/`. Chaque langue a son sélecteur (Français ·
English · Español) en haut de page. Rien à compiler, aucun serveur à
administrer, aucune base de données. C'est exactement ce qu'il faut pour
**GitHub Pages**.

> **Le site EST en ligne.** Il est publié par **GitHub Pages**, depuis le dépôt
> **`natuuralz/cookerize-site`** (public), et servi à l'adresse
> **https://www.cookerize.net/**. Les pages de confidentialité et de suppression
> de compte y répondent **HTTP 200** — vérifié le 3 novembre 2026. La procédure de
> publication ci-dessous reste la marche à suivre pour toute mise à jour.

## 1. Arborescence complète du site

```
site/
├── index.html                 FR — présentation (racine)
├── confidentialite.html       FR — politique de confidentialité  ★ Google Play
├── suppression-compte.html    FR — suppression de compte          ★ Google Play
├── mentions-legales.html      FR — éditeur, hébergeur, achats
├── conditions.html            FR — conditions d'utilisation  ★ Google Play
├── app-ads.txt                déclaration des vendeurs AdMob (racine du domaine)
├── styles.css                 charte commune aux trois langues
├── img/
│   ├── icone.png              favicon
│   ├── icone-maitre.png       icône haute résolution
│   ├── banniere.png           bannière d'en-tête
│   ├── ecran-01-accueil.jpg
│   ├── ecran-02-bibliotheque.jpg
│   ├── ecran-03-recherche.jpg
│   ├── ecran-04-fiche.jpg
│   ├── ecran-09-frigo.jpg
│   ├── ecran-10-batch.jpg
│   └── mobile/               captures par langue (fr/en/es-accueil…recette.webp)
├── en/                        version anglaise
│   ├── index.html
│   ├── privacy.html
│   ├── delete-account.html
│   ├── legal-notice.html
│   └── terms.html
└── es/                        version espagnole
    ├── index.html
    ├── privacidad.html
    ├── eliminar-cuenta.html
    ├── aviso-legal.html
    └── condiciones.html
```

**Total : 45 fichiers** — 15 pages HTML, 1 feuille de style, 27 images (9 à la
racine de `img/` plus 18 dans `img/mobile/`), `app-ads.txt`, et ce README.
Trois pages sont **celles que Google Play vérifie ou réclame** : la politique de
confidentialité, la suppression de compte, et les conditions d'utilisation — cette
dernière est saisie dans « Contenu de l'application ». Les deux premières
**ne doivent jamais changer de nom ni de place**.

## 2. Mettre en ligne — pas à pas (GitHub Pages)

Le site est servi par **GitHub Pages** depuis un **autre dépôt**,
**`natuuralz/cookerize-site`** (public), réglé ainsi :

- **Branche** : `main`
- **Dossier publié** : `/` (racine du dépôt)
- **`CNAME`** contenant `www.cookerize.net` — le domaine personnalisé
- **`.nojekyll`** — pour que GitHub Pages serve les fichiers tels quels,
  sans traitement Jekyll

Ce dépôt porte une **copie du dossier `site/`** de ce dépôt-ci, plus ces deux
fichiers propres à Pages (`CNAME`, `.nojekyll`). Il n'y a donc rien à configurer
chez un hébergeur : on modifie les fichiers **ici**, dans `site/`, on les
recopie vers le dépôt du site, on pousse, et **GitHub Pages reconstruit le site
tout seul en une minute**.

```sh
# 1) Cloner UNE fois le dépôt du site, à côté de ce dépôt.
cd C:/Users/natuuralz/Cookerize
git clone https://github.com/natuuralz/cookerize-site.git cookerize-site

# 2) Recopier le contenu de site/ vers le dépôt du site.
#    `cp -R site/. …` copie le CONTENU (pas le dossier site lui-même) et laisse
#    CNAME et .nojekyll en place : ils ne vivent que dans le dépôt du site.
#    Ce README-ci est de la documentation de travail : il n'a rien à faire en
#    ligne, on le retire de la copie.
cd app
cp -R site/. ../cookerize-site/
rm -f ../cookerize-site/README.md

# 3) Publier : GitHub Pages reconstruit le site automatiquement.
cd ../cookerize-site
git add -A
git commit -m "Mise à jour du site"
git push origin main
```

Deux points d'attention :

- `cp -R` **écrase** les fichiers existants mais **n'efface pas** ceux qu'on
  aurait supprimés dans `site/` : si un fichier disparaît ici, le retirer aussi
  là-bas (`git rm <fichier>`) avant de pousser.
- **Ne jamais supprimer `CNAME` ni `.nojekyll`** dans le dépôt du site : sans
  eux, le domaine personnalisé et l'absence de traitement Jekyll sautent.

Après quelques dizaines de secondes, le site est à jour à l'adresse ci-dessous.

## 3. Les adresses publiques attendues, fichier par fichier

Base : **`https://www.cookerize.net/`**

| Fichier local | Adresse publique |
|---|---|
| `index.html` | `https://www.cookerize.net/` |
| `confidentialite.html` | `https://www.cookerize.net/confidentialite.html` ★ |
| `suppression-compte.html` | `https://www.cookerize.net/suppression-compte.html` ★ |
| `mentions-legales.html` | `https://www.cookerize.net/mentions-legales.html` |
| `conditions.html` | `https://www.cookerize.net/conditions.html` ★ |
| `app-ads.txt` | `https://www.cookerize.net/app-ads.txt` |
| `styles.css` | `https://www.cookerize.net/styles.css` |
| `img/icone.png` | `https://www.cookerize.net/img/icone.png` |
| `img/banniere.png` | `https://www.cookerize.net/img/banniere.png` |
| `img/ecran-01-accueil.jpg` … `ecran-10-batch.jpg` | `https://www.cookerize.net/img/ecran-01-accueil.jpg` … |
| `img/mobile/…` | `https://www.cookerize.net/img/mobile/…` |
| `en/index.html` | `https://www.cookerize.net/en/` |
| `en/privacy.html` | `https://www.cookerize.net/en/privacy.html` |
| `en/delete-account.html` | `https://www.cookerize.net/en/delete-account.html` |
| `en/legal-notice.html` | `https://www.cookerize.net/en/legal-notice.html` |
| `en/terms.html` | `https://www.cookerize.net/en/terms.html` |
| `es/index.html` | `https://www.cookerize.net/es/` |
| `es/privacidad.html` | `https://www.cookerize.net/es/privacidad.html` |
| `es/eliminar-cuenta.html` | `https://www.cookerize.net/es/eliminar-cuenta.html` |
| `es/aviso-legal.html` | `https://www.cookerize.net/es/aviso-legal.html` |
| `es/condiciones.html` | `https://www.cookerize.net/es/condiciones.html` |

### Les adresses que Google vérifie — à ne jamais casser

**Google Play vérifie deux pages**, saisies telles quelles dans la fiche du
magasin :

- **Politique de confidentialité** → `https://www.cookerize.net/confidentialite.html`
- **Suppression de compte** → `https://www.cookerize.net/suppression-compte.html`

Ces deux adresses **ne doivent jamais changer de nom ni de dossier** : si elles
bougeaient, la fiche Play pointerait dans le vide et l'application pourrait être
retirée. Elles doivent répondre en **HTTPS (200)**, sans redirection vers une
autre page (voir §4). Les pages équivalentes existent aussi en anglais
(`en/privacy.html`, `en/delete-account.html`) et en espagnol
(`es/privacidad.html`, `es/eliminar-cuenta.html`), mais ce sont les deux
adresses françaises qui sont déclarées dans la fiche.

## 4. Le HTTPS n'est pas une option

Google **refuse** une politique de confidentialité servie en `http://` : il
exige une adresse `https://` avec un cadenas valide. Un site en `http` seul est
donc un motif de rejet de la fiche Play. GitHub Pages fournit le HTTPS
automatiquement : le certificat Let's Encrypt se pose tout seul dès que le
domaine personnalisé (`CNAME`) est reconnu, à condition que l'option
**« Enforce HTTPS »** soit cochée (Settings → Pages du dépôt du site). Une fois
en place, taper `cookerize.net` doit basculer tout seul sur
`https://www.cookerize.net`.

## 5. Vérifier après la mise en ligne

Ouvrir une invite de commandes (Windows : touche Windows, taper `cmd`, Entrée)
et lancer ces quatre commandes, une par une. Le **code** attendu est en
commentaire ; `200` = la page répond, tout va bien.

```sh
curl -I https://www.cookerize.net/                 # attendu : HTTP/1.1 200 OK
curl -I https://www.cookerize.net/confidentialite.html    # attendu : 200
curl -I https://www.cookerize.net/suppression-compte.html # attendu : 200
curl -I https://www.cookerize.net/en/                      # attendu : 200
curl -I https://www.cookerize.net/app-ads.txt              # attendu : 200
```

Puis, à l'œil, dans un navigateur :

- `https://www.cookerize.net/` — la présentation s'affiche, les captures
  défilent, le sélecteur **English / Español** en haut mène bien aux pages
  anglaise et espagnole.
- `https://www.cookerize.net/es/` — la version espagnole s'affiche, les images
  se chargent (c'est le signe que `img/` a bien été recopié).
- Un **cadenas** apparaît dans la barre d'adresse.
- Taper `https://cookerize.net` (sans `www`) redirige bien vers
  `https://www.cookerize.net`.

## Ce qu'il reste à faire sur le site

- **Le nom de domaine** (`cookerize.net`) et son renouvellement ne sont pas
  gérés ici : voir le dossier `01 - Administratif` du Drive.
- La page de présentation annonce « bientôt sur Google Play » : **à remplacer par
  le lien du magasin** le jour de la publication (dans les trois langues).
- Les captures d'écran devront être remplacées par des captures de la version
  publiée, avec la marque visible.
- Si un texte anglais ou espagnol change : **mettre à jour la page de chaque
  langue** dans le même mouvement, sinon une version reste en arrière.
