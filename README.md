# DSFR RTL

DSFR Right To Left (ci-après RTL) est une extension au Système de Design de l'État.

Il fournit l'ensemble des styles pour adapter le DSFR pour des langues qui s'écrivent de droite à gauche.

## Installation

L'installation de DSFR RTL peut se faire de différentes manières :
* en téléchargeant le fichier style de ce repository ;
* en utilisant le gestionnaire de paquets NPM.

### Fichiers statiques

Il est possible de télécharger les sources de ce repository au format .zip. Le fichier principal sera un fichier SCSS qui surchargera le style du DSFR pour l'adapter en RTL.

### NPM

DSFR RTL est également disponible via NPM. Pour cela, plusieurs prérequis :
* [NodeJS](https://nodejs.org/fr) doit être installé ;
* Un fichier `package.json` doit être présent à la racine du projet.

Installez ensuite le package DSFR RTL avec la commande `npm install @gouvfr/dsfr-rtl`.

## Importation du style

Lier la feuille de style au HTML :

```html
<link rel="stylesheet" href="./style/dsfr-rtl.css" />
```

## Sujets spécifiques à l'intégration HTML

* Les **textes non-traduits** dans un texte RTL peuvent avoir un comportement non désiré s'il y a des nombres ou des caractères spéciaux en début ou fin de phrase. Il est possible de résoudre cette problématique en encapsulant le texte non traduit par un `span` ayant la class "fr-text-plaintext" : `<span class="fr-text-plaintext">Texte non traduit</span>`.

Exemple sur le lien "Qu’est-ce que FranceConnect+". La mise en place de cette classe évitera que le "+" ne passe tout à gauche.

* Le sens des **icônes** doit être inversé lorsque celles-ci ont une direction relative à la navigation dans le site ou à la lecture. Certaines icônes ont été gérées directement dans le fichier SCSS de cette extension (la flèche d'une card par exemple).

Certaines icônes auront besoin d'un traitement manuel et spécifique, c'est pour cela que la class CSS existe `fr-icon-rtl`. Elle permettra d'opérer une symétrie verticale pour l'avoir dans le bon sens.

* Si les **numéros d’étapes** (Stepper) sont injectés dynamiquement via un Template, l’ordre des éléments change en RTL : 

    * en français : étape [current] sur [max]
    * en arabe : [max] sur [current] étape