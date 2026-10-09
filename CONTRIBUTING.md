# Contribuer à StudySync

## Workflow Git (GitHub Flow)

`main` est protégée : personne ne pousse directement dessus, pas même les administrateurs. Tout changement passe par une Pull Request relue.

1. **Prendre un ticket** sur le [board](https://github.com/users/JesuisMat/projects/4), s'assigner et le passer en « En cours » (1 seul ticket en cours par personne).
2. **Créer une branche** depuis `main` à jour :

   ```bash
   git switch main && git pull
   git switch -c feature/6-import-pdf
   ```

   Préfixes : `feature/`, `fix/`, `docs/`, `chore/`, suivis du n° du ticket et d'un slug court.
3. **Commiter** au format [Conventional Commits](https://www.conventionalcommits.org/fr/) avec le n° du ticket :

   ```text
   feat: import d'un cours PDF (#6)
   fix: message d'erreur sur fichier trop lourd (#6)
   docs: ajoute la vision produit au README (#21)
   ```

   Types utilisés : `feat`, `fix`, `docs`, `chore`, `refactor`, `test`, `style`.
4. **Ouvrir la PR** vers `main`, remplir le template, mettre `Closes #<n°>` et demander la relecture d'un autre membre. Le ticket passe en « En revue ».
5. **Relecture** : au moins 1 approbation. Toute nouvelle modification invalide l'approbation précédente et toutes les conversations doivent être résolues.
6. **Merge** en *squash* par l'auteur une fois approuvée. La branche est supprimée automatiquement et le ticket passe en « Terminé ».

## Relire une PR

- Les critères d'acceptation du ticket sont-ils couverts ?
- Le code est-il lisible, sans secret ni donnée personnelle (le repo est public) ?
- La doc est-elle à jour si le comportement change ?
- Commenter avec bienveillance : proposer, expliquer pourquoi, distinguer bloquant et suggestion.

## Méthode & rituels

> 🚧 À compléter par le Facilitateur — ticket [#22](https://github.com/JesuisMat/studysync/issues/22).
