# Architecture du MVP

> Proposition du Tech Lead, à formaliser en ADR-004 pendant le sprint 1.

## Stack

| Brique | Choix | Pourquoi |
|---|---|---|
| Front + API | Next.js (TypeScript) | Un seul projet pour l'interface et les routes serveur |
| Auth, base, stockage | Supabase (Auth, Postgres, Storage) | Offre gratuite, auth prête à l'emploi, règles d'accès par utilisateur (RLS) |
| Génération de quiz | API d'un modèle de langage, sortie JSON structurée | Isolée derrière une interface pour pouvoir changer de fournisseur |
| Hébergement | Vercel | Déploiement automatique et URL de prévisualisation par PR |

## Vue d'ensemble

```mermaid
flowchart LR
    U["Étudiant<br>navigateur"] --> F["Next.js<br>pages + routes API"]
    F --> A["Supabase Auth"]
    F --> S["Supabase Storage<br>PDF des cours"]
    F --> D["Supabase Postgres<br>cours, quiz, réponses"]
    F --> X["Extraction du texte<br>du PDF"]
    X --> L["API LLM<br>génération du quiz JSON"]
    L --> F
    V["Vercel"] -. héberge .- F
```

## Parcours principal : du PDF au quiz

```mermaid
sequenceDiagram
    actor E as Étudiant
    participant App as Next.js
    participant St as Supabase Storage
    participant DB as Postgres
    participant LLM as API LLM
    E->>App: Importe un cours PDF (A3)
    App->>St: Stocke le fichier (privé)
    App->>DB: Crée le cours + texte extrait
    E->>App: Génère un quiz (B1)
    App->>LLM: Texte du cours + consignes (10 QCM, source, notion)
    LLM-->>App: Quiz au format JSON
    App->>DB: Enregistre le quiz et ses questions
    E->>App: Répond aux questions (B2)
    App->>DB: Enregistre réponses + score
    App-->>E: Correction expliquée (B3)
```

## Modèle de données (première version)

```mermaid
erDiagram
    USER ||--o{ SUBJECT : organise
    USER ||--o{ COURSE : importe
    SUBJECT ||--o{ COURSE : contient
    COURSE ||--o{ QUIZ : genere
    QUIZ ||--|{ QUESTION : contient
    QUIZ ||--o{ ATTEMPT : est_passe
    ATTEMPT ||--|{ ANSWER : contient
    QUESTION ||--o{ ANSWER : recoit
    QUESTION {
        text statement
        json choices
        int correct_index
        text explanation
        text source_ref
        text notion
    }
```

## Points d'attention

- **Secrets :** clés Supabase et LLM uniquement dans les variables d'environnement Vercel / `.env.local` (jamais commitées, le repo est public).
- **Données :** chaque cours est privé à son utilisateur (politiques RLS sur toutes les tables).
- **Qualité IA :** chaque question garde sa source (`source_ref`) et sa notion (`notion`), utilisées par la correction (B3) et les notions à revoir (C2).
