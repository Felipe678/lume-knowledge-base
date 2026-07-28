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
- **MVP v1:** branch `mvp/mvp-0.0.1` no GitHub (`github.com/Felipe678/lume`)
- **v2 (MVP 0.0.2):** PR #1 aberto para `main` — Home em cards, Modo Foco com timer, assistente de objetivos com prioridade/fila, overlay de progresso, Conquistas & Premiações, Framer Motion; 74 testes + E2E
- **Fluxo git definido:** GitFlow adaptado (`mvp/`, `rlse/`, `fix/`, `hotfix/`, PR para main) — ver `04-tecnologia/fluxo-git.md`
- **Decisões pendentes:** registro de domínio (lume.app / lumelabs.com.br), identidade visual definitiva da chama
- **Próxima frente:** merge do PR #1 → deploy na Vercel → teste físico no tablet (Fase 1 → critério: 2 semanas de uso diário)
