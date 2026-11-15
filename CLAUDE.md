# Lorenzo Kart

Jogo de kart 3D em um único arquivo (`index.html`, Three.js r170 como módulo via importmap + Supabase), publicado no GitHub Pages:
https://smduarte1977.github.io/lorenzo-kart/

- `index.html` = versão 2.0 (gráfico em alta definição, níveis fácil/médio/difícil).
- `v1/` = versão 1 antiga e leve (Three.js r128), mantida para celulares fracos. Tem o próprio `v1/version.json`.

## Ao publicar qualquer mudança
- Aumente `GAME_VERSION` em `index.html` **e** o número em `version.json` (os dois iguais).
  Isso faz aparecer o botão "Nova atualização" para quem já tem o jogo aberto ou instalado.
- Servidor (recordes/nomes): projeto Supabase `lorenzo-kart` (funções `register_player`, `submit_result`, `leaderboard`, `top_wins`).
- Online usa Supabase Realtime (canal `kart-room-<código>`), sem tabelas. Mensagens de votação: `vote` (pista) e `dvote` (nível); `start` leva `diff`.
