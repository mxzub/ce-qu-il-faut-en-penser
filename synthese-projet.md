# Synthèse — Mes sujets de conv'

> Projet de site web personnel pour lister et partager les idées et histoires abordées en conversation.

---

## Objectif

Créer un site web simple, consultable sur mobile, qui liste les sujets de conversation récurrents. Chaque sujet présente :
- une description rapide
- l'opinion personnelle de l'auteur
- des liens vers des références
- des liens vers des sujets similaires

---

## Architecture retenue

Deux fichiers à placer dans le même dossier :

| Fichier | Rôle |
|---|---|
| `index.html` | Interface complète du site (HTML/CSS/JS) |
| `subjects.json` | Contenu des sujets (texte, tags, références) |

Le site est **entièrement statique** : aucun serveur, aucune base de données. `index.html` lit `subjects.json` et construit l'interface dynamiquement.

---

## Structure d'un sujet (JSON)

```json
{
  "id": 1,
  "title": "Titre du sujet",
  "short": "Une phrase résumé pour la liste",
  "tags": ["tag1", "tag2"],
  "description": "Explication développée du sujet...",
  "opinion": "Ce que j'en pense personnellement...",
  "refs": [
    { "label": "Nom du lien", "url": "https://..." }
  ],
  "related": [2, 3]
}
```

Le champ `related` contient les `id` des sujets liés — ils apparaissent en bas de la page détail.

---

## Fonctionnalités de l'interface

- **Liste des sujets** avec titre, résumé et tags
- **Filtre par tag** (barre cliquable en haut)
- **Vue détail** au clic sur un sujet (description, opinion, références, sujets similaires)
- **Navigation retour** vers la liste
- **Animations** d'entrée au chargement
- **Optimisé mobile** (responsive, typographie fluide)
- **Typographie** : Lora (titres) + DM Sans (corps)

---

## Options d'hébergement évaluées

| Solution | Facilité | Coût | Domaine custom |
|---|---|---|---|
| **Notion** | Très facile | Gratuit | Payant (10$/mois) |
| **Google Sites** | Très facile | Gratuit | Gratuit |
| GitHub Pages | Technique | Gratuit | Gratuit |
| Framer / Webflow | Intermédiaire | Limites plan gratuit | Payant |

**Recommandations retenues :** Notion (le plus rapide à mettre en place) ou Google Sites (le plus complet gratuitement).

---

## Workflow pour ajouter un sujet

1. Décrire le sujet à Claude en quelques phrases
2. Claude génère le bloc JSON correspondant
3. Coller le bloc dans `subjects.json` (via l'éditeur web de la plateforme choisie)
4. Le site se met à jour immédiatement

**Exemple de prompt :**
> "Ajoute un sujet sur le biais de confirmation. Description : on cherche naturellement les infos qui confirment ce qu'on croit déjà. Mon avis : c'est pour ça que débattre sur Internet ne sert à rien."

---

## Intégration Claude ↔ GitHub

Une connexion directe entre Claude et GitHub n'est pas disponible via MCP pour l'instant. Deux alternatives existent :

- **Claude Code** (terminal) : accès direct au dépôt Git en local
- **GitHub Action + formulaire** : formulaire mobile → mise à jour automatique du JSON via l'API GitHub (nécessite ~1h de setup)

Pour un usage immédiat, le flux manuel (JSON généré par Claude → collé dans l'éditeur) reste la solution la plus simple.

---

## Fichiers livrés

- `index.html` — site complet prêt à déployer
- `subjects.json` — 4 sujets d'exemple (Dunning-Kruger, Fermi, Moore, attention collective)
