# 2026-07-28 — v2 (MVP 0.0.2) e fluxo git

## Contexto

Depois de rodar o MVP v1 localmente, o Felipe definiu a direção do v2 em quatro ondas: objetivo como funcionalidade central (com porquê, prioridade e fila), modo Foco com temporizador e popup de transição, Home em cards estilo menu de apps com Framer Motion, e Conquistas com premiações configuráveis. Também definiu o fluxo git do projeto.

## O que foi feito

- **Fluxo git**: branch `mvp/mvp-0.0.1` preservando o v1; v2 construído em `mvp/mvp-0.0.2`; **PR #1** aberto para `main` (github.com/Felipe678/lume/pull/1). Convenções em `04-tecnologia/fluxo-git.md`.
- **Domínio v2**: prioridade/estimativa/fila/completedAt nos objetivos; premiações com 4 tipos de gatilho; perfil; stats (períodos, horas, ritmo, projeção, heatmap, maior sequência); sugestão de encaixes por prioridade; 13 medalhas automáticas; migração v1→v2. 74 testes.
- **UI v2**: Home em cards, Modo Foco (timer MM:SS + popup de transição + celebrações de prêmio e fila), GoalWizard de 6 passos, overlay de detalhe (Hoje/Semana/Mês + horas + projeção), toggle pizza/barra, Plano mensal (heatmap), Conquistas, Perfil, Configurações (CRUD de premiações + dados).
- **Verificação**: E2E dirigido em navegador headless cobrindo o fluxo inteiro (seed → wizard → foco/timer → transição → conclusão de objetivo → prêmio → fila → resgate → heatmap → persistência de preferências), sem erros de console.

## Decisões (com o porquê)

- Registradas em `04-tecnologia/decisoes-tecnicas.md`: schema v2 com migração (backups v1 continuam válidos), status de objetivo sempre derivado, premiações com unlock persistido vs medalhas derivadas, Framer Motion (regra: Foco não pisca), preferências de aparelho fora do backup.
- **Enriquecimento das premiações** (proposta aceita): gatilhos por objetivo/sequência/horas/semana perfeita; categorias (material, experiência, lazer, descanso, investir em si); resgate consciente com histórico; marcos de hábito 7/21/66/100 dias.

## Números novos

- 74 testes (35 novos) · bundle 144 KB gzip (+57 do Framer Motion) · 8 rotas · 13 medalhas.

## Aprendizados

- O requisito "painel sempre visível" e o requisito "dashboard rico" convivem bem com duas telas (`/` Home e `/foco` kiosk) + preferência de tela inicial por aparelho.
- `innerText` reflete `text-transform: uppercase` — asserts de E2E precisam ser case-insensitive.

## Próximos passos

- [ ] Revisar e mergear o PR #1
- [ ] Deploy na Vercel + PWA no tablet físico
- [ ] Começar o uso diário real (critério da Fase 1)
- [ ] Identidade visual definitiva da chama + domínio

## Arquivos alterados nesta sessão

- `02-produto/escopo-mvp.md`, `04-tecnologia/decisoes-tecnicas.md`, `04-tecnologia/fluxo-git.md` (novo), `README.md`, este diário.
