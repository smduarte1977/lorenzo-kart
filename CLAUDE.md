# Lorenzo Kart

Jogo de kart 3D em um único arquivo (`index.html`, Three.js r128 + Supabase), publicado no GitHub Pages:
https://smduarte1977.github.io/lorenzo-kart/

## Ao publicar qualquer mudança
- Aumente `GAME_VERSION` em `index.html` **e** o número em `version.json` (os dois iguais).
  Isso faz aparecer o botão "Nova atualização" para quem já tem o jogo aberto ou instalado.
- Servidor (recordes/nomes): projeto Supabase `lorenzo-kart` (funções `register_player`, `submit_result`, `leaderboard`, `top_wins`).
- Online usa Supabase Realtime (canal `kart-room-<código>`), sem tabelas.
