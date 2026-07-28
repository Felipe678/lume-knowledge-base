# CLAUDE.md — Protocolo de trabalho no lume-knowledge-base

Este repositório é a memória de longo prazo do projeto **Lume** (app organizador visual de objetivos e tarefas diárias) e da marca de software que o abriga (**Lume Labs**). Toda sessão de trabalho (humana ou com Claude) lê daqui e escreve de volta aqui.

## Início de sessão (obrigatório)

1. Ler `README.md` (mapa do repo + Estado atual).
2. Ler `00-visao/roadmap-fases.md`.
3. Ler as 2–3 entradas mais recentes de `diario/`.
4. Ler os arquivos das áreas que a tarefa do dia toca.
5. Alinhar qualquer recomendação com `01-negocio/principios.md` — são regras fixas. Se uma tarefa conflitar com um princípio, apontar o conflito antes de prosseguir.

## Fim de sessão (obrigatório)

1. Atualizar os arquivos de área afetados (editar, nunca duplicar).
2. Criar entrada em `diario/` a partir de `diario/TEMPLATE.md` (`AAAA-MM-DD-assunto.md`).
3. Atualizar a seção "Estado atual" do `README.md` se fase, meta ou frente de trabalho mudaram.
4. Commit com mensagem descritiva em português (`docs:` para conhecimento, `feat(area):` quando fizer sentido). Push quando houver remoto.

## Regras do repositório

- Versionar tudo — não existe `.gitignore` aqui de propósito.
- Português brasileiro em todo o conteúdo.
- Os arquivos `.md` são a fonte da verdade; binários em `arquivos/` são derivados deles.
- Decisões nunca são apagadas — são revertidas com uma nova entrada no diário explicando o porquê.
- Decisões importantes levam a data no título: `(decisão AAAA-MM-DD)`.
- O código do app NÃO mora aqui. O app vive em `J:\Projetos\lume` (repo próprio). Aqui ficam visão, negócio, produto, design e decisões técnicas de alto nível.

## O que o Felipe valoriza

- Racionalidade com propósito: toda recomendação vem com o porquê e, quando possível, com números.
- Ele é dev de software — soluções automatizáveis são bem-vindas.
- O Lume nasce de uma dor real dele (impaciência, imediatismo, inconsistência). O produto existe para construir constância — o KB deve proteger o projeto do próprio imediatismo: antes de sugerir mudar de rota, checar o roadmap e os princípios.
