# Miroiter ce dépôt GitHub vers GitLab (Inria)

Ce tutoriel explique comment copier ce dépôt vers une forge GitLab, ici [gitlab.inria.fr](https://gitlab.inria.fr), et comment garder les deux copies synchronisées.

Un « fork » n'existe qu'à l'intérieur d'une même plateforme : on ne peut pas forker GitHub vers GitLab. Deux approches existent :

- **l'import** : une copie faite une fois ;
- **le miroir** : une copie que l'on met à jour.

Ce parcours combine les deux : on importe une première fois, puis on pousse les mises à jour depuis sa machine.

> **Convention.** Le dépôt GitHub reste le dépôt de référence (URL canonique, GitHub Actions, GitHub Pages). La copie GitLab est un miroir secondaire.

Durée : environ 20 minutes. Prérequis : un compte GitHub, un compte sur gitlab.inria.fr, `git` installé.

## 1. Préparer le dépôt GitHub

- Vérifiez que la branche `main` est à jour et que les workflows GitHub Actions sont au vert.
- Cherchez d'éventuels secrets dans l'historique, car un miroir copie tout l'historique :

  ```bash
  git log -p | grep -i -E "token|secret|password"
  ```

- Décidez de la visibilité de la copie GitLab (publique, interne ou privée).

## 2. Créer le projet GitLab

### Option A : l'import GitLab (le plus simple)

1. Sur gitlab.inria.fr : **New project → Import project → GitHub**.
2. Sur GitHub, créez un jeton d'accès personnel (*classic*, portée `repo`) : <https://github.com/settings/tokens>. Collez-le dans GitLab.
3. Choisissez `lindangulopez/citer-preserver-logiciels`, puis votre espace de noms (personnel ou groupe d'équipe) et gardez le même nom de projet.
4. Cliquez sur **Import**, puis **révoquez le jeton** sur GitHub une fois l'import terminé.

### Option B : la copie manuelle

À utiliser si l'import GitHub est désactivé sur l'instance.

1. Sur GitLab : **New project → Create blank project**. Décochez l'initialisation avec un README.
2. Dans un terminal :

   ```bash
   git clone --mirror https://github.com/lindangulopez/citer-preserver-logiciels.git
   cd citer-preserver-logiciels.git
   git push --mirror https://gitlab.inria.fr/<espace-de-noms>/citer-preserver-logiciels.git
   ```

   L'authentification se fait avec votre compte Inria, un jeton d'accès GitLab ou une clé SSH.

## 3. Garder les deux copies synchronisées

Dans votre clone de travail, ajoutez GitLab comme second dépôt distant :

```bash
git remote add gitlab git@gitlab.inria.fr:<espace-de-noms>/citer-preserver-logiciels.git
git push gitlab main --tags
```

Ensuite, après chaque `git push origin main`, lancez `git push gitlab main --tags`.

Pour tout pousser d'un coup, ajoutez une seconde adresse de push à `origin` :

```bash
git remote set-url --add --push origin git@gitlab.inria.fr:<espace-de-noms>/citer-preserver-logiciels.git
git remote set-url --add --push origin https://github.com/lindangulopez/citer-preserver-logiciels.git
```

Variante automatisée : une étape GitHub Actions qui pousse vers GitLab avec un jeton d'accès de projet GitLab stocké comme secret GitHub. Vérifiez au préalable que l'instance autorise les jetons de projet.

> **À éviter.** Ne commitez pas des deux côtés indépendamment : les historiques divergeraient.

## 4. Adapter le dépôt pour GitLab

- Les fichiers de `.github/workflows/` ne s'exécutent pas sur GitLab. Vous pouvez les ignorer, ou ajouter un `.gitlab-ci.yml` minimal qui refait la même vérification.
- Gardez l'URL GitHub comme adresse canonique dans `README.md`, `CITATION.cff` et `codemeta.json`. Ajoutez l'adresse GitLab comme miroir (par exemple dans `sameAs`) plutôt que de la substituer.
- Ajoutez une ligne dans le README de la copie GitLab :

  ```text
  Miroir de https://github.com/lindangulopez/citer-preserver-logiciels
  ```

## 5. Lien avec Software Heritage

Archivez l'URL GitHub canonique avec [Save code now](https://archive.softwareheritage.org/save/). N'archivez l'URL GitLab que si vous voulez une seconde origine : le contenu étant identique, le SWHID du dépôt sera le même.

## Vérifier

- `git ls-remote origin main` et `git ls-remote gitlab main` renvoient le même identifiant de commit.
- Les branches et étiquettes sont identiques des deux côtés.
- Sur GitLab, l'arborescence, l'historique et la licence s'affichent correctement.
- Un commit de test poussé sur `origin`, puis synchronisé, apparaît sur GitLab.

## Points à vérifier avant de commencer

- L'instance autorise-t-elle l'import GitHub et les jetons d'accès de projet ?
- Quel espace de noms (personnel ou équipe) doit porter le projet ? Cela détermine qui peut le voir et le maintenir.
