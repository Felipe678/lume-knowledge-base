# Log de decisões técnicas

Decisões com data no título. Nunca apagar — reverter com nova entrada e o porquê.

## Instâncias derivadas, não materializadas (decisão 2026-07-28)

A grade (`TimeBlock[]`) é a fonte da verdade da recorrência. O "dia de hoje" é calculado em memória; só check-ins são persistidos (`"AAAA-MM-DD:blockId"`). **Por quê:** elimina jobs de materialização, migrações de instância e estados fantasma; o custo (editar a grade reinterpreta o passado) é aceitável porque o streak deriva só de check-ins.

## Intervalo semiaberto [início, fim) (decisão 2026-07-28)

Às 09:00 em ponto, o bloco que termina 09:00 já acabou e o que começa 09:00 é o atual. **Por quê:** blocos adjacentes nunca disputam o "agora".

## Streak com dia neutro (decisão 2026-07-28)

Dia sem blocos agendados não quebra nem incrementa o streak. Hoje vazio não zera (a chama de ontem vale até meia-noite). **Por quê:** domingo livre não pode punir — puniria justamente quem montou uma grade realista. Aproximação consciente: dias neutros derivam da grade atual; snapshot diário fica para v2.

## Datas sempre locais (decisão 2026-07-28)

`todayISO()` formata manualmente a data local; proibido `toISOString().slice(0,10)` (UTC quebra à noite no fuso BR — 21h de terça já seria "quarta").

## Check-in de qualquer bloco de hoje (decisão 2026-07-28)

Upcoming, current ou missed — terminou antes ou fez atrasado, conta igual. Retroativo de outros dias fica para v2. **Por quê:** o app pune a inconstância, não a vida real.
