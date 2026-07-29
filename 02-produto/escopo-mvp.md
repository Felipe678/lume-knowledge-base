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

## v3 — MVP 0.0.3 (feedback de uso real, 2026-07-29)

1. **Foco manual com confirmação**: clicar em bloco pendente/perdido abre modal ("Iniciar? Leva X min") e vira o foco atual com timer próprio; troca de foco vigente é confirmada. Barra de progresso decorrido + checklist de etapas no Foco.
2. **Rotina de trabalho**: semanal fixa e escala cíclica com âncora (12x36, 24x72, plantão noturno virando o dia); sugestões de encaixe desviam do trabalho e o FitEditor avisa conflitos.
3. **Rotina (estilo de vida)**: blocos sem objetivo são "Rotina" — separados na timeline/Home, quick-add com 13 sugestões na Grade.
4. **Navegação contínua**: Home → rolar para baixo revela o Foco (scroll-snap); `/foco` segue para o kiosk.
5. **Alertas locais**: voz pt-BR + notificação com frases motivacionais (Alexa → backlog).
6. **Fechamento do dia**: resumo + frase de transição + preview de amanhã.
7. **Conta + sync**: server Express+Mongo (JWT, tenant uuid), local-first com last-write-wins e conflito 409; modo convidado continua integral.

## Status de construção (2026-07-29)

| Entrega | Status |
|---|---|
| MVP v1 (branch `mvp/mvp-0.0.1`) | ✅ no GitHub |
| v2 (branch `mvp/mvp-0.0.2`) | ✅ PR #1 aberto para `main` |
| v3 (branch `mvp/mvp-0.0.3`) | ✅ PR #2 aberto para `main` |
| Testes | ✅ 103 no domínio + 7 no server + E2E headless sem erros |
| MongoDB Atlas | ✅ cluster criado e conectado (2026-07-29) — smoke completo: register/login/sync/409 |
| Deploy Vercel + API | pendente |
| Teste físico no tablet | pendente |
