# Fluxo git (decisão 2026-07-28)

Padrão GitFlow adaptado, definido pelo Felipe. Vale para o repo do app (`Felipe678/lume`).

## Branches

| Tipo | Padrão | Uso |
|---|---|---|
| Tronco | `main` | Equivalente ao "master" do GitFlow — só recebe merge via PR |
| MVP / desenvolvimento | `mvp/mvp-X.Y.Z` | Cada iteração do MVP (ex.: `mvp/mvp-0.0.1` = v1, `mvp/mvp-0.0.2` = v2) |
| Lançamento | `rlse/vX.Y.Z` | Quando o projeto for implantado de fato (ex.: `rlse/v1.0.0`) |
| Correção | `fix/nome-do-bug-correcao` | Bugs em desenvolvimento |
| Correção urgente | `hotfix/nome-do-bug-correcao` | Bugs em produção |

## Regras

1. Toda implementação de branch MVP entra em `main` via **Pull Request** — nunca push direto.
2. O estado de cada MVP fica preservado no seu branch (histórico navegável de versões).
3. Commits em português, prefixos `feat:`/`fix:`/`docs:`/`chore:` com escopo quando fizer sentido (`feat(dominio):`).
4. O KB (`lume-knowledge-base`) é documentação: commit direto na `main` com prefixo `docs:`, seguindo o protocolo do próprio CLAUDE.md.

## Histórico

- `mvp/mvp-0.0.1` — MVP v1 (Painel, Grade, Objetivos) — 2026-07-28
- `mvp/mvp-0.0.2` — v2 (Home em cards, Foco com timer, wizard, fila, conquistas/premiações) — PR #1 — 2026-07-28
