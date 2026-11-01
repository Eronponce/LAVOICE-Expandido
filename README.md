# LAVOICE H4 — Expandido

Expansão comunitária não oficial do LAVOICE H4, jogo original de Tsomyst. Crie por voz ou texto, construa, combine efeitos e jogue com até seis pessoas.

## Distribuição

A distribuição pública dos pacotes executáveis foi suspensa em 1º de novembro de 2026. Os ZIPs completos do LAVOICE original, do Mod 2, do Mod 4 e do Laboratório foram removidos das releases. **Nenhum executável ou patch do mod está disponível neste repositório neste momento.**

Para obter o LAVOICE H4 original, use a [página oficial de Tsomyst](https://tsomyst.itch.io/lavoice). As releases mantêm apenas documentação e notas históricas; o ZIP LAVOICE-Obsidian contém documentação, não o jogo.

## O que a expansão oferece

- Até seis jogadores, nicks, minimapa, cores, acessórios de robô e inventário de seis espaços.
- Sandbox, Corrida de Eliminações, Invasão de Bases até 3 contra 3 e Tower Defense cooperativo.
- Estruturas por dimensões, materiais e andares, casas mobiliadas, mais animais, veículos, armas, vestíveis e magias.
- Elementos combináveis, raios de escala e gravidade, montaria e física arcade.
- Caos competitivo calculado pelo poder composto da criação, com orbes disputados.
- Armas procedurais pelo mapa, drops compartilháveis, favoritos, histórico e desfazer limitado.
- Prévia visível do pedido, preço e saldo antes de criar. Uma posição de fila por pessoa.
- 291 dicas de criatividade e uso. Gráficos D3D12 na GPU; o modelo original de reconhecimento de voz continua na CPU.

O H4 original já incluía criação por voz/texto, matéria, montagem, destruição em blocos, renderização na GPU e os mapas Original, Espaço e Tokyo 3. [O histórico cumulativo](CHANGELOG.md) distingue essas funções das adições dos Mods 1 a 4.

## Controles rápidos

| Controle | Função |
| --- | --- |
| T | Digitar um pedido |
| V segurado | Criar por voz |
| V rápido | Alternar extração de matéria |
| Clique esquerdo na prévia | Confirmar criação |
| Clique direito na prévia | Recusar sem gastar |
| Clique do meio na prévia | Guardar um pedido na fila |
| Backspace | Cancelar a fila |
| 1 a 6 | Selecionar espaço do inventário |
| E / G | Pegar / largar arma |
| F | Montar / sair de uma criação livre próxima |
| F2 / M | Alterar nick / mostrar minimapa |
| F3 | Perfil e regras; anfitrião altera a partida |
| F4 no TD | Anfitrião inicia a onda durante a preparação |

Exemplos: quero casa completa de 3 andares; quero laser de fogo e gelo; quero pombo teleguiado explosivo; quero raio encolhedor; quero carro montável. A interpretação combina padrões de português com o catálogo; não entende qualquer frase imaginável.

## Tower Defense

Até seis aliados defendem um núcleo. O mapa possui quatro rotas e 24 pontos para sete tipos de torre. O padrão começa com **300 materiais compartilhados**, recompensa **3 por animal** e **80 por onda vencida**; extração e reciclagem não repõem esse saldo. Há até 32 inimigos simultâneos. Regras são configuráveis em F3.

A conversa entre jogadores inicia silenciada, com preferência local em F3. O reconhecimento de voz para pedir criações continua disponível no jogo normal.

## Documentação no Obsidian

[**Navegar pelo índice da documentação**](docs/Obsidian/LAVOICE/00%20-%20Comece%20aqui.md)

Baixe LAVOICE-Obsidian.zip, extraia e abra a pasta LAVOICE como cofre no Obsidian. As 26 notas conectam visão geral, comandos, arquitetura Godot, criação de conteúdo, rede, física, build, testes e publicação. Para retomar o desenvolvimento, comece por [CONTEXTO PARA AGENTES](docs/Obsidian/LAVOICE/CONTEXTO%20PARA%20AGENTES.md). Nenhum plugin adicional é necessário.

[Patch notes completos](CHANGELOG.md) · [Catálogo](docs/CATALOGO-DE-COMANDOS.txt) · [Controles detalhados](docs/LEIA-ME.txt) · [Roteiro de testes](docs/ROTEIRO-DE-TESTES.md) · [Créditos](CREDITOS.txt)

## Laboratório de depuração

O ZIP executável do Laboratório foi retirado das releases. As descrições e os relatórios permanecem como documentação do projeto; não há laboratório executável disponível para download no repositório.

## Verificação e limites

- Jogo Mod 4: **7.982 verificações locais aprovadas** no motor nativo.
- Rede Mod 4: **245 verificações aprovadas**, com um anfitrião e cinco clientes na mesma máquina.
- Laboratório: **667 verificações aprovadas**, 191 imagens da auditoria e quatro dos controles, com renderização real.
- O ZIP de documentação Obsidian tem SHA-256 em [SHA256SUMS.txt](SHA256SUMS.txt); não há arquivo de jogo ou patch publicado neste momento.

Voz e conexão pela internet não foram revalidadas nesta rodada. Esses testes não esgotam combinações livres, obstáculos complexos e latência real. Os móveis são cenográficos e a física usa aproximações arcade. Medidas durante captura não são um benchmark de FPS.

A conexão normal continua por IP/rede local/Radmin VPN, UDP 27840. Mod 2, Mod 3, laboratório e versão oficial não são clientes intercambiáveis do Mod 4.

## Sobre o repositório

Este repositório público mantém documentação e notas históricas. Os pacotes executáveis do jogo, do mod e do laboratório foram removidos das releases. O projeto de trabalho e os dados privados de desenvolvimento permanecem fora deste repositório.

Jogo original: **Tsomyst**. Consulte [CREDITOS.txt](CREDITOS.txt) para os créditos e avisos registrados no projeto.
