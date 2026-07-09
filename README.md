# grimoire

Une veille commune en **informatique**, **cybersécurité** et **IA** : des fiches
courtes qui pointent vers des repos, outils, sites et cours. Le contenu est écrit
en Markdown ; le site est généré par [Hugo](https://gohugo.io/) avec le thème
[risotto](https://github.com/joeroe/risotto), remis à la sauce « base de
connaissances » (arbre de navigation à gauche, façon hugo-book).

> Démo : `https://<utilisateur>.github.io/<nom-du-repo>/` (à compléter après le premier déploiement).

## À quoi ça ressemble

- Barre latérale gauche : arbre repliable de toutes les sections, construit
  automatiquement à partir des dossiers de `content/`.
- Colonne centrale : la fiche.
- Colonne de droite : infos de la page (description, tags, sommaire, lien
  « éditer »).
- Palette de couleurs unique changeable en une ligne (Catppuccin Mocha par
  défaut, plus les 16 thèmes de risotto).

## Démarrer en local

Il faut **Hugo extended** (version 0.128 ou plus récente conseillée).

```bash
# Installer Hugo extended : https://gohugo.io/installation/
git clone https://github.com/<utilisateur>/<nom-du-repo>.git
cd <nom-du-repo>
hugo server
# puis ouvrir http://localhost:1313/
```

Le thème est déjà inclus dans `themes/risotto/` : rien d'autre à installer.

## Ajouter une ressource

Deux minutes, trois façons.

1. Créer une nouvelle fiche à partir du modèle :

   ```bash
   hugo new cyber/ma-fiche.md
   ```

   Ça crée un fichier prérempli (titre, tags, un bloc `resource` d'exemple).

2. Ou copier un `.md` existant dans `content/<domaine>/` et l'adapter.

Chaque ressource est un petit bloc :

```markdown
{{</* resource title="Nom de l'outil" url="https://exemple.com" type="repo" tags="recon, réseau" */>}}
Une phrase qui explique pourquoi c'est utile.
{{</* /resource */>}}
```

- `type` : `repo`, `outil`, `site`, `cours` ou `video` (change juste la couleur du badge).
- `tags` : séparés par des virgules.
- Le texte entre les deux balises accepte du Markdown (gras, liens, etc.).

Encadré optionnel :

```markdown
{{</* note type="tip" */>}}
Un conseil utile. Types : info, tip, warn.
{{</* /note */>}}
```

## Comment s'organise la navigation

L'arbre de gauche **se construit tout seul** à partir de l'arborescence de
`content/`. Pour ajouter un domaine ou un sous-thème, il suffit de créer un
dossier avec un `_index.md` :

```
content/
  cyber/
    _index.md            <- la section "Cybersécurité"
    apprendre.md         <- une fiche
    offensif/
      _index.md          <- une sous-section
      reconnaissance.md  <- une fiche
```

Dans chaque `_index.md`, deux champs pilotent l'affichage et l'ordre :

```toml
+++
title = "Cybersécurité"
description = "Une phrase de présentation."
weight = 20     # ordre dans le menu (petit = plus haut)
icon = "🛡️"     # emoji affiché sur la carte d'accueil
+++
```

## Changer l'apparence

Tout est dans `hugo.toml` :

- `title` : le nom affiché (logo + onglets).
- `[params.theme].palette` : la palette. Essaie `tokyo-night-dark`, `dracula`,
  `gruvbox-dark`, `tender`, `material`... ou garde `catppuccin-mocha`. Liste complète dans
  `static/css/palettes/` et `themes/risotto/static/css/palettes/`.
- `[params.about]` : logo (emoji), titre et description de la barre latérale.
- `[[params.socialLinks]]` : les liens en bas de la barre latérale (icônes
  Font Awesome 6).

Les couleurs de toute l'interface (cartes, arbre, badges, code) dérivent de la
palette : changer de palette suffit à changer tout le site. Pour aller plus
loin, `static/css/custom.css` est à toi.

## Publier sur GitHub Pages

1. Crée un dépôt **public** sur GitHub et pousse ce dossier dedans :

   ```bash
   git init -b main
   git add .
   git commit -m "Initial commit"
   git remote add origin https://github.com/<utilisateur>/<nom-du-repo>.git
   git push -u origin main
   ```

2. Sur GitHub : **Settings > Pages > Build and deployment > Source = GitHub Actions**.

3. C'est tout. À chaque `push` sur `main`, le workflow
   `.github/workflows/hugo.yml` build le site et le publie. L'URL finale
   s'affiche dans l'onglet **Actions** (et dans Settings > Pages).

Le workflow règle l'URL de base automatiquement : pas besoin de toucher à
`baseURL` dans `hugo.toml`, même si le site est servi dans un sous-dossier
(`/<nom-du-repo>/`).

## Travailler à deux

- Ajoute ton pote en **collaborateur** : Settings > Collaborators.
- Pour rester au propre, chacun peut bosser sur une branche et ouvrir une pull
  request, ou pousser directement sur `main` pour les petits ajouts. Chaque
  push publie automatiquement.

## Renommer le projet

`grimoire` n'est qu'un nom par défaut. Pour le changer :

- `title` dans `hugo.toml`,
- `[params.about].title`,
- le nom du dépôt GitHub (l'URL Pages suit).

## Crédits

- Thème [risotto](https://github.com/joeroe/risotto) de Joe Roe (licence MIT,
  voir `themes/risotto/LICENSE`).
- Généré avec [Hugo](https://gohugo.io/).

## Licence

Le code du site est sous licence MIT (voir `LICENSE`). Les fiches et textes de
`content/` sont sous licence [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)
sauf mention contraire.
