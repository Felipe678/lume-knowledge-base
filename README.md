# Lume — Knowledge Base

Memória de longo prazo do projeto **Lume**: app organizador visual de objetivos e tarefas diárias — um "quadro de horários da escola" vivo, sempre aberto num tablet/monitor da casa, que transforma objetivos grandes em evolução diária, com constância gamificada estilo Duolingo.

## Mapa do repositório

| Pasta | Conteúdo |
|---|---|
| `00-visao/` | Visão, manifesto, metas e roadmap por fases |
| `01-negocio/` | Princípios fixos, modelo de negócio, KPIs |
| `02-produto/` | Conceito, personas, escopo do MVP, backlog de ideias |
| `03-design/` | Identidade visual e princípios de UX |
| `04-tecnologia/` | Stack, arquitetura e log de decisões técnicas |
| `diario/` | Log cronológico de sessões de trabalho (usar `TEMPLATE.md`) |
| `arquivos/` | Entregáveis binários derivados dos `.md` |

O código do app vive em repo separado: `J:\Projetos\lume`.

## Estado atual (2026-07-28)

- **Fase:** 1 — Construção do MVP (ver `00-visao/roadmap-fases.md`)
- **Meta ativa:** MVP funcional rodando num tablet na parede de casa, usado pelo Felipe todos os dias
- **Produto:** Lume 🔥 (app web React + Vite, PWA, modo Painel ambiente)
- **Empresa/marca:** Lume Labs (marca nova de software, separada da Vertex Studio Lab)
- **MVP v1:** branch `mvp/mvp-0.0.1` · **v2:** PR #1 · **v3:** PR #2 (`github.com/Felipe678/lume`)
- **v3 (MVP 0.0.3, feedback de uso real):** foco manual com confirmação + timer + checklist, rotina de trabalho (12x36/plantões), Rotina vs Objetivos, Home contínua (scroll → Foco), alertas de voz/notificação, fechamento do dia, **login + sync MongoDB local-first** (110 testes no total)
- **Fluxo git:** GitFlow adaptado (`mvp/`, `rlse/`, `fix/`, `hotfix/`, PR para main) — ver `04-tecnologia/fluxo-git.md`
- **Decisões pendentes:** registro de domínio, identidade visual definitiva da chama
- **Próxima frente:** revisar/mergear PRs #1 e #2 → criar cluster no MongoDB Atlas (`server/.env`) → deploy (Vercel + API) → teste físico no tablet (Fase 1 → 2 semanas de uso diário)
