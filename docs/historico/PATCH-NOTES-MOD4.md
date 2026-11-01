# LAVOICE Expandido — Mod 4

## Tower Defense cooperativo
- Até seis jogadores no mesmo time, defendendo um núcleo central.
- Mapa próprio com praça circular, quatro rotas curvas de invasão e 24 pontos demarcados para torres.
- Animais terrestres e voadores surgem por ondas, com dificuldade crescente e um chefe a cada cinco ondas.
- Padrão: 10 ondas, 20 segundos de preparação e um animal a cada 0,8 segundo. F4 permite ao anfitrião iniciar a próxima onda durante a preparação.
- Vitória ao vencer a última onda; derrota se o núcleo cair. Jogadores renascem com a proteção configurada.
- O grupo começa com **300 materiais compartilhados**. Cada animal eliminado concede **3**; cada onda vencida concede **80**. Saldo limitado a 9.999.
- Material inicial, recompensas, intervalo de spawn, preparação, ondas e vida do núcleo podem ser alterados em F3 pelo anfitrião.
- Extração do cenário, créditos de reciclagem e espólios de morte não repõem esse saldo. As rotas ficam protegidas da escavação e destruição.
- Torres só podem ocupar pontos livres, uma por ponto, no tamanho padrão; aliados não danificam o núcleo nem as defesas amigas.
- Tipos de torre: metralhadora, fogo, gelo, elétrica, canhão, sniper e veneno. Elas miram e disparam automaticamente, respeitando o alcance.
- A troca de modo online preserva a sessão e aguarda a retirada dos objetos antigos antes de carregar o novo mapa.

## Confirmação de criações em todos os modos
- Novos pedidos de armas, objetos, criaturas, estruturas e habilidades abrem uma prévia antes da criação.
- Um painel central mostra o que o jogo entendeu, o preço em materiais, o saldo disponível e o motivo quando não é possível construir.
- **Botão esquerdo:** aceitar e construir. **Direito:** recusar, sem gastar. **Meio:** colocar na fila.
- A fila tem **uma posição por jogador**. Ela aguarda material e o término da montagem atual. Backspace cancela o pedido enfileirado.
- O preço mostrado é mantido no pedido enfileirado. O host valida novamente saldo, posição e limites ao executá-lo.
- O material é debitado uma única vez ao iniciar a criação; a animação continua mesmo que o saldo chegue a zero. Dois aliados não podem gastar o mesmo saldo.
- O clique de confirmação é consumido pelo painel e não dispara a arma atual.
- Compras enfileiradas não apagam uma prévia diferente aberta depois.
- Interações como pegar, largar, montar e comandos de edição continuam diretas. Spawns automáticos e projéteis das armas também não pedem confirmação.

## Inventário e voz
- Uma criação de arma usa primeiro um espaço livre e mantém a arma atual selecionada.
- Se os seis espaços estiverem cheios, ela substitui somente o espaço selecionado; a arma anterior é largada quando há capacidade.
- A conversa por voz entre jogadores vem silenciada por padrão, incluindo envio e reprodução. O reconhecimento de voz para criar continua disponível com o modelo original.
- F3 permite desmarcar a opção de silenciar a conversa. A preferência é local e persistente.
- Dicas atualizadas: agora são **291** exemplos e orientações.

## Perseguição e desempenho
- Animais testam colisões para subir degraus pequenos, tentam desvios laterais e saltam ao encontrar obstáculos ou ficarem presos. As hordas seguem pontos das rotas até o núcleo.
- A perseguição usa consultas do corpo físico antes de subir; a implementação se apoia no teste de movimento da [API oficial do Godot](https://docs.godotengine.org/en/stable/classes/class_physicsbody3d.html#class-physicsbody3d-method-test-move).
- Aquisição de alvos limitada a cinco atualizações por segundo por perseguidor; a lista de candidatos é compartilhada por passo de física.
- Modelos de animais com a mesma geometria reaproveitam as malhas, mesmo quando mudam vida ou rota. Avaliações de Caos também têm cache limitado.
- Máximo de 32 animais simultâneos; o restante da onda aguarda vaga. A rede reserva espaço para criações e projéteis, e atingir esse limite não pausa os inimigos já ativos.
- Ao atingir o limite de objetos, projéteis antigos são removidos antes das construções. Ao terminar o Tower Defense, inimigos e torres deixam de agir.

## Verificação
- **7.717 verificações de regressão**, **206 de recursos anteriores** e **59 novas** passaram no motor nativo: **7.982 verificações locais**.
- Teste com anfitrião e cinco clientes: revisão e confirmação remotas, fila, saldo compartilhado, arma em espaço livre, torre, ondas e mudança de mapa passaram nos seis processos. Foram 245 verificações de rede.
- No cenário de 120 passos simulados da perseguição, foram 10 atualizações de alvo, contra 120 no caminho anterior: aproximadamente 92% menos atualizações nesse trecho. Isso não representa ganho medido de FPS.
- Playwright foi tentado e não iniciou neste ambiente. A verificação usou o Godot nativo em modo headless.
- Ainda é necessário testar sensação de jogo, imagem e latência com amigos em computadores diferentes. O desvio dos animais é local; labirintos fechados ou obstáculos muito grandes ainda podem exigir outra rota.

Todas as pessoas precisam usar o mesmo Mod 4. Mod 3 e seus arquivos originais foram preservados.
