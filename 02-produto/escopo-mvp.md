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

## Status de construção

| Passo | Status |
|---|---|
| 1. Bootstrap Vite + Tailwind | em andamento |
| 2–13 | pendente |
