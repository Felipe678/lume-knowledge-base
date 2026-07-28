# 2026-07-28 — Construção do MVP (do zero ao GitHub)

## Contexto

Mesma sessão da fundação: com o plano aprovado, o MVP foi construído inteiro em `J:\Projetos\lume`.

## O que foi feito

- App completo: Painel ambiente (`/`), Grade semanal (`/grade`) e Objetivos (`/objetivos`).
- Domínio puro com 39 testes unitários (agenda derivada, intervalo semiaberto, streak com dia neutro, datas locais, validação de import).
- Time travel de dev, Wake Lock, check-in com desfazer, export/import JSON, PWA (autoUpdate, fullscreen), ícones da chama.
- Verificação E2E dirigida em navegador headless: seed → grade → painel → time travel para 08:30 → check-in (chama 0→1, anel 0/3→1/3) → virada de dia automática (streak preservado). Sem erros de console.
- Push para `github.com/Felipe678/lume` (app) e `github.com/Felipe678/lume-knowledge-base` (este KB).

## Decisões (com o porquê)

- **`react-router` puro no lugar de `react-router-dom`** — a versão dom mais recente embutia um `react-router` com CVE (CSRF no modo RSC, não explorável em SPA, mas auditoria limpa vale o custo zero); desde a v7 o pacote base exporta tudo. Produção com 0 vulnerabilidades.
- **Emoji do seed sem bandeiras** (📚 no lugar de 🇬🇧) — Windows não renderiza emojis de bandeira; o painel pode rodar em monitor Windows.
- Vulnerabilidades restantes do `npm audit` são todas de devDependencies (tooling), não afetam o app servido.

## Números novos

- 39 testes passando · bundle ~87 KB gzip · build ~250 ms.

## Aprendizados

- O time travel como infraestrutura de primeira classe pagou-se na mesma hora: o dia inteiro foi simulado em segundos no teste E2E.

## Próximos passos

- [ ] Conectar o repo na Vercel (deploy contínuo; `vercel.json` já incluso)
- [ ] Instalar como PWA no tablet e fazer o teste físico (legibilidade a 3 m, Wake Lock)
- [ ] Começar o uso diário real (critério de saída da Fase 1: 2 semanas sem abandonar)

## Arquivos alterados nesta sessão

- `02-produto/escopo-mvp.md` (status de construção)
- `README.md` (Estado atual)
- Este diário.
