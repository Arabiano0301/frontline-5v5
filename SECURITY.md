# Política de segurança

O Frontline 5v5 é um jogo estático: roda inteiro no navegador, não tem servidor próprio e guarda o progresso
apenas no `localStorage` do aparelho.

## Dependências externas

| O quê | De onde | Quando |
|---|---|---|
| **Three.js r128** | `cdnjs.cloudflare.com` (versão fixa) | sempre |
| **PeerJS 1.5.4** | `cdnjs.cloudflare.com` (versão fixa) | só ao abrir o multijogador |
| Servidor público de salas | `0.peerjs.com` | só ao criar ou entrar numa sala |

O servidor de salas só apresenta os aparelhos uns aos outros. Depois disso, os dados da partida trafegam
direto entre os jogadores via WebRTC. O código da sala é a única forma de entrar nela.

Uma melhoria possível é baixar os dois arquivos do `cdnjs` para o repositório e carregá-los localmente.

## Proteções no jogo

- O `index.html` traz uma **Content-Security-Policy**: scripts só do próprio arquivo e do `cdnjs`, e conexões só com o servidor de salas.
- No multijogador, o anfitrião executa a partida e valida o que recebe: nomes, mensagens de chat, emblemas,
  títulos e operadores são limitados em tamanho e conferidos contra listas conhecidas. Todo texto vindo de
  outros jogadores é exibido como texto, nunca como HTML.
- Nenhum dado é enviado para fora do jogo, a não ser o que vai para os outros jogadores da mesma sala
  (nome, emblema, título, operador, posição e ações na partida).

## Reportar um problema

Encontrou um problema? Abra uma [issue](../../issues) sem detalhes sensíveis ou use
**Security → Report a vulnerability** neste repositório.
