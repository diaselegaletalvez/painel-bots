# painel-bots

Painel de controle dos bots da Dias Inc.

- `index.html` — o painel (GitHub Pages)
- `data/bots.json` — lista de slugs dos bots ativos
- `data/bots/<slug>.json` — estado atual de cada bot

Cada bot escreve **só no próprio arquivo**. Nunca em `bots.json` nem no de outro bot.

## Schema de `data/bots/<slug>.json`

| campo | tipo | regra |
|---|---|---|
| `slug` | string | igual ao nome do arquivo |
| `nome` | string | nome do bot |
| `projeto` | string | o que ele toca |
| `status` | enum | `trabalhando` \| `esperando_voce` \| `bloqueado` \| `concluido` \| `parado` |
| `resumo` | string | 1 frase, em português, o que foi feito na última execução |
| `proximo_passo` | string | 1 frase, o que vem agora |
| `bloqueio` | string \| null | se `status` for `bloqueado` ou `esperando_voce`, explicar o que o Dias precisa fazer |
| `progresso` | 0–100 | % do objetivo do bot |
| `atualizado_em` | ISO 8601 | com fuso `-03:00` |
| `eventos` | array | mais recente primeiro, máx. 20, `{ "quando": ISO, "texto": string }` |
