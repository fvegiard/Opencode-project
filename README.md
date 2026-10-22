# Opencode-project

Ce dépôt contient de la configuration et des documents pour les agents Pi et
OpenSpec. Il ne contient actuellement aucune application, aucun code Python,
aucun manifeste de dépendances ni suite de tests ou de build exécutable.

## Contenu

| Chemin | Rôle |
| --- | --- |
| [AGENTS.md](AGENTS.md) | Consignes applicables au dépôt et validation disponible. |
| [.pi/settings.json](.pi/settings.json) | Paramètres Pi, actuellement vides; aucune initialisation automatique de worktree. |
| [.pi/prompts](.pi/prompts) | Huit prompts pour les changements OpenSpec, la planification et une boucle TDD. |
| [.pi/skills](.pi/skills) | Sept dossiers de skills décrivant des procédures d'agent. |
| [.pi/dashboard/knowledge_base.json](.pi/dashboard/knowledge_base.json) | Configuration de la base de connaissances et de sa doctrine. |
| [.pi/dashboard/kb/index.db](.pi/dashboard/kb/index.db) | Base locale de connaissances suivie dans Git; son contenu n'est pas validé par les vérifications ci-dessous. |
| [openspec/config.yaml](openspec/config.yaml) | Configuration OpenSpec avec le schéma `spec-driven`. |

Les prompts et skills décrivent des procédures; leur présence ne signifie pas
qu'une application, ses dépendances ou les outils externes sont installés.
Aucun changement OpenSpec actif n'est actuellement enregistré dans ce dépôt.

## Validation disponible

Depuis la racine, avec PowerShell 7, vérifier que les deux configurations JSON
sont lisibles :

```powershell
$ErrorActionPreference = 'Stop'
Get-Content -LiteralPath '.pi/settings.json' -Raw | ConvertFrom-Json
Get-Content -LiteralPath '.pi/dashboard/knowledge_base.json' -Raw | ConvertFrom-Json
```

Vérifier aussi que les liens locaux des documents modifiés pointent vers des
fichiers ou dossiers existants. Cette validation porte sur les formats et les
références; elle ne lance ni Pi, ni OpenSpec, ni une application.

L'ancien hook de worktree qui créait un environnement Python et installait un
fichier de dépendances absent a été retiré. Une nouvelle initialisation devra
être fondée sur des sources et un manifeste réellement ajoutés au dépôt.
