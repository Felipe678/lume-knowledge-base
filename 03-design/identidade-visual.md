# Identidade visual

## Marca

- **Nome:** Lume — chama em português. A chama do streak (à la Duolingo) é o coração da marca: manter o lume aceso todo dia.
- **Tom:** despojado, direto, motivador sem ser piegas. Copy curta ("Faltam 23 min", "A seguir: Inglês", "Dia completo 🔥").
- **Símbolo:** a chama. Estados: apagada (streak 0), acesa (streak ativo), grande/celebrando (dia completo). SVG próprio, animável.

## Princípios de UX do Painel (legível a 3 metros)

1. **Tipografia gigante** — atividade atual com `clamp()` (~8vw); nada estoura o layout (ellipsis em títulos longos).
2. **Tema escuro único** no MVP — painel aceso o dia todo na parede: menos luz, menos burn-in, mais contraste.
3. **Cor = objetivo** — cada objetivo tem cor de uma paleta fixa + emoji; a cor do bloco atual tinge o acento da tela.
4. **Zero fricção** — `/` abre direto no Painel; navegação escondida (toque revela); check-in é um botão gigante com desfazer em toast (sem diálogo de confirmação).
5. **O relógio manda** — a tela avança sozinha; ninguém "opera" o painel, ele acompanha o dia.

## Paleta (v1, refinar depois)

| Papel | Valor |
|---|---|
| Fundo | quase-preto quente (`#0c0a09`, stone-950) |
| Texto | branco quente (`#fafaf9`) |
| Chama | gradiente âmbar → laranja (`#f59e0b` → `#ea580c`) |
| Cores de objetivo | paleta fixa de 8 tokens (amber, sky, emerald, rose, violet, lime, cyan, fuchsia) |

Pendente: logotipo, ícone PWA definitivo, animação da chama.
