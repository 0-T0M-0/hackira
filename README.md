# hackira

> Veille technique : informatique, cybersécurité, IA. Repos, outils et ressources, rangés.

![Hugo](https://img.shields.io/badge/Hugo-extended-000?logo=hugo&logoColor=fff)
![Licence](https://img.shields.io/badge/licence-MIT-blue)

Lien : [hackira](https://0-t0m-0.github.io/hackira/)

Base de connaissances collaborative, générée en statique avec [Hugo](https://gohugo.io/)
et le thème [risotto](https://github.com/joeroe/risotto). Le contenu est écrit en
Markdown et la navigation se construit à partir de l'arborescence de `content/`.
https://0-t0m-0.github.io/hackira/
## Développement

Prérequis : [Hugo extended](https://gohugo.io/installation/) (0.128 ou plus récent).

```bash
hugo server        # http://localhost:1313
```

## Ajouter une ressource

```bash
hugo new cyber/ma-fiche.md
```

Une fiche est un fichier Markdown. Un dossier contenant un `_index.md` devient une
section, ajoutée automatiquement au menu.

## Déploiement

Hébergé sur GitHub Pages via GitHub Actions. Après le premier push sur `main`,
activer **Settings > Pages > Source : GitHub Actions**. Chaque push publie le site.

## Licence

[MIT](LICENSE).
