# LAVOICE Expandido — Mod 3

## Jogue com até seis pessoas
- Lobby, transporte, validação da sessão, spawns, nomes, minimapa e inventário preparados para seis jogadores.
- Duelo por rodadas preservado. Sandbox livre e dois modos competitivos disponíveis na oficina (F3).
- Invasão de Bases: duas equipes equilibradas, até 3 contra 3. Construa defesas, invada a base rival e destrua o núcleo. Sem núcleo, a equipe deixa de renascer; vence a última equipe restante.
- Corrida de Eliminações: objetivo configurável, placar de eliminações/mortes, equipes opcionais, renascimento automático e proteção temporária.

## Caos e defesa
- Barra de 0 a 100, orbes anunciados e marcados no minimapa. Padrão: a cada 60 segundos, +25 pontos, expiração em 30 segundos.
- Raridades opcionais: comum +15, raro +35 e lendário +75. Eliminações podem dar Caos.
- Custo calculado pelos atributos e comportamentos montados, incluindo projéteis, explosões, cadência, canos, anexos e cargas escondidas. Trocar o nome de uma criação não altera seu poder nem evita a cobrança.
- Poderes nucleares chegam a 100 de Caos. Intervalos, recompensas, raridades, custo nuclear e multiplicador de poderes especiais podem ser ajustados pelo anfitrião.
- Construções competitivas têm resistência e limite de dano por impacto: um tiro ou uma única explosão não apagam o prédio. Partes se desprendem visualmente e deixam de bloquear a passagem conforme a vida cai.

## Construção por voz
- Casas, torres, pontes, fortalezas, prisões, labirintos e caixas de paredes ao redor do jogador.
- Dimensões, até três andares, madeira, tijolo, pedra, aço, vidro e gelo. Entradas, janelas e escadas deixam passagem pelo interior.
- Casas completas mobiliadas incluem cama, colchão, travesseiro, guarda-roupa, bancada, pia, fogão, geladeira, sofá, mesa, cadeiras, vaso sanitário, chuveiro, luz e estante.
- Móveis são peças de cenário. A distribuição foi organizada por quarto, cozinha, sala, banheiro e armazenamento, tomando como referência as categorias de cômodos e móveis da [IKEA](https://www.ikea.com.tw/en/rooms).
- Casas mobiliadas usam no mínimo 8 × 8 metros para acomodar os móveis. Planos têm limites de dimensões e até 112 peças para proteger o desempenho.
- Mire em criações próprias para duplicar, ampliar, reduzir, trocar material, adicionar efeitos ou ordenar que uma criatura proteja a base.
- Marque uma região e mova uma criação até ela. Sem marca, a criação vem para perto de você.

## Terreno, eventos e poderes
- Marque o início de uma região com a mira e escolha o fim. Fogo se espalha progressivamente; gelo e lava alteram a superfície e criam perigos temporários.
- Crateras, terremotos e montanhas. Regeneração automática de terreno opcional.
- Furacão, chuva de meteoros e noite podem ocorrer aleatoriamente, com aviso global. Desligados por padrão; ative em F3.
- Teletransporte curto, invisibilidade e escudo de energia. Portais, armas de física e combinações de elementos das versões anteriores continuam disponíveis.
- Montagem ampliada para criações livres de outros jogadores também; núcleos, objetos segurados, projéteis e montarias já ocupadas ficam fora dessa interação.

## Armas no mapa e compartilhamento
- Até quatro armas procedurais aparecem em lugares aleatórios; as vagas são repostas periodicamente.
- Milhares de combinações de nomes, com projéteis, movimento, ricochete e elementos sorteados de verdade. O nome aparece sobre a arma.
- E: pegar uma arma próxima. G: largar a arma atual para outro jogador.
- Armas poderosas geradas no mapa cobram Caos ao serem recolhidas. Armas que já foram pagas e depois compartilhadas não cobram novamente.
- Drops recebem física e desaparecem se atingidos por uma explosão. Expiram após 90 segundos por padrão.
- Limite padrão de seis drops por pessoa: ao largar o sétimo, o mais antigo que continua no chão é removido. Armas na mão ficam fora dessa limpeza.
- Inventário ampliado para seis espaços, selecionáveis pelas teclas 1 a 6.

## Oficina e criatividade
- Menus ampliados, seis robôs no lobby, nick individual, cores e pinturas existentes, mais coroa, antena, halo e cartola.
- F3 abre perfil e regras. Alterar regras durante uma partida reinicia a partida ao aplicar. Clientes podem mudar o perfil; regras online são exclusivas do anfitrião.
- 284 dicas diferentes alternam a cada 13 segundos no canto superior direito, abaixo do minimapa.
- Favoritos por nome, histórico de comandos na interface e desfazer com histórico limitado. Desfazer remove a criação mais recente ou reverte um movimento/região registrado; não devolve recursos nem reverte dano em jogadores.

## Verificação e limites desta versão
- 7.696 verificações de regressão e 206 verificações novas passaram no motor nativo.
- Teste local com um anfitrião e cinco clientes: seis jogadores, dois núcleos, quatro armas, construção mobiliada e orbe sincronizados; pegar e largar arma remotamente também passaram.
- Playwright foi tentado e não iniciou neste ambiente; a validação usou o Godot nativo. O teste de rede foi na mesma máquina, sem ensaio de latência pela internet ou inspeção visual manual de uma partida completa.
- A interpretação usa padrões de português e o catálogo do jogo; não entende toda frase imaginável. Use os exemplos incluídos.
- Pinturas persistem pelo sistema original. Favoritos do anfitrião/local persistem; os de clientes remotos valem para a sessão.
- O terreno conserva a destruição em blocos original; novas construções compostas quebram por partes. Eletrodomésticos são cenográficos.
- Modos Apocalipse, Sobrevivência, Rei da Colina e fase separada de preparação de bases continuam fora desta versão.
- Modelo de voz original mantido. Todos precisam usar o mesmo Mod 3 para entrar na sessão.
