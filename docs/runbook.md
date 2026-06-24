# Runbook - Agent FAQ Support Technique

## Objectif

Ce document décrit les actions à suivre en cas d’incident avec l’agent.

## Incident 1 : L’agent répond hors périmètre

### Symptôme

L’agent répond à une question qui ne concerne pas le support technique.

### Action

1. Désactiver l’agent avec le kill-switch.
2. Analyser la question utilisateur.
3. Corriger le prompt.
4. Tester avec plusieurs demandes hors périmètre.
5. Réactiver l’agent.

## Incident 2 : L’agent ne détecte pas une panne critique

### Symptôme

L’utilisateur signale une erreur grave, mais l’agent donne une réponse normale.

### Action

1. Désactiver l’agent.
2. Ajouter des règles de détection : erreur 500, panne générale, tous les utilisateurs bloqués.
3. Tester le workflow.
4. Redéployer.

## Kill-switch

Pour désactiver l’agent :

```json
{
  "agent_enabled": false
}
```
