# chauffageromand.ch

Site statique. Aucune dépendance, aucun serveur applicatif, aucune base de données.

## Contenu

```
index.html                                 accueil
simulateur/                                simulateur en 8 questions
loi-energie-vaud/                          pilier d'autorité
prix/pompe-a-chaleur-villa/                page de conversion principale
demarches/chaudiere-en-panne/              page urgence, saison froide
subventions/programme-batiments-vaud/      page aides
qui-sommes-nous/                           modèle économique, transparence
confidentialite/                           protection des données
404.html                                   page introuvable
assets/style.css                           feuille de style commune
sitemap.xml, robots.txt, _headers          fichiers techniques
```

## Mettre en ligne, gratuitement

1. Créer un dépôt sur GitHub et y pousser ce dossier.
2. Sur Cloudflare Pages, connecter le dépôt. Aucune commande de build, dossier racine `/`.
3. Ajouter le domaine `chauffageromand.ch` dans les réglages du projet, puis suivre les instructions de délégation DNS.
4. Le fichier `_headers` est appliqué automatiquement par Cloudflare Pages. Sur Netlify, il fonctionne aussi ; sur un autre hébergeur, il est ignoré sans dommage.

## Brancher le formulaire

Dans `simulateur/index.html`, en haut du script :

```js
var FORM_ENDPOINT = "";
```

Tant que la valeur est vide, l'envoi affiche l'écran de confirmation et écrit le contenu de la demande dans la console du navigateur. Utile pour vérifier ce que recevra l'installateur.

Pour activer l'envoi réel : créer un compte gratuit sur Web3Forms, obtenir une clé, et remplacer par `https://api.web3forms.com/submit`, puis ajouter `access_key` dans l'objet `payload`. Toute autre solution acceptant un POST JSON convient également.

## Avant la première publication

- [ ] Vérifier la date d'entrée en vigueur de la loi et les échéances auprès de la Direction générale de l'environnement du canton de Vaud.
- [ ] Vérifier les montants d'aide sur le site officiel du Programme Bâtiments.
- [ ] Préciser, dans `loi-energie-vaud/`, le seuil de surface et l'échéance concernant les bâtiments classés F et G, laissés volontairement approximatifs.
- [ ] Créer l'adresse `contact@chauffageromand.ch`, citée sur quatre pages.
- [ ] Remplacer la mention d'hébergement dans `confidentialite/` par le prestataire réellement retenu.
- [ ] Déclarer le site dans Google Search Console et y soumettre `sitemap.xml`.

## Modifier le contenu

Chaque page est un fichier HTML autonome, éditable directement. La structure d'une page de contenu :

- `<div class="direct">` : la réponse immédiate, en haut. C'est ce que Google extrait.
- `<h2 id="...">` : les sections, reprises dans le sommaire latéral `<aside class="side">`.
- `<div class="note">` : encadré d'avertissement.
- `<div class="cta">` : appel vers le simulateur. Deux par page longue, pas davantage.
- `<details>` : questions fréquentes, à tenir synchronisées avec le bloc `FAQPage` en bas de page.

Si le JSON-LD et les questions visibles divergent, Google peut ignorer le balisage. Modifier les deux ensemble.

## Ajouter une page

Reprendre `subventions/programme-batiments-vaud/index.html` comme gabarit, remplacer le contenu de `<article>`, le sommaire, le titre, la description et le JSON-LD, puis ajouter l'adresse dans `sitemap.xml` et un lien depuis au moins deux pages existantes.
