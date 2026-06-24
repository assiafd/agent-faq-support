# Agent Card - Agent FAQ Support Technique

## Nom

Agent FAQ Support Technique

## Version

v1.0.0

## Objectif

Répondre aux questions techniques simples des utilisateurs.

## Entrées

Question utilisateur en texte libre.

## Sorties

Réponse courte, claire et professionnelle.

## Périmètre

- Connexion
- Mot de passe
- Accès utilisateur
- Bug simple
- Utilisation de la plateforme

## Hors périmètre

- Questions médicales
- Questions juridiques
- Piratage
- Demandes personnelles
- Sujets non techniques

## Modèle utilisé

Groq - llama-3.1-8b-instant

## Risques

- Mauvaise classification d’une demande critique
- Réponse incomplète
- Réponse hors périmètre

## Kill-switch

Variable : AGENT_ENABLED=false

## Propriétaire

Équipe IA / Support
