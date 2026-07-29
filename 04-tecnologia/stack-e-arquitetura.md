# Stack e arquitetura

Repo do app: `J:\Projetos\lume` · GitHub: `github.com/Felipe678/lume`

## Stack (decisão 2026-07-28)

| Área | Escolha | Por quê |
|---|---|---|
| Base | React + Vite + TypeScript | Velocidade máxima de MVP; decidido com o Felipe |
| Estado | Zustand + middleware `persist` | localStorage de graça (com version/migrate); seletores evitam re-render global no tick do relógio |
| Rotas | react-router-dom | 3 rotas, padrão |
| Estilo | Tailwind CSS v4 | Layout fullscreen/dark rápido; paleta via `@theme` |
| Datas | Helpers próprios (`domain/dates.ts`) | Domínio só usa "HH:mm" e data local ISO; ~40 linhas; date-fns só se doer |
| Ícones | lucide-react | Leve; a chama é SVG próprio |
| Testes | Vitest | Unitários no domínio puro |
| PWA | vite-plugin-pwa (`autoUpdate`) | Fullscreen no tablet; tablet sempre ligado não pode prender service worker velho |
| Deploy | Vercel | Grátis, push-to-deploy |

## Arquitetura

- **Domínio puro** (`src/domain/`): types, dates, schedule, progress, streak — funções puras, 100% testáveis, zero React.
- **Grade é a fonte da verdade da recorrência**: instâncias diárias são derivadas em memória (`getDayActivities`); só o check-in é persistido, chaveado por `"AAAA-MM-DD:blockId"`.
- **Clock store separado** (`useClock`): tick de 10s + `devOffsetMs` (time travel de dev, hard-gated por `import.meta.env.DEV`); fonte única de "agora" para todos os componentes; tick forçado em `visibilitychange`.
- **Views** (`src/features/`): `painel/` (kiosk, rota `/`), `grade/`, `objetivos/`.
- Wake Lock API no Painel; export/import JSON com `validateAppState`; listener de `storage` para múltiplas abas.

## Backend (v3, 2026-07-29)

- `server/` no próprio repo: Express 5 + Mongoose + bcryptjs + JWT (30d) + CORS restrito.
- MongoDB **Atlas free** (decisão) — `server/.env` a partir do `.env.example`; sem Atlas, `npm run dev:memory` sobe com Mongo em memória.
- Rotas: `POST /auth/register|login`, `GET/PUT /state` (LWW com `baseUpdatedAt`; conflito → 409 com a versão do servidor). Tenant = `userId` uuid.
- Testes: supertest + mongodb-memory-server. Scripts raiz: `dev:server`, `test:server`.
- **Fase futura registrada:** deploy da API (Render/Railway), refresh tokens, microserviços.

## Fora do MVP por decisão

Lib de componentes (Painel é 100% custom), i18n (PT-BR fixo), merge automático de sync (CRDT), skill Alexa própria.
