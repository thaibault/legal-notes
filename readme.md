<!-- !/usr/bin/env markdown
-*- coding: utf-8 -*-
region header
Copyright Torben Sickert (info["~at~"]tsickert.com) 16.12.2012

License
-------

This library written by Torben Sickert stands under a creative commons naming
4.0 international license.
See https://creativecommons.org/licenses/by/4.0/deed.de
endregion -->


<!--|deDE:Projektstatus-->
<!--|frFR:État du projet-->
Project status
--------------

[![npm](https://img.shields.io/npm/v/legal-notes?color=%23d55e5d&label=npm%20package%20version&logoColor=%23d55e5d&style=for-the-badge)](https://www.npmjs.com/package/legal-notes)
[![npm downloads](https://img.shields.io/npm/dy/legal-notes.svg?style=for-the-badge)](https://www.npmjs.com/package/legal-notes)

[![build push package](https://img.shields.io/github/actions/workflow/status/thaibault/legal-notes/build-package-and-push.yaml?label=build%20push%20package&style=for-the-badge)](https://github.com/thaibault/legal-notes/actions/workflows/build-package-and-push.yaml)

<!--|deDE:Einsatzmöglichkeiten-->
<!--|frFR:Cas d'utilisation-->
Use case
--------

Legal-Notes is a reusable HTML snippet holding the legal disclaimer and
privacy statements of all my project websites. It is maintained once and
embedded into each documentation page and home page, so every site always
shows the same up to date legal text.
<!--deDE:
    Legal-Notes ist ein wiederverwendbares HTML-Snippet mit dem rechtlichen
    Haftungsausschluss und den Datenschutzhinweisen all meiner
    Projekt-Webseiten. Es wird an einer Stelle gepflegt und in jede
    Dokumentations- und Homepage eingebunden, sodass jede Seite stets
    denselben aktuellen Rechtstext zeigt.
-->
<!--frFR:
    Legal-Notes est un extrait HTML réutilisable contenant l'avertissement
    juridique et les déclarations de confidentialité de tous mes sites de
    projet. Il est maintenu à un seul endroit et intégré dans chaque page de
    documentation et page d'accueil, de sorte que chaque site affiche
    toujours le même texte juridique à jour.
-->

Sections included:
<!--deDE:Enthaltene Abschnitte:-->
<!--frFR:Sections incluses:-->

- Disclaimer: liability for content and links.<!--deDE:Haftungsausschluss: Haftung für Inhalte und Links.--><!--frFR:Désistement: responsabilité quant au contenu et aux liens.-->
- Copyright of content and artwork.<!--deDE:Urheberrecht an Inhalten und Grafiken.--><!--frFR:Droit d'auteur sur les contenus et les illustrations.-->
- Privacy policy including the content delivery network (Cloudflare) and a
  possible use of Google Analytics.<!--deDE:Datenschutzerklärung inklusive Content-Delivery-Network (Cloudflare) und einer möglichen Nutzung von Google Analytics.--><!--frFR:Politique de confidentialité, y compris le réseau de diffusion de contenu (Cloudflare) et une éventuelle utilisation de Google Analytics.-->

All texts are available in American English, German and French. The
translations are embedded as HTML comments and can be switched at runtime via
[web-internationalization](https://tsickert.com/web-internationalization).
<!--deDE:
    Alle Texte liegen in amerikanischem Englisch, Deutsch und Französisch vor.
    Die Übersetzungen sind als HTML-Kommentare eingebettet und lassen sich zur
    Laufzeit mittels
    [web-internationalization](https://tsickert.com/web-internationalization)
    umschalten.
-->
<!--frFR:
    Tous les textes sont disponibles en anglais américain, en allemand et en
    français. Les traductions sont intégrées sous forme de commentaires HTML
    et peuvent être changées à l'exécution grâce à
    [web-internationalization](https://tsickert.com/web-internationalization).
-->

<div class="wd-table-of-contents">
    <h2 id="content">Content<!--deDE:Inhalt--><!--frFR:Contenu--></h2>
    <!--wd-table-of-contents-->
</div>

Installation
------------

```bash
yarn add --dev legal-notes
```

The package ships two files:
<!--deDE:Das Paket liefert zwei Dateien aus:-->
<!--frFR:Le paquet fournit deux fichiers:-->

- "index.html": The readable source.<!--deDE:"index.html": Die lesbare Quelle.--><!--frFR:"index.html": La source lisible.-->
- "index.compiled.html": A minified version which keeps all translation
  comments. This is the package entry point.<!--deDE:"index.compiled.html": Eine minimierte Version, die alle Übersetzungskommentare behält. Dies ist der Einstiegspunkt des Pakets.--><!--frFR:"index.compiled.html": Une version minifiée qui conserve tous les commentaires de traduction. C'est le point d'entrée du paquet.-->

<!--|deDE:Verwendung-->
<!--|frFR:Utilisation-->
Usage
-----

<!--|deDE:In EJS-Vorlagen mit weboptimizer-->
<!--|frFR:Dans des modèles EJS avec weboptimizer-->
### In EJS templates with weboptimizer

[weboptimizer](https://tsickert.com/weboptimizer) resolves package names in
its EJS "include" function to the package entry point. That is how
[web-documentation](https://tsickert.com/web-documentation) and my home page
embed the notes:
<!--deDE:
    [weboptimizer](https://tsickert.com/weboptimizer) löst Paketnamen in
    seiner EJS-Funktion "include" zum Einstiegspunkt des Pakets auf. So binden
    [web-documentation](https://tsickert.com/web-documentation) und meine
    Homepage die Hinweise ein:
-->
<!--frFR:
    [weboptimizer](https://tsickert.com/weboptimizer) résout les noms de
    paquets de sa fonction EJS "include" vers le point d'entrée du paquet.
    C'est ainsi que
    [web-documentation](https://tsickert.com/web-documentation) et ma page
    d'accueil intègrent les mentions:
-->

```HTML
<section>
    <h2>About this website</h2>
    <%- await _.include('legal-notes') %>
</section>
```

<!--|deDE:In Node.js-->
<!--|frFR:Dans Node.js-->
### In Node.js

Resolve the entry point and read it as text:
<!--deDE:Lösen Sie den Einstiegspunkt auf und lesen Sie ihn als Text ein:-->
<!--frFR:Résolvez le point d'entrée et lisez-le comme texte:-->

```JavaScript
import {readFile} from 'fs/promises'

const legalNotes = await readFile(
    new URL(import.meta.resolve('legal-notes')), 'utf8'
)
```

<!--|deDE:Im Browser-->
<!--|frFR:Dans le navigateur-->
### In the browser

Load the snippet from a CDN and insert it into your page:
<!--deDE:
    Laden Sie das Snippet von einem CDN und fügen Sie es in Ihre Seite ein:
-->
<!--frFR:Chargez l'extrait depuis un CDN et insérez-le dans votre page:-->

```JavaScript
const response =
    await fetch('https://unpkg.com/legal-notes@latest/index.compiled.html')

document.querySelector('.legal-notes').innerHTML = await response.text()
```

<!--|deDE:Entwicklung-->
<!--|frFR:Développement-->
Development
-----------

Edit "index.html" and build the minified version via
[html-minifier](https://www.npmjs.com/package/html-minifier):
<!--deDE:
    Bearbeiten Sie "index.html" und erzeugen Sie die minimierte Version
    mittels [html-minifier](https://www.npmjs.com/package/html-minifier):
-->
<!--frFR:
    Modifiez "index.html" et générez la version minifiée via
    [html-minifier](https://www.npmjs.com/package/html-minifier):
-->

```bash
yarn install
yarn build # Writes "index.compiled.html".
yarn test  # Builds and prints the result.
yarn clear # Removes compiled files.
```

New package versions are published by manually running the "Build package
and push" GitHub workflow.
<!--deDE:
    Neue Paketversionen werden durch manuelles Starten des GitHub-Workflows
    "Build package and push" veröffentlicht.
-->
<!--frFR:
    Les nouvelles versions du paquet sont publiées en lançant manuellement le
    workflow GitHub "Build package and push".
-->
