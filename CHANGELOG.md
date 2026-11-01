# Histórico do LAVOICE Expandido

## Mod 4 e laboratório — 2026-11-01

Release cumulativa do LAVOICE Expandido, do H4 original ao conteúdo atual. O jogo original é de Tsomyst; Expandido é uma modificação comunitária não oficial. Esta publicação mantém o jogo normal e o laboratório como pacotes separados.

### O que já existia no H4 original

- Criação por voz e texto, extração de matéria, montagem de objetos e destruição do cenário em blocos.
- Treino, duelo e multiplayer por IP/rede local, originalmente para até quatro pessoas.
- Arena Original, Espaço e Tokyo 3. O mapa de Tower Defense é adição do Expandido.
- Motor Godot 4.7.2, renderização DirectX 12 na GPU e reconhecimento de voz offline original. O reconhecimento não foi substituído por outro modelo nem convertido para GPU nesta entrega.

### Mod 1 — primeira expansão

- Cura, regeneração, salvaguarda, visão noturna, campo de visão ampliado, velocidade, pulo, voo, jetpack e modo escavador; vida máxima limitada a 150.
- Veículos dirigíveis, incluindo carro e helicóptero, e combinação de armas/projéteis como katanas explosivas, canhão de plasma e pombos teleguiados explosivos.
- Criaturas que seguem o dono e variações de tamanho até 10×; ponte, escada, plataforma e abrigo.
- Modelo de voz e motor originais preservados. A primeira entrega registrou 112 verificações no executável.

### Mod 2 — catálogo, física e personalização

- Catálogo ampliado naquela versão para 248 tipos e variações de criações, 24 vestíveis e 1.600 receitas nomeadas. São combinações e modelos próprios/adaptados, não 1.600 modelos independentes.
- Até 13 elementos combináveis, herança dos elementos pelos projéteis e reações entre fogo, gelo, água, choque, veneno, terra, vento, luz, sombra e gravidade.
- Física arcade, impulso, quique, montaria, raios encolhedor/ampliador, antigravidade, trator, repulsor, estase, vórtice, super força e magias.
- Mais construções e vida/barra de HP nas construções invocadas, com remoção pela mira e destruição por dano.
- Armaduras, capas, botas e elmos com efeitos; nicks sincronizados, minimapa e tom da cor do invocador.
- Limites ampliados de 40 para 80 entidades por jogador e de 128 para 256 entidades online.

### Mod 3 — seis jogadores, estruturas e competição

- Lobby, transporte, spawns, inventário, minimapa e perfis preparados para até seis jogadores. Inventário com seis espaços e personalização adicional de robôs.
- Sandbox, Corrida de Eliminações com renascimento/placar e Invasão de Bases, com até 3 contra 3 e núcleos que controlam o renascimento.
- Caos de 0 a 100, orbes disputados, raridades opcionais e cobrança pelo poder composto da receita, incluindo suas cargas e projéteis. Um nome inocente não remove o custo de um efeito nuclear.
- Construção de casas, torres, pontes, fortalezas, prisões, labirintos e caixas de paredes, com material, dimensões e até três andares. Casas completas incluem móveis cenográficos e plantas limitadas a até 112 peças.
- Edição contextual de criações próprias, regiões de terreno, fogo progressivo, lava, gelo, crateras, terremotos, montanhas e regeneração opcional do mapa.
- Eventos opcionais de furacão, meteoros e noite; teletransporte, invisibilidade e escudo de energia.
- Até quatro armas procedurais no mapa; pegar, largar, compartilhar e limpar drops por tempo/limite, sem remover armas que continuam na mão.
- Favoritos, histórico, desfazer limitado e oficina F3 para regras/perfil. Todos os modos futuros mencionados nas ideias não foram implementados: Apocalipse, Rei da Colina e fase separada de preparação de bases continuam fora desta versão.

### Mod 4 — Tower Defense e confirmação de criações

- Tower Defense cooperativo para até seis pessoas, com núcleo central, quatro rotas curvas, 24 pontos para torres, animais terrestres/voadores e chefes a cada cinco ondas.
- Sete torres automáticas: metralhadora, fogo, gelo, elétrica, canhão, sniper e veneno. Máximo de 32 inimigos simultâneos; os restantes aguardam vaga.
- Saldo compartilhado de 300 materiais por padrão; +3 por animal e +80 por onda vencida. Regras de ondas, recompensas, preparação e núcleo configuráveis pelo anfitrião. Extração e reciclagem não repõem esse saldo.
- Prévia global para novas armas, criaturas, objetos, estruturas e habilidades, com interpretação, preço, saldo e motivo de bloqueio visíveis.
- Botão esquerdo confirma; direito recusa sem gastar; meio guarda um pedido na fila de uma posição. Backspace cancela a fila. Cobrança única ao iniciar a criação e revalidação pelo host ao executar a fila.
- Nova arma ocupa primeiro um espaço livre e mantém a seleção atual. Com os seis espaços cheios, substitui somente o selecionado, largando a anterior quando há capacidade.
- Conversa por voz silenciada por padrão, com preferência local em F3. O reconhecimento de voz para criar continua disponível no jogo normal.
- Perseguição com consultas físicas para pequenos degraus, saltos e desvios locais; aquisição de alvos a 5 Hz, candidatos compartilhados por passo de física e caches limitados de geometria/Caos.
- Troca de modo online preserva a sessão e aguarda a remoção dos objetos antigos antes do novo mapa. Evicção prioriza projéteis antigos antes das construções.
- 291 dicas de criatividade e uso na interface.

### Laboratório mod4-lab1 — depuração separada

- Câmera livre, nove vistas por mapa, seleção dos quatro mapas, pausa e câmera lenta.
- Galeria de 28 modelos: 12 construções e 16 amostras de animais, veículos, armas e poderes, com enquadramento adequado ao tamanho.
- Formas de colisão por objeto, teste de pedidos por texto e registro de bugs com imagem, câmera, regras, inventário, pedido pendente e estado da partida.
- Auditoria gráfica/física automatizada e relatório HTML com filtros: 191 imagens da auditoria mais quatro imagens dos controles, em 1280 × 720.
- Corrigidos na ferramenta: câmera dentro do personagem nas capturas dos spawns, armas pequenas longe do enquadramento, colisões retiradas ao congelar amostras e título sobreposto ao painel.
- O laboratório inicia **offline, com materiais de teste ilimitados e sem voz**. Use o Mod 4 normal para partidas com amigos, economia, Caos e reconhecimento de voz. As amostras da galeria ficam paradas; comportamento real é testado no mundo.

### Documentação e distribuição

- Pacotes completos para Windows do jogo atual e do laboratório; H4 original mantido como referência.
- Documentação para Obsidian com visão geral, arquitetura, implementação, comandos, testes e publicação.
- Créditos e avisos de terceiros preservados nos pacotes.
- **Compatibilidade:** todos os participantes precisam do mesmo ZIP Mod 4. Mod 2, Mod 3, laboratório e versão oficial não substituem esse pacote em partidas compartilhadas.

### Evidência e limites

- Jogo Mod 4: **7.982 verificações locais** no motor nativo, sendo 7.717 de regressão, 206 de recursos anteriores e 59 novas.
- Rede Mod 4: **245 verificações** em um anfitrião e cinco clientes na mesma máquina, incluindo prévia, confirmação, fila, orçamento compartilhado, torres, ondas e troca de mapa.
- Laboratório: **667 verificações aprovadas**, sendo 638 da auditoria e 29 dos controles, sem erros nos logs finais.
- Estes resultados não garantem ausência de bugs. Internet/latência entre computadores, voz, navegação em labirintos fechados e todas as combinações livres ainda exigem testes adicionais. Os móveis são cenográficos e a física usa aproximações arcade.
- Playwright foi tentado, mas o parser do RTK falhou; as verificações alternativas usaram o Godot nativo, inclusive eventos de mouse e capturas reais na etapa do laboratório.
- A redução de consultas de alvo foi observada em um cenário simulado; não é uma medição de ganho de FPS em partida.

**Release:** https://github.com/Eronponce/LAVOICE-Expandido/releases/tag/mod4

**Histórico do repositório:** https://github.com/Eronponce/LAVOICE-Expandido/compare/mod2...mod4 — os commits deste repositório registram documentação/distribuição, não o histórico completo do desenvolvimento interno.

---

## Registro anterior preservado

# LAVOICE H4 — Expandido Mod 2

Atualização de 31/10/2026, a partir do Expandido Mod 1.

## Conteúdo novo

- 248 tipos e variações de criações: 64 animais, 48 construções, 64 armas, 16 veículos, 24 projéteis, 14 ferramentas de física, 16 magias e 2 punhos especiais.
- 24 vestíveis, com armaduras, capas, botas e elmos.
- 1.600 receitas nomeadas que combinam esses tipos com temas elementais. São combinações prontas; os 248 tipos têm modelos próprios ou modelos do jogo adaptados.

## Efeitos que combinam

- Até 13 elementos juntos: laser, fogo, gelo, choque, veneno, ácido, água, vento, terra, luz, sombra, gravidade e plasma.
- Os projéteis herdam os elementos da arma. Cor, tamanho, velocidade, blindagem, peso, precisão e cadência podem acompanhar os elementos.
- Fogo + gelo: choque térmico. Água + choque: eletrocussão. Veneno + fogo: combustão tóxica. Terra + gelo: cristalização.
- Fogo + vento: tempestade de fogo. Sombra + luz: eclipse. Choque + gelo: geada elétrica. Gravidade + vento: pressão gravitacional.
- Mais rápido, mais devagar, preto e pegando fogo podem ser usados no mesmo pedido, conforme o objeto e o efeito.

## Física e montaria

- Montaria em criações suas próximas: animais, móveis, veículos, armas colocadas no mundo e construções. Use F para montar e sair.
- Acrescente montável para colocar no mundo uma criação que normalmente iria para a mão.
- Acrescente com física para habilitar peso, gravidade, colisões, quique e transferência de impulso. A simulação é uma física arcade; a rotação visual usa colisores simples.
- Raio encolhedor e ampliador alteram o modelo e as colisões, mantendo o tamanho entre 0,3× e 10×.
- Arma antigravidade, repulsor, raio trator, estase e vórtice, com versões que combinam esses efeitos.
- Super força entrega um punho para golpear e empurrar objetos; o punho terremoto combina impacto e elementos.

## Construções

- Casas, cabanas, castelos, fortalezas, pontes, rampas, escadas, hangares, garagens, mirantes, túneis, labirintos e arenas.
- Fábrica, usina, central elétrica, estação espacial, templo, torre de mago, aeroporto, biblioteca, estádio, estacionamento, aqueduto, escadaria em espiral, pirâmide, zigurate e planetário.
- Todas as construções invocadas têm vida, número de HP e barra. Podem ser destruídas por dano.
- Remover construção ou demolir remove uma construção sua próxima na mira.

## Personagens e interface

- Armaduras de fogo, gelo, eletricidade, pedra, plasma e fogo com gelo; trajes antitóxico, tempestade e escavador.
- Capas, botas e elmos com proteção, regeneração, velocidade, pulo e gravidade reduzida. Um vestível por posição do corpo; posições diferentes combinam.
- Vestíveis duram 180 segundos e têm custo em matéria. Remover efeitos também tira seus bônus.
- Vida máxima do jogador continua em 150.
- Invocações recebem um tom da cor de seu dono.
- Nick acima dos jogadores, com sincronização pela rede. F2 abre a troca de nick, com até 20 caracteres.
- Minimap no canto superior direito com posições, nomes e criações por cor. M mostra ou oculta.

## Limites e multiplayer

- Limite por jogador: de 40 para 80 entidades.
- Limite global online: de 128 para 256 entidades.
- Todos devem usar o mesmo ZIP Mod 2. O jogo impede a mistura com Mod 1 ou versões oficiais.
- Partidas por IP/rede local/Radmin VPN, 2 a 4 pessoas, UDP 27840, como na versão anterior.

## Conferência desta entrega

- 7.690 verificações passaram tanto no projeto quanto no executável com o motor original.
- Duas instâncias do executável conectaram entre si e sincronizaram os nicks.
- Playwright indisponível neste ambiente; a validação automática foi feita no próprio jogo. O teste visual e a conexão entre computadores diferentes ficam para o uso real.
- Voz original offline mantida. Créditos e licenças originais acompanham o pacote.
