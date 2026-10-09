# StudySync

> Révise tes cours avec des quiz générés par IA à partir de tes propres PDF, et découvre ce que tu dois retravailler.

StudySync transforme un cours PDF en quiz QCM corrigé et expliqué, puis montre à l'étudiant les notions où il fait le plus d'erreurs. C'est le **projet 1** du module « Gestion de projet & collaboration » du MSc Epitech.

| | Lien |
|---|---|
| 📋 Board de suivi (GitHub Projects) | <https://github.com/users/JesuisMat/projects/4> |
| 📚 Documentation projet (Notion) | <https://curious-nitrogen-736.notion.site/StudySync-Espace-projet-3f45743a17a68185878cf3170e88d91a> |
| 🗺️ Sprints (milestones) | <https://github.com/JesuisMat/studysync/milestones> |

## Équipe

| Membre | Rôle | GitHub |
|---|---|---|
| Maxime | Product Owner + dev | [@maxlamenace33-del](https://github.com/maxlamenace33-del) |
| Alexis | Facilitateur / Scrum Master + dev | [@Alexis2mlt](https://github.com/Alexis2mlt) |
| Matthieu | Tech Lead + dev | [@JesuisMat](https://github.com/JesuisMat) |
| Julien | Développeur + Responsable doc | [@Julien33100](https://github.com/Julien33100) |

## Vision & personas

> 🚧 À compléter par le Product Owner — ticket [#21](https://github.com/JesuisMat/studysync/issues/21).

## Périmètre du MVP

1. Créer un compte, se connecter, se déconnecter
2. Importer un cours au format PDF
3. Générer un quiz de 10 QCM à partir d'un cours, avec la source citée pour chaque question
4. Répondre au quiz et obtenir une correction expliquée
5. Consulter l'historique de ses quiz et les notions à revoir en priorité

Hors périmètre : application mobile native, partage social, formats autres que PDF texte (pas d'OCR), questions ouvertes, paiement. Détails dans la fiche de cadrage (Notion).

## Organisation

- **Méthode :** Scrum, sprints d'1 semaine, du 12 octobre au 20 novembre 2026 (un milestone par sprint).
- **Backlog :** 3 épics, 17 user stories priorisées en MoSCoW, estimées en tailles de T-shirt.
- **Workflow Git :** GitHub Flow, `main` protégée, 1 relecture obligatoire par PR. Voir [CONTRIBUTING.md](CONTRIBUTING.md).

### Definition of Done

- [ ] Code relu : PR approuvée par au moins 1 autre membre
- [ ] Critères d'acceptation validés (démo ou test)
- [ ] README / doc à jour si nécessaire
- [ ] Mergé dans `main` (CI verte) et ticket déplacé en « Terminé »

## Architecture

> 🚧 Schéma du MVP à venir dans `docs/architecture.md` — ticket [#24](https://github.com/JesuisMat/studysync/issues/24).

## Démarrer en local

> 🚧 L'application sera initialisée au sprint 1 — ticket [#25](https://github.com/JesuisMat/studysync/issues/25).
