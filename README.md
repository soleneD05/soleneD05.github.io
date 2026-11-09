# soleneD05.github.io

Mon CV interactif : **[soleneD05.github.io](https://soleneD05.github.io)**

Je suis AI Engineer et Data Scientist NLP. Plutôt que de décrire ce que je sais faire, ce site applique à mon propre CV les méthodes que j'utilise au quotidien sur des documents médicaux : NER, API, pipeline de traitement et recherche d'information.

## Les quatre vues

| Vue | Pour qui | Ce qu'elle montre |
|---|---|---|
| [Annotation](https://soleneD05.github.io/#annotation) | Tout le monde | Mon parcours en texte brut, annoté en entités nommées comme dans Label Studio (poste, organisation, date, outil, méthode, diplôme, savoir-être), filtrable par label |
| [API](https://soleneD05.github.io/#api) | Recruteurs tech | Le même contenu présenté comme une doc OpenAPI / FastAPI : endpoints testables, curl et réponses JSON |
| [Vidéo](https://soleneD05.github.io/#video) | Aperçu rapide | Une animation de 36 s : mon CV passe dans mon propre pipeline (OCR, classification, NER, résumé, JSON) |
| [Questions](https://soleneD05.github.io/#questions) | RH et tech | Un « Demandez à Solène » qui retrouve la réponse dans mon parcours, avec un score BM25 |

## Choix techniques

- **Un seul fichier `index.html`**, en HTML, CSS et JavaScript natifs, sans framework ni étape de build. Le site se charge vite et s'héberge gratuitement sur GitHub Pages.
- **Une seule source de vérité.** Le texte du CV est écrit avec un balisage d'annotation (`[FastAPI|TECH]`). L'onglet Annotation, les endpoints `/skills` et `/entities` et les compteurs sont tous calculés à partir de ce texte.
- **Une recherche d'information locale.** L'onglet Questions découpe mon parcours en passages, tokenise la question (minuscules, sans accents ni mots vides, racinisation légère) et classe les passages avec BM25. Tout tourne dans le navigateur : aucune donnée n'est envoyée à un serveur et aucune clé d'API n'est exposée. C'est la partie *retrieval* d'un RAG, sans génération par LLM.
- **Accessible et responsive** : thème clair et sombre, navigation au clavier (touches 1 à 7 pour filtrer les labels), respect de `prefers-reduced-motion`, affichage adapté au mobile.
- **Des données fictives pour les démos.** Les scores de confiance et de classification sont illustratifs.

## Lancer en local

```bash
git clone https://github.com/soleneD05/soleneD05.github.io.git
cd soleneD05.github.io
python3 -m http.server 8000
# puis ouvrir http://localhost:8000
```

## Structure

```
index.html                 le site complet
cv-solene-degrutere.pdf    le CV au format classique, pour les ATS
README.md
```

## Pistes d'évolution

- Brancher un vrai RAG génératif (embeddings, puis un LLM Mistral derrière un endpoint FastAPI sur Hugging Face Spaces).
- Remplacer l'annotation statique par l'inférence d'un modèle GLiNER.

## Contact

- Email : solene.degrutere@orange.fr
- LinkedIn : [solene-degrutere](https://www.linkedin.com/in/solene-degrutere)
- GitHub : [soleneD05](https://github.com/soleneD05)
