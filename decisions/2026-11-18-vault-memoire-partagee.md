---
type: decision
source: [human, claude-code]
created: 2026-11-18
updated: 2026-11-18
tags: [vault, memory, agents]
---

# Vault Obsidian comme mémoire partagée humain + agents

## Contexte

Besoin d'une mémoire commune entre moi, Claude Code et d'autres agents IA (Codex, workers Orca). La mémoire automatique de Claude Code (`~/.claude/projects/<projet>/memory/`) est cloisonnée par projet et invisible des autres agents.

## Décision

- Vault en fichiers Markdown simples dans `~/work/vault`, versionné en Git local sans remote ; Obsidian sert seulement à la lecture et la navigation humaine.
- Les agents y accèdent directement par le système de fichiers ; les conventions sont dans [[AGENTS]].
- Il **complète** la mémoire automatique de Claude Code, qu'il ne remplace pas : celle-ci garde les détails propres à Claude dans un projet, le vault reçoit ce qui sert à tous.
- Branchement Claude Code : ligne de pointeur dans `~/.claude/CLAUDE.md` + `permissions.additionalDirectories` dans `~/.claude/settings.json`.
- Les agents ne commitent pas : je relis et je commite.

## Alternatives écartées

- **Serveur MCP Obsidian** (plugin Local REST API) : exige Obsidian ouvert, une clé d'API et une configuration par agent, pour un gain limité par rapport à `grep`.
- **Remplacer la mémoire automatique de Claude** : contourne un mécanisme intégré, sans bénéfice pour les autres agents.
- **Skill `/vault` dédié** : à ajouter seulement si les agents appliquent mal les conventions.
