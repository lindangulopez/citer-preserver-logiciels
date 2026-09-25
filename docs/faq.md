# Questions fréquentes

Les questions posées le plus souvent avant et après le webinaire « Citer et préserver des codes et logiciels avec SWHID et CodeMeta ». Les réponses sur Software Heritage renvoient au cours de Roberto Di Cosmo, *The Source Code of Science* (voir [Sources](#sources)).

- [Avant la session](#avant-la-session)
- [Archiver avec Software Heritage](#archiver)
- [Décrire et citer](#decrire-et-citer)
- [Après la session](#apres-la-session)

<a id="avant-la-session"></a>

## Avant la session

<a id="compte-github"></a>

### Faut-il un compte GitHub pour suivre le webinaire ?

Non. On peut suivre la démonstration sans aucun compte.

Pour refaire le parcours sur sa machine, il faut un compte sur une forge git. **Forker ce dépôt demande un compte GitHub**, car le dépôt de référence est sur GitHub.

<a id="fork-sans-compte"></a>

### Peut-on forker un dépôt sur une instance GitLab sans y avoir de compte ?

**Non, pas un vrai fork.** Sur GitLab, un fork est une copie du projet rangée dans l'espace de noms d'un utilisateur ou d'un groupe **sur la même instance**. Il faut donc un compte sur cette instance. Beaucoup d'instances permettent de se connecter via GitHub ou ORCID, mais cela crée quand même un compte local.

Pour forker, il faut :

1. un compte sur l'instance ;
2. pouvoir voir le projet : un projet public est visible par tout utilisateur connecté, un projet interne uniquement par les utilisateurs connectés de cette instance, un projet privé exige un rôle donnant accès au code ;
3. que le fork soit activé, car les administrateurs ou les propriétaires du projet peuvent le désactiver ;
4. que les inscriptions soient ouvertes : beaucoup d'instances institutionnelles sont fermées aux personnes extérieures.

Sans compte, on peut quand même :

- **cloner et héberger la copie ailleurs** : pour un projet public, `git clone` fonctionne sans connexion, puis on pousse vers une autre forge. On obtient sa propre copie, mais GitLab ne la reconnaît pas comme un fork, et on ne peut pas ouvrir de merge request vers l'original ;

  ```bash
  git clone https://gitlab.inria.fr/<espace-de-noms>/<projet>.git
  cd <projet>
  git remote set-url origin <url-de-votre-nouveau-depot>
  git push -u origin main
  ```

- **envoyer des patchs** par courriel (`git format-patch`) ou via une issue, si le projet accepte ce type de contribution ;
- **mettre en place un miroir** sur une autre instance, qui tire régulièrement depuis le dépôt public.

Il n'existe pas de fédération entre instances GitLab : on ne peut pas forker d'une instance vers une autre. La fédération des forges (ForgeFed) est en discussion, mais elle n'est pas disponible.

**Pour ce dépôt** : sans compte Inria, le [miroir gitlab.inria.fr](miroir-gitlab.md) peut être cloné, mais pas forké. Forkez plutôt la version GitHub.

<a id="qgis"></a>

### Faut-il installer QGIS ?

Seulement pour refaire le parcours complet sur sa machine. La version à utiliser est indiquée dans [`data/README.md`](../data/README.md). Pour suivre la démonstration, rien à installer.

<a id="archiver"></a>

## Archiver avec Software Heritage

<a id="depot-prive"></a>

### Mon dépôt est privé : puis-je l'archiver ?

Non. Un dépôt privé ne peut pas être archivé tant qu'il n'est pas rendu public (ch. 5.1).

<a id="sans-forge"></a>

### Mon code n'est pas sur une forge (fichier .zip ou .tar.gz) : que faire ?

Deux possibilités, sans identifiants particuliers (ch. 5.1) :

- **Le plus simple : Zenodo.** Un logiciel déposé sur Zenodo est transmis automatiquement à Software Heritage, à condition que les fichiers soient publics. La page Zenodo affiche alors le DOI et le SWHID.
- **Save code now** accepte aussi une archive `.zip` ou `.tar.gz`, depuis un compte gratuit. Le dépôt passe par une file de modération avant d'être archivé, ce qui peut prendre du temps.

<a id="delai"></a>

### Combien de temps prend l'archivage ?

L'archivage est asynchrone : la demande est enregistrée tout de suite, la visite du dépôt se fait ensuite. Un statut « pending » ou « partial » demande surtout du temps, en particulier pour un long historique. **Revérifiez plutôt que de soumettre à nouveau** (ch. 5.1).

Pour ne plus y penser, on peut archiver automatiquement chaque nouvelle version avec un webhook de publication (GitHub, GitLab, Gitea, Bitbucket, SourceForge).

<a id="miroir"></a>

### Si j'archive le dépôt GitHub, faut-il aussi archiver le miroir GitLab ?

Non. Le contenu est identique, donc le SWHID est le même. Archivez l'URL canonique, ici l'URL GitHub (voir [Miroir GitLab, §5](miroir-gitlab.md#software-heritage)).

<a id="decrire-et-citer"></a>

## Décrire et citer

<a id="doi-swhid"></a>

### DOI ou SWHID ?

Les deux, car ils ne répondent pas à la même question (ch. 4 et 5.1) :

- le **DOI** sert à trouver l'objet et à le citer dans une bibliographie ;
- le **SWHID** identifie le code exact et permet de vérifier qu'il n'a pas changé. Il est normalisé (ISO/IEC 18670).

<a id="codemeta-cff"></a>

### `codemeta.json` ou `CITATION.cff` ?

Les deux. `codemeta.json` décrit le logiciel (auteurs, licence, dépendances, dépôt). `CITATION.cff` indique comment le citer. Mettez-les à jour à chaque nouvelle version, pour que les citations restent justes (ch. 5.1 et 5.3-5.4).

<a id="workflow"></a>

### Pourquoi le workflow n'écrase-t-il pas `codemeta.json` ?

C'est un choix de conception. Le fichier `codemeta.json` à la racine est l'exemple corrigé à la main. Le workflow [`generate-codemeta.yml`](https://github.com/lindangulopez/citer-preserver-logiciels/blob/main/.github/workflows/generate-codemeta.yml) produit un fichier séparé, `codemeta.generated.json`, et affiche la différence entre les deux. On voit ainsi ce que l'outil trouve seul, et ce qu'il faut corriger.

<a id="hal"></a>

### Et HAL ?

HAL est un exemple parmi d'autres, pertinent dans le contexte français. Il dépose le code chez Software Heritage par le canal de dépôt réservé aux partenaires, auquel un chercheur n'a pas besoin d'accéder directement (ch. 5.1).

<a id="apres-la-session"></a>

## Après la session

<a id="questions"></a>

### Où poser mes questions ?

Pour toute question sur la formation ou sur l'archivage de vos logiciels dans Software Heritage : **helpdesk@softwareheritage.org**.

Pour refaire le parcours seul·e, commencez par [la check-list](getting-started.md).

<a id="sources"></a>

## Sources

Roberto Di Cosmo, *The Source Code of Science: Archiving, Referencing and Reproducing Research Software*, v1.6, septembre 2026, CC-BY-4.0. Dernière version : <https://hal.science/hal-05734828>. Chapitres cités : 4 (identifiants), 5.1 (archiver), 5.3-5.4 (décrire, citer).
