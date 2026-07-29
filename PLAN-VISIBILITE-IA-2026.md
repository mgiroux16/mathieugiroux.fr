# Plan de visibilité dans la recherche IA : mathieugiroux.fr

**Date :** 28 juillet 2026
**Base :** guide officiel Google du 16 mai 2026 (mis à jour 21 mai) + audit du dépôt `site/`

---

## 0. Trois corrections avant tout

**L'article que tu as lu est déjà dépassé sur son point central.** Il annonce les Aperçus IA en France « avant le 23 septembre 2026 ». En réalité Google les a déployés, avec le Mode IA, le **21-22 juillet 2026**. C'est en cours depuis une semaine. Fait vérifié.

**Google a publié un guide officiel qui contredit une partie du contenu GEO qui circule.** Le 16 mai 2026, Google a documenté pour la première fois comment optimiser pour les Aperçus IA et le Mode IA. Sa position est explicite : *« optimiser la recherche par IA générative revient à optimiser l'expérience de recherche, et donc le SEO »*. Il n'y a pas de discipline séparée. Fait vérifié, source primaire.

**Les chiffres de l'article, je ne les ai pas validés.** Les 93 % de sessions sans clic (Semrush), les 58,5 % de zéro-clic (SparkToro/Datos), la chute de 60 % du trafic des petits éditeurs (Chartbeat), la bascule du top 10 de 76 % à 38 % des citations : ces données circulent mais je ne suis pas remonté aux études sources. Traite-les comme une tendance directionnelle, pas comme des mesures fiables. La direction est solide, l'ampleur est incertaine.

---

## 1. Ce qui décide réellement d'une citation

Google décrit deux mécanismes, et ils dictent toute la stratégie.

**Le RAG (ancrage).** Avant de répondre, le modèle va chercher des pages dans l'index Google classique, en extrait des passages, puis affiche les liens. Conséquence : si une page n'est pas indexée et éligible à un extrait, elle n'existe pas pour l'IA. Le socle technique n'a pas changé.

**Le query fan-out.** Le modèle ne traite pas ta requête, il en génère une constellation. « Comment débuter avec l'IA » devient en parallèle « quelle IA gratuite choisir », « erreurs de débutant avec ChatGPT », « l'IA peut-elle se tromper », « combien coûte ChatGPT ». Conséquence : **une page qui couvre un sujet sous toutes ses facettes a plusieurs points d'entrée dans la réponse. Une page qui vise un mot-clé unique en a un seul.**

Le levier le plus lourd selon Google, à long terme, est le contenu non générique : *« un avis d'expert ou de personnes expérimentées qui transcende l'ordinaire »*, par opposition au « sept conseils aux primo-accédants ».

C'est exactement ton positionnement. Le « je raconte ce que les gens vivent avec l'IA, pas ce que les experts en disent » est littéralement ce que Google décrit comme le facteur numéro un. L'angle est bon. Le problème est ailleurs : dans l'exécution technique et dans la couverture.

---

## 2. Ce que Google dit de ne PAS faire

Cette liste vaut de l'argent, elle t'évite de perdre du temps.

| Fausse bonne idée | Verdict Google |
|---|---|
| `llms.txt` et fichiers « spéciaux » pour IA | Inutile pour Google Search. Aucun traitement particulier. |
| Découper le contenu en petits blocs pour l'IA | Inutile. Pas de longueur idéale. |
| Réécrire son style « pour l'IA » | Inutile. Les modèles comprennent les synonymes. |
| Multiplier les pages pour chaque variante de requête | Contraire aux règles anti-spam (contenu à grande échelle). |
| Gonfler artificiellement les mentions de marque | Filtré par les systèmes anti-spam. |
| Sur-investir dans les données structurées | Non requis pour l'IA générative. Reste utile pour les résultats enrichis classiques. |

**Ce que ça veut dire pour toi :** ton `llms.txt` et `llms-full.txt` ne servent à rien pour Google. Ils ont un effet modeste et non prouvé sur Perplexity et Claude. Ne les supprime pas, mais n'y investis plus une minute. Actuellement `llms.txt` dit « Livre 1 disponible, livres 2 à 6 à venir » alors que ton schema en déclare trois publiés : cette contradiction est plus nuisible que le fichier n'est utile.

---

## 3. Audit : ce qui va, ce qui bloque

### Ce qui est déjà bien

- Schema `Article` + `FAQPage` sur les 8 articles du blog, correctement formé
- Auteur nommé et visible sur chaque page (« Par Mathieu Giroux, conseiller numérique »)
- Structure Hn propre, réponse donnée tôt dans chaque section
- Sections « Questions fréquentes » : exactement le format extractible que le RAG aime
- 10 à 12 liens internes par page
- `robots.txt` ouvert aux crawlers IA (GPTBot, ClaudeBot, PerplexityBot, Google-Extended)
- HTML statique, pas de JavaScript à rendre : idéal pour l'exploration

### Les 8 blocages, par ordre d'impact

**1. Tu ne mesures rien. C'est le vrai problème.**
Aucune balise de vérification Search Console, aucun Umami, aucun analytics détecté dans le HTML. La Search Console intègre désormais les clics venus des Aperçus IA et du Mode IA dans le rapport Performances (type de recherche « Web »). Sans elle, tu pilotes à l'aveugle et tu ne sauras jamais si quoi que ce soit dans ce plan fonctionne.

**2. `robots.txt` ne déclare pas le sitemap.**
Une ligne manquante. Coût : zéro. Effet : découverte plus rapide.

**3. La page comparatif est datée 2025.**
`chatgpt-claude-gemini-quelle-ia-choisir.html` : titre H2 « Comparatif ChatGPT vs Claude vs Gemini (2025) », 8 occurrences de 2025, `lastmod` sitemap au **2025-06-09**. Or les articles comparatifs sont, selon les données disponibles, le type de contenu le plus cité par les IA, et les moteurs génératifs ont un biais de fraîcheur marqué. C'est ta page à plus fort potentiel et c'est la plus périmée du site.

**4. Aucune page « À propos ».**
Pas de page auteur, donc pas d'entité consolidée. Pour un site dont l'argument unique est l'expérience de terrain d'une personne nommée, c'est l'angle mort principal. Google insiste sur l'identification de l'auteur et de ses qualifications.

**5. Aucun `sameAs` nulle part.**
Rien ne relie « Mathieu Giroux » du site à ton profil LinkedIn, ta page auteur Amazon, ton compte X. Les modèles n'ont aucun moyen de savoir qu'il s'agit de la même personne.

**6. Le schema `Person` est incomplet et l'email est incohérent.**
`iapourtousmg@gmail.com` dans le schema, `contact@mathieugiroux.fr` dans `llms.txt`. Pas de `sameAs`, pas de `knowsAbout`, pas d'`image`.

**7. La page d'accueil ne répond à aucune question.**
Son H1 est « Comprendre et utiliser l'IA, sans coder, sans jargon. » C'est une accroche de marque. Elle ne sera jamais citée dans une réponse générée, parce qu'elle ne répond à rien. Ce n'est pas grave en soi, mais ça veut dire que toute ta visibilité IA repose sur 8 articles de blog.

**8. `netlify.toml` traîne dans le dépôt.**
Contraire à ta propre règle projet (GitHub Pages uniquement). À supprimer avant qu'il ne serve à quelqu'un.

---

## 4. Plan d'action

### Semaine 1 : le socle mesurable (2 heures, impact maximal)

**Search Console.** Valide `mathieugiroux.fr` (propriété de domaine via DNS OVH, ou balise HTML dans `index.html`). Soumets `sitemap.xml`. Sans ça, rien d'autre n'est mesurable.

**Une ligne dans `robots.txt` :**
```
Sitemap: https://mathieugiroux.fr/sitemap.xml
```

**Analytics.** Ton Umami est déjà self-hosted sur Hetzner d'après ta doc projet, mais le script n'est dans aucune page. Ajoute-le, ou bascule sur autre chose. Sans mesure de trafic entrant, tu ne pourras pas isoler ce que les surfaces IA t'apportent.

**Supprime `netlify.toml`.**

### Semaine 2 : l'identité d'auteur (3 heures)

**Crée `/a-propos.html`.** Pas une page de vanité : la page qui prouve l'expérience. Qui tu accompagnes, depuis quand, combien de personnes, ce que tu as observé que personne d'autre n'a observé, tes livres. C'est le signal E-E-A-T le plus direct, et Google le nomme explicitement.

**Corrige et enrichis le schema `Person` sur `index.html`** (à répliquer sur `/a-propos.html`) :

```json
{
  "@type": "Person",
  "@id": "https://mathieugiroux.fr/#mathieu-giroux",
  "name": "Mathieu Giroux",
  "url": "https://mathieugiroux.fr/a-propos.html",
  "jobTitle": "Conseiller numérique",
  "description": "Conseiller numérique en Charente. Accompagne des personnes non techniciennes dans l'usage quotidien de l'intelligence artificielle. Auteur de la série IA pour Tous.",
  "email": "contact@mathieugiroux.fr",
  "knowsAbout": ["Intelligence artificielle générative", "ChatGPT", "Claude", "Gemini", "Prompt engineering", "Inclusion numérique"],
  "sameAs": [
    "https://www.linkedin.com/in/TON-PROFIL",
    "https://www.amazon.fr/stores/author/TON-ID",
    "https://x.com/TON-COMPTE"
  ]
}
```

Puis, dans chaque article, remplace `"author": {"@type": "Person", "name": "Mathieu Giroux"}` par une référence à cette entité :
```json
"author": { "@id": "https://mathieugiroux.fr/#mathieu-giroux" }
```

**Vérifie l'email** partout : un seul, `contact@mathieugiroux.fr`, dans le schema, `llms.txt` et `llms-full.txt`.

**Mets `llms.txt` à jour** (3 livres publiés, pas 1). Cinq minutes, juste pour ne pas raconter deux versions différentes.

### Semaine 3-4 : refaire la page comparatif (une demi-journée)

C'est l'action à plus fort rendement du plan. Le comparatif est le format le plus cité, et il est périmé.

- Titre et H2 en 2026, pas 2025
- Tarifs et limites gratuites actualisés pour ChatGPT, Claude et Gemini
- Un vrai tableau comparatif HTML (`<table>`), pas des paragraphes : les tableaux sont ce que le RAG extrait le plus proprement pour les comparaisons
- Ajoute les facettes manquantes que le query fan-out va générer : **le prix**, les **alternatives** (Mistral, Copilot, Perplexity : un français cherchera Le Chat), la **confidentialité des données**, l'**usage mobile**, les **cas où aucune des trois ne convient**
- Ajoute `"dateModified"` à jour dans le schema et corrige le `lastmod` du sitemap (2025-06-09 → date réelle)
- Garde ton angle : sur chaque comparaison, dis ce que tu as vu chez les gens que tu accompagnes. C'est ce qu'aucun modèle ne peut générer seul, et c'est précisément ce que Google décrit comme non générique.

Ajoute aussi le schema `dateModified` réel partout ailleurs : plusieurs de tes articles ont `datePublished` = `dateModified`, donc ils vieillissent sans jamais rajeunir.

### Mois 2 : la couverture par facettes (le vrai chantier)

Le réflexe naturel serait d'écrire 20 articles courts. **C'est exactement ce que Google sanctionne** au titre de l'utilisation abusive de contenu à grande échelle. La bonne approche est l'inverse : approfondir les pages existantes jusqu'à ce que chacune couvre toutes les facettes de son sujet.

Méthode, article par article. Pour chaque page, liste les sous-requêtes qu'un modèle générerait à partir du sujet, puis vérifie que la page y répond :

| Facette | Question type | Présente ? |
|---|---|---|
| Coût | « c'est gratuit ? » | souvent absente |
| Erreurs fréquentes | « pourquoi ça ne marche pas » | partiellement |
| Alternatives | « et sinon quoi d'autre » | absente |
| Risques / confidentialité | « est-ce que c'est sûr » | présente sur le PDF, absente ailleurs |
| Cas où ça ne marche pas | « quand ne pas utiliser l'IA » | absente partout |
| Public spécifique | « pour un senior », « pour un indépendant » | absente |

Les sections FAQ que tu as déjà sont le bon véhicule : passe de 3-4 questions à 8-10, en couvrant ces facettes. Ça n'ajoute aucune page, ça multiplie les points d'entrée, et ça reste utile au lecteur humain.

**Deux ou trois pages nouvelles maximum, sur des sujets réellement distincts et pour lesquels tu as du terrain.** Suggestions cohérentes avec ton positionnement et avec des formats fortement cités :

1. « Combien coûte vraiment l'IA en 2026 : gratuit, payant, ce qui change » (comparatif = format le plus cité)
2. « Les erreurs que je vois le plus souvent chez les débutants » (expérience directe, non copiable, impossible à générer)
3. « Quand l'IA n'est pas la bonne réponse » (contrarian, ton angle, aucune concurrence)

### En continu : mesurer, pas supposer

Une fois la Search Console en place, regarde tous les mois :

- **Impressions vs clics par page.** Si les impressions montent et les clics stagnent, tu es cité sans être visité. C'est la bascule décrite dans l'article, et c'est mesurable chez toi.
- **Fais le test manuel** que l'article suggère, sur 5 requêtes qui comptent : *« quelle IA choisir pour débuter »*, *« comment résumer un PDF avec l'IA »*, *« écrire un CV avec l'IA »*, *« comment bien écrire un prompt »*, *« l'IA pour les débutants »*. Note si un Aperçu IA s'affiche, et s'il te cite. Refais-le chaque mois. C'est du travail manuel, c'est la seule donnée qui compte, et ça prend dix minutes.

---

## 5. Le point que l'article a raison de soulever, et sa limite pour toi

L'auteur a raison sur un point : être cité sans être cliqué est un scénario réel, et le classement ne garantit plus la citation.

Mais sa conclusion ne s'applique pas mécaniquement à ton cas. Un média vit du trafic publicitaire : chaque clic perdu est une perte sèche. Toi, tu vends des livres et tu construis une liste email. Une citation dans un Aperçu IA avec ton nom, en tant que conseiller numérique auteur d'une série de livres, a une valeur en soi, même sans clic. Elle construit l'association « IA pour les débutants → Mathieu Giroux » dans les modèles eux-mêmes.

Ce qui veut dire que ton indicateur n'est pas le trafic. C'est : **est-ce que je suis nommé quand quelqu'un demande à une IA par quoi commencer pour apprendre l'IA ?** Et ça, ça se teste directement en posant la question à ChatGPT, Claude, Gemini et Perplexity. Fais-le aujourd'hui pour avoir un point de départ.

---

## Contre-analyse

**L'objection principale :** ce plan repose lourdement sur le guide Google de mai 2026, qui est une source intéressée. Google a un intérêt évident à dire « faites du SEO classique, rien ne change », parce que l'inverse reviendrait à admettre qu'il a cassé le contrat implicite avec les éditeurs. Les données terrain des éditeurs racontent une autre histoire que le discours officiel, et Google conteste ces données sans en fournir de contradictoires.

**L'angle mort :** tout ce plan optimise pour Google. Or une part croissante des recherches « par quelle IA commencer » se fait directement dans ChatGPT, Claude ou Perplexity, qui ne fonctionnent pas comme la recherche Google, ne publient pas de guide, et pondèrent probablement plus les mentions tierces (forums, Reddit, avis Amazon, citations sur d'autres sites) que le contenu on-site. Pour ces surfaces, ton meilleur levier n'est pas ton site : ce sont tes avis Amazon, tes posts LinkedIn, et le fait d'être mentionné ailleurs que chez toi.

**Une seule justification faible :** l'affirmation « les comparatifs sont le format le plus cité » vient d'agrégats d'agences SEO, pas d'une étude que j'ai pu vérifier à la source. Elle est cohérente avec le fonctionnement du query fan-out, mais je la donne comme inférence plausible, pas comme fait établi.
