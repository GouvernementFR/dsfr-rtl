# DSFR RTL

DSFR Right To Left (ci-après RTL) est une extension au Système de Design de l'État.

Il fournit l'ensemble des styles pour adapter le DSFR pour des langues qui s'écrivent de droite à gauche.

## Installation

L'installation de DSFR RTL peut se faire de différentes manières :
* en téléchargeant le fichier style de ce repository ;
* en utilisant le gestionnaire de paquets NPM.

### Fichiers statiques

Il est possible de télécharger les sources de ce repository au format .zip depuis [la page Release de Github](https://github.com/GouvernementFR/dsfr-rtl/releases). Le fichier compilé se trouve dans `dist/dsfr-rtl.css`, ou `dist/dsfr-rtl.min.css` pour la version minifiée. Vous trouverez aussi une version sass `src/dsfr-rtl.scss` paramètrable via des variables, permettant de paramétrer les classes utilitaires à générées.

### NPM

DSFR RTL est également disponible via NPM. Pour cela, plusieurs prérequis :
* [NodeJS](https://nodejs.org/fr) doit être installé ;
* Un fichier `package.json` doit être présent à la racine du projet.

Installez ensuite le package DSFR RTL avec la commande `npm install @gouvfr/dsfr-rtl`.

## Importation du style

Lier la feuille de style au HTML :

```html
<link rel="stylesheet" href="./style/dsfr-rtl.min.css" />
```

## Sujets spécifiques à l'intégration HTML

* Les **textes non-traduits** dans un texte RTL peuvent avoir un comportement non désiré s'il y a des nombres ou des caractères spéciaux en début ou fin de phrase. Il est possible de résoudre cette problématique en encapsulant le texte non traduit dans un `span` ayant la classe `fr-text-plaintext`.
Par exemple sur le lien "Qu’est-ce que FranceConnect+", la mise en place de cette classe évitera que le "+" ne passe tout à gauche : `<span class="fr-text-plaintext">FranceConnect+</span>`

* Le sens des **icônes** doit être inversé lorsque celles-ci ont une direction relative à la navigation dans le site ou à la lecture. Certaines icônes ont été gérées directement dans le fichier SCSS de cette extension (la flèche d'une card par exemple).
Certaines icônes auront besoin d'un traitement manuel et spécifique, c'est pour cela que la class CSS existe `fr-icon-rtl`. Elle permettra d'opérer une symétrie verticale pour inverser le sens de l'icône.

* Sur le composant indicateur d'étape (Stepper), si les **numéros d’étapes** sont injectés dynamiquement via un Template, l’ordre des éléments change en RTL :
    * en français : étape [current] sur [max]
    * en arabe : [max] sur [current] étape


## Points de vigilance

* Attention au **line-height**, l'écart entre les lignes est souvent plus faible en arabes car les caractères prennent plus de place en hauteur. De plus, les caractères pourraient être croppés si le line-height est trop faible.

* Eviter le **soulignement** des textes en arabes. De nombreux caractères arabes contiennent des signes diacritiques en bas qui pourrait être masqués par le soulignement.

* Vérifier le **retour à la ligne** des longs mots. Le DSFR utilise la propriété `overflow-wrap: break-word` pour forcer le passage à la ligne des mots plus grand que leur conteneur. En arabe cette propriété peut avoir un comportement non désiré car les lettres d'un mot sont indissociables.

* Certains **champs de formulaire** spécifiques ne doivent pas être inversés. Par exemple, les champs "email" ou "téléphone" doivent rester en LTR car leur contenu se lit de gauche à droite. Le placeholder doit cepedendant être placé sur la droite si ce texte est traduit dans une langue RTL.

## Contribution
Le processus de contribution est détaillé sur la page [CONTRIBUTING.md](https://github.com/GouvernementFR/dsfr-rtl/blob/dev/CONTRIBUTING.md).