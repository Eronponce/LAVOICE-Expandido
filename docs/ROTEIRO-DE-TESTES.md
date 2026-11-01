# Roteiro de reprodução

Abra ABRIR-LABORATORIO.bat. Use o seletor de mapas, a câmera livre e o campo Pedido de teste. O laboratório usa material de teste ilimitado e inicia sem voz. Para avaliar recursos, competição, voz ou rede, use o Mod 4 normal.

| Área | Teste manual | Resultado a conferir |
| --- | --- | --- |
| Mapas | Percorra Original, Tokyo 3, Espaço e TD; use F8 e a vista de cima. | Sem buracos inesperados, peças faltando ou câmera cortando o cenário. |
| Spawns | Entre como jogador, ande perto dos seis pontos de nascimento. | Sem nascer preso em paredes ou cair através do chão. |
| Interiores | Explore portas, corredores e escadas dos edifícios de Tokyo 3. | Escala suficiente para o personagem e ausência de colisões invisíveis. |
| Estruturas | Peça casa completa, casa de 3 andares, ponte de aço, fortaleza, prisão e labirinto. | Planta, dimensões e material correspondem ao pedido. |
| Tamanhos | Compare casas de 3 x 3 x 3 e 24 x 18 x 28, com 1 e 3 andares. | Sem dimensões negativas, escadas vedadas ou peças desconectadas. |
| Montagem | Confirme uma casa; acompanhe em 0,25x e com a câmera livre. | Peças chegam à posição final e a construção termina. |
| Destruição | Ataque parede, piso e torre até perderem vida e desaparecerem. | Peças removidas deixam de bloquear; não há forma invisível restante. |
| Efeitos | Combine fogo, gelo, eletricidade, explosões e projéteis divididos. | Sem travamento ou multiplicação ilimitada de entidades. |
| Inventário | Faça duas armas, depois complete os seis espaços e faça a sétima. | Slot livre primeiro; inventário cheio substitui somente o selecionado. |
| Confirmação | Proponha algo e recuse; confirme outra criação. | A recusa não cria objetos; confirmar não dispara a arma anterior. |
| Fila | No Mod 4 normal, deixe um pedido sem material na fila e tente outro. | Fila comporta um; não há cobrança dupla ao receber recursos. |
| Animais | Invoque lobos, gatos e pombos perto de degraus, paredes e rampas. | Perseguição acompanha altura e desvia; registre locais onde ficam presos. |
| Veículos | Crie carro, moto e tanque; monte e desmonte perto de paredes. | Câmera, colisão e saída do veículo funcionam; consulte o catálogo de controles. |
| Terreno | No Sandbox normal, faça cratera, gelo, fogo, lava e terremoto em regiões distintas. | Alcance respeita a área; efeitos não ficam ativos após a limpeza. |
| Espaço | Troque de planeta, caminhe perto das paredes e use voo/gravidade. | Orientação acompanha a superfície; sem ficar preso entre gravidades. |
| Tower Defense | Construa torres em bases válidas e inválidas e inicie ondas. | Inimigos nascem nas quatro rotas e torres reconhecem alvos. |
| TD compartilhado | No Mod 4 normal com aliados, confirmem pedidos com saldo apertado. | Saldo comum nunca fica negativo e cada pedido aceito cobra uma vez. |
| Competição | Teste renascimento, proteção, pontos e quebra do núcleo. | Regras e placar coincidem em todos os clientes. |
| Caos | No modo competitivo normal, compare armas comuns e criações nucleares com nomes diferentes. | Custo depende dos efeitos; orbe só pode ser coletado uma vez. |
| Drops | Solte sete armas e deixe outras no chão; exploda uma delas. | Limpeza respeita armas na mão, tempo e limite; item destruído não reaparece. |
| Eventos | Ative meteoros, furacão e noite em partida de teste. | Eventos terminam e não deixam efeitos sem limite. |
| Estabilidade | Troque de mapa dez vezes e repita o mesmo cenário após aquecer os caches. | Sem crescimento contínuo de objetos após a limpeza ou queda progressiva de FPS. |
| Rede | No Mod 4 normal, use seis jogadores em máquinas diferentes, com host saindo e clientes reconectando. | Construção, dano, pontuação e recursos concordam; latência real ainda precisa de teste. |
| Voz | No Mod 4 normal, teste microfone e frases com ruído e sotaques. | Interpretação aparece antes de criar; voz dos aliados permanece na preferência escolhida. |

## Como registrar

1. Anote o pedido exato e os passos até o problema.
2. Use F1 para abrir o painel e escreva a descrição no campo de relato.
3. Clique em Registrar bug + imagem ou pressione F9.
4. Guarde a pasta Diagnosticos/data-hora e ultimo-laboratorio.log.
5. Acrescente esperado, ocorrido, frequência e se acontece em outro mapa.

O relatório salva imagem, câmera, regras, inventário, pedido pendente e estado da partida. Ele não é um salvamento completo do terreno destruído. Para problemas que dependem de várias modificações, inclua os passos e pedidos na descrição.

A galeria mantém as amostras paradas para estudar modelos e formas de colisão. Para testar IA, armas disparando, veículos e montagem real, use Pedido de teste no mundo. Em testes competitivos e de rede, preserve também o log do host e do cliente.

## Cobertura entregue

A rodada gráfica percorre 4 mapas, 9 ângulos por mapa, 24 spawns, 119 estruturas fixas por verificações de dados, 16 vistas dos 8 planetas, 8 interiores da cidade e 28 modelos em três ângulos. Também verifica portas, pisos e paredes de casas, remoção de colisões por dano e uma onda TD com sete tipos de torre.

São 638 verificações automatizadas da auditoria e 29 da interface. Essa cobertura não esgota combinações livres de linguagem, mapas deformados, IA em labirintos, voz e partidas pela internet. O Playwright não executou neste ambiente (falha do parser do RTK); a interface foi verificada diretamente no executável Godot, com eventos de mouse e capturas reais.
