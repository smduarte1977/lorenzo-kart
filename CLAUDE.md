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

## Contas, pais e app (versão 17)
- Senha do piloto fica no servidor (bcrypt): `set_password`, `login_player` (aparelho novo ganha token próprio em `player_tokens`), `save_progress`, `player_status`.
- O aparelho lembra a senha da criança (`lorenzoKart_users`); tocar no piloto salvo entra direto. "Remover deste aparelho" tira só do celular.
- Pais: no jogo, botão PAIS gera código de 6 números (30 min) via `get_link_code`; painel em `pais/` cria a conta `<piloto>_pais` (`parent_create`) e entra sempre com senha (`parent_login`, sessão só na memória, 8 h).
- Registros (90 dias): `log_join`/`log_leave`/`log_event` (emoji, mic_on, mic_off) e corridas em `submit_result`. Voz não é gravada; `parent_set_voice` bloqueia o áudio do filho.
- App instalável (PWA): `manifest.json` + `sw.js` (rede primeiro). Painel dos pais tem `pais/manifest.json` e `pais/sw.js`.
