# Escopo do MVP (decisão 2026-07-28)

## Dentro

- CRUD de Objetivos com etapas (fragmentação manual)
- Grade semanal de blocos recorrentes (vinculados a objetivo ou "Obrigatória")
- **Modo Painel** (rota `/`, kiosk): atividade atual gigante com tempo restante, próxima atividade, timeline do dia, progresso do dia, progresso diário/total por objetivo, chama/streak, botão de check-in
- Check-in de qualquer bloco de hoje (antecipado, atual ou atrasado) + desfazer
- Export/import JSON validado
- Tema escuro único, PWA fullscreen, Wake Lock, deploy Vercel

## Fora (vai para `backlog-ideias.md`)

Backend/login/sync, notificações, exceções de recorrência, drag-and-drop na grade, blocos cruzando meia-noite, estatísticas históricas, streak freeze, tema claro, check-in retroativo.

## Regras de domínio decididas

- Instâncias diárias são **derivadas** da grade — nunca materializadas; só o check-in é persistido (`"AAAA-MM-DD:blockId"`).
- Blocos usam intervalo semiaberto `[início, fim)`; validação: fim > início, mínimo 5 min, sem cruzar meia-noite.
- **Streak:** dia aceso = ≥1 check-in; dia **neutro** (0 blocos agendados) não quebra nem incrementa; hoje vazio ainda não zera (chama de ontem vale até meia-noite). Dias neutros derivam da grade atual (aproximação consciente; snapshot diário fica para v2).
- Datas sempre no fuso local; fonte única de "agora" (clock store, tick 10s).

Os 13 passos de construção e os 33 edge cases numerados estão no plano de implementação (sessão de fundação, ver diário 2026-07-28).

## v2 — MVP 0.0.2 (decisão e construção 2026-07-28)

Quatro ondas de requisitos do Felipe transformaram o produto:

1. **Objetivo é a funcionalidade central** — GoalWizard de 6 passos (o quê / por quê / prioridade / estimativa de horas / etapas / quando / encaixes sugeridos pela prioridade: alta = 5×60min, média = 3×45min, baixa = 2×30min). **Fila de objetivos** (`afterGoalId`): começam após outro concluir, com celebração e ativação guiada no Foco.
2. **Modo Foco** (`/foco`) — temporizador regressivo MM:SS da atividade atual; popup animado de transição ao término pedindo permissão para prosseguir.
3. **Home em cards** (`/`) — grid estilo menu de apps: Foco atual, Progresso diário, Progresso total, Objetivos, Plano semanal, Plano mensal, Conquistas, Perfil, Configurações. Animações com Framer Motion. Overlay de detalhe por objetivo: Hoje/Semana/Mês, horas investidas vs estimadas, projeção. Layout pizza/barra alternável.
4. **Conquistas & Premiações** — galeria de objetivos concluídos, 13 medalhas automáticas (streaks 7/21/66/100, semana perfeita, horas...), premiações configuráveis com gatilhos (concluir objetivo / sequência / horas / semana perfeita) e resgate com histórico.

## Status de construção (2026-07-28)

| Entrega | Status |
|---|---|
| MVP v1 (branch `mvp/mvp-0.0.1`) | ✅ no GitHub |
| v2 completo (branch `mvp/mvp-0.0.2`) | ✅ PR #1 aberto para `main` |
| Testes | ✅ 74 unitários no domínio + E2E headless sem erros |
| Deploy Vercel | pendente (conectar o repo na Vercel; `vercel.json` pronto) |
| Teste físico no tablet | pendente |
