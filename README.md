# Agent FAQ Support Technique

## Description

Ce projet implémente un agent IA simple de support technique sur la plateforme Agentic AI (Langflow).

L'objectif est de démontrer les bonnes pratiques de mise en production d'un agent IA :

- Documentation via une Agent Card
- Versionnement des prompts et configurations avec Git
- Gestion des incidents via un Runbook
- Mise en place d'un Kill-Switch
- Possibilité de rollback vers une version stable

---

# Objectif métier

L'agent répond aux questions simples liées au support technique :

- Connexion utilisateur
- Mot de passe oublié
- Gestion des accès
- Utilisation de la plateforme
- Erreurs simples

L'agent ne traite pas :

- Questions médicales
- Questions juridiques
- Questions financières
- Demandes de piratage
- Sujets hors périmètre

---

# Architecture du workflow

```text
Chat Input
    ↓
Prompt Template - JSON Config
    ↓
Groq - JSON Generator
    ↓
Smart Router (Kill Switch)
    ├── agent_enabled
    │         ↓
    │   Prompt Agent FAQ
    │         ↓
    │      Groq
    │         ↓
    │    Chat Output
    │
    └── agent_disabled
              ↓
     Chat Output Maintenance
```

---

# Structure du projet

```text
agent-faq-support/
│
├── prompts/
│   └── agent_faq_prompt.md
│
├── config/
│   └── agent_config.json
│
├── docs/
│   ├── agent_card.md
│   └── runbook.md
│
├── workflow/
│   └── workflow.json
│
└── README.md
```

---

# Agent Card

L'Agent Card décrit :

- Le rôle de l'agent
- Son périmètre fonctionnel
- Ses limites
- Les risques identifiés
- Les règles de sécurité
- Le modèle utilisé
- Le propriétaire du système

Consulter :

```text
docs/agent_card.md
```

---

# Prompt Versioning

Le prompt principal de l'agent est stocké dans :

```text
prompts/agent_faq_prompt.md
```

Cela permet :

- le suivi des modifications
- l'audit des changements
- le rollback vers une version précédente

---

# Configuration

Le fichier de configuration :

```text
config/agent_config.json
```

Exemple :

```json
{
  "agent_name": "Agent FAQ Support Technique",
  "version": "v1.0.0",
  "agent_enabled": true,
  "model": "llama-3.1-8b-instant",
  "temperature": 0.2
}
```

---

# Kill-Switch

Le Kill-Switch permet de désactiver immédiatement l'agent.

Activation :

```json
{
  "agent_enabled": true
}
```

Désactivation :

```json
{
  "agent_enabled": false
}
```

Lorsque l'agent est désactivé, le Smart Router redirige automatiquement vers :

```text
L’agent est temporairement désactivé pour maintenance.
Veuillez contacter le support humain.
```

---

# Gestion des incidents

La procédure complète est documentée dans :

```text
docs/runbook.md
```

Exemples d'incidents :

- Réponse hors périmètre
- Mauvaise classification
- Détection incorrecte d'un incident critique
- Mauvais comportement du modèle

---

# Versioning Git

Initialisation :

```bash
git init
git add .
git commit -m "Initial release"
```

Création de la première version :

```bash
git tag v1.0.0
```

Liste des versions :

```bash
git tag
```

---

# Rollback

Retour vers une version stable :

```bash
git checkout v1.0.0
```

---

# Cas de test

## Test 1

Entrée :

```text
J’ai oublié mon mot de passe.
```

Résultat attendu :

```text
Instructions de réinitialisation du mot de passe.
```

---

## Test 2

Entrée :

```text
Quelle est la capitale du Maroc ?
```

Résultat attendu :

```text
Cette demande est hors périmètre pour l’Agent FAQ Support Technique.
Veuillez contacter le support humain.
```

---

## Test 3

Entrée :

```text
Tous les utilisateurs obtiennent une erreur 500.
```

Résultat attendu :

```text
Un incident critique semble détecté.
Veuillez contacter immédiatement l’équipe support.
```

---

# Technologies utilisées

- Agentic AI Platform
- Langflow
- Groq LLM
- Smart Router
- Git
- Markdown

---

# Auteur

Assia AL Farrad

Projet réalisé dans le cadre du laboratoire :

**Agent Card, Prompt Versioning, Runbook, Kill-Switch et Rollback pour les systèmes IA.**
