# Log de decisões técnicas

Decisões com data no título. Nunca apagar — reverter com nova entrada e o porquê.

## Sync local-first com last-write-wins (decisão 2026-07-29)

App continua 100% funcional offline/convidado; logado, o AppState inteiro sincroniza (PUT debounced com `baseUpdatedAt`). Conflito (outro aparelho salvou depois) → 409 → backup local + adota a versão do servidor + aviso visível. Primeira sincronização com dados dos dois lados → o usuário escolhe (nunca mesclar automaticamente). **Por quê:** o tablet da parede não pode depender de internet; para 1 usuário com poucos aparelhos, LWW com aviso é simples e suficiente — merge/CRDT fica para quando doer.

## Sessão de foco manual por aparelho (decisão 2026-07-29)

`manualFocus` vive em `lume:session` (fora do AppState/export/sync): sobrevive a reload do tablet, não vaza para outros aparelhos. Status sempre derivado (`resolveFocus`): sessão de bloco excluído/concluído/dia diferente é descartada sozinha. **Por quê:** foco é estado do aparelho, não do usuário.

## Trabalho noturno como segmentos por data (decisão 2026-07-29)

`end <= start` = turno vira o dia; o domínio responde "quais faixas ocupam ESTA data" (0–2 segmentos). Escala cíclica usa módulo normalizado (âncora no futuro funciona). **Por quê:** plantão 19h–7h é o caso real de quem vive de escala; tratar por data elimina os bugs clássicos de "que dia é o turno".

## Alertas locais antes de Alexa (decisão 2026-07-29)

SpeechSynthesis pt-BR + Notification API com frases motivacionais determinísticas (âncora anti-repetição pós-reload). Skill Alexa própria é projeto à parte → backlog. **Por quê:** 90% do valor com 5% do custo; sem dependência de nuvem de terceiros no MVP.

## Instâncias derivadas, não materializadas (decisão 2026-07-28)

A grade (`TimeBlock[]`) é a fonte da verdade da recorrência. O "dia de hoje" é calculado em memória; só check-ins são persistidos (`"AAAA-MM-DD:blockId"`). **Por quê:** elimina jobs de materialização, migrações de instância e estados fantasma; o custo (editar a grade reinterpreta o passado) é aceitável porque o streak deriva só de check-ins.

## Intervalo semiaberto [início, fim) (decisão 2026-07-28)

Às 09:00 em ponto, o bloco que termina 09:00 já acabou e o que começa 09:00 é o atual. **Por quê:** blocos adjacentes nunca disputam o "agora".

## Streak com dia neutro (decisão 2026-07-28)

Dia sem blocos agendados não quebra nem incrementa o streak. Hoje vazio não zera (a chama de ontem vale até meia-noite). **Por quê:** domingo livre não pode punir — puniria justamente quem montou uma grade realista. Aproximação consciente: dias neutros derivam da grade atual; snapshot diário fica para v2.

## Datas sempre locais (decisão 2026-07-28)

`todayISO()` formata manualmente a data local; proibido `toISOString().slice(0,10)` (UTC quebra à noite no fuso BR — 21h de terça já seria "quarta").

## Schema v2 com migração automática (decisão 2026-07-28)

`schemaVersion: 2` adiciona prioridade/estimativa/fila nos objetivos, premiações (`rewards`) e perfil. Migração pura v1→v2 no persist (mesma chave `lume:v1`) e no import de backup (aceita v1 e v2). **Por quê:** backups v1 do Felipe continuam válidos — check-ins são sagrados (princípio 7).

## Status de objetivo sempre derivado (decisão 2026-07-28)

`archived | queued | completed | active` deriva de `archivedAt`/`afterGoalId`/etapas — nunca persistido. Ativar da fila = apagar `afterGoalId`. Bloqueador concluído, arquivado ou inexistente libera a fila. **Por quê:** campo de status persistido dessincroniza; dado quebrado nunca pode prender o usuário.

## Premiações com unlock persistido, medalhas derivadas (decisão 2026-07-28)

Premiações do usuário carimbam `unlockedAt` uma única vez (reconciliação após check-in/etapa). Medalhas automáticas são 100% derivadas dos dados. **Por quê:** prêmio destravado não pode "des-destravar" ao editar dados; medalhas sem estado não têm bug de sincronização.

## Framer Motion como lib de animação (decisão 2026-07-28)

+~56 KB gzip aceitos pela centralidade da gamificação. Regra: animações curtas (<400ms); o modo Foco só anima chama e popups (tela ambiente não pisca).

## Preferências de aparelho fora do AppState (decisão 2026-07-28)

`lume:ui` (pizza/barra, tela inicial) em chave própria, fora do export/import. **Por quê:** o tablet da parede e o desktop podem divergir; backup carrega dados do usuário, não do aparelho.

## Check-in de qualquer bloco de hoje (decisão 2026-07-28)

Upcoming, current ou missed — terminou antes ou fez atrasado, conta igual. Retroativo de outros dias fica para v2. **Por quê:** o app pune a inconstância, não a vida real.
