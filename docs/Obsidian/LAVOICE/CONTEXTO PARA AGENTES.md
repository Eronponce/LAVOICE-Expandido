---
title: "Contexto técnico para agentes"
version: mod4-lab1
updated: 2026-11-01
tags:
  - lavoice
  - lavoice/retomada
---

# Contexto técnico para agentes

Esta é uma nota de contexto, não um AGENTS.md e não uma autorização para executar ações externas. Serve para retomar o projeto com os contratos corretos.

## Estado da entrega

O jogo recomendado é **LAVOICE H4 Expandido Mod 4**. O laboratório separado é **mod4-lab1**. A base normal não foi sobrescrita para criar o laboratório. Os pacotes completos incluem DLLs, voz original, créditos e licenças; não basta distribuir só o EXE.

O projeto local recuperado está em **work/recovered** no workspace de desenvolvimento e **não é um repositório Git**. O checkout público de documentação fica em **work/github-release**. Os caminhos das notas são relativos à raiz Godot, nunca à pasta do cofre. O repositório público é de documentação e binários, não um checkout completo compilável com todos os recursos originais.

## Invariantes a preservar

- Até 6 jogadores; todos precisam da mesma versão Mod 4.
- Protocolo 25 e gameplay h4-community-defense-4 em SessionCompatibility.
- Host valida pedidos, custo, dano, equipes, coleta, pontuação e regras.
- Separar interpretação de execução. Receita entendida não cria nem cobra imediatamente.
- CreationOrders confirma/enfileira e debita uma vez; BuildAnimator não cobra novamente quando pré-pago.
- Uma posição de fila por jogador. Arma nova usa slot livre primeiro; seis slots cheios substituem o selecionado.
- TD tem saldo compartilhado, pads válidos, uma torre por pad, rotas protegidas e sem extração/reciclagem criando saldo por fora.
- Elementos/poder real, incluindo subárvores e anexos, influenciam Caos; nome não determina sozinho o risco.
- Limites de entidade/projétil/árvore não são opcionais ao criar uma ação nova.
- Escala muda modelo e colisões. Respeitar Gravity em mundo espacial.
- Mudança de modo online espera limpeza/despawn e preserva a sessão no reload.
- Reconhecimento original sherpa/Parakeet continua no caminho CPU; renderização D3D12 usa GPU.
- Conversa de voz vem silenciada por padrão; isso é separado de reconhecer comandos.
- Laboratório inicia offline, sem voz e com recursos de teste livres. Não use seu saldo para avaliar equilíbrio.

## Fluxo de criação

Texto/voz reconhecida → Forge.request → host quando cliente → CommandInterpreter.parse → PhraseParser como fallback → Recipe → CreationOrders.propose → Shaper/CreationReview → clique/fila → revalidar/try_spend → Forge._materialize → Assembler/ModelBuilder → BuildAnimator → Thing ativa → replicação.

Comandos de edição/pegar/largar/montar e spawns internos têm caminhos próprios; não imponha uma confirmação a cada projétil.

## Mapa de arquivos essenciais

| Área | Arquivo |
| --- | --- |
| Mundo/partida | scenes/main.gd; scenes/arena/arena.gd |
| Jogador/inventário | scenes/player/player.gd; scenes/player/hands.gd; scenes/player/shaper.gd |
| Criação/preço | scripts/autoload/forge.gd; scripts/gameplay/creation_orders.gd |
| Linguagem | scripts/gameplay/command_interpreter.gd; scripts/language/phrase_parser.gd; scripts/language/recipe.gd; scripts/language/lexicon_data.gd |
| Montagem/corpo | scripts/things/assembler.gd; scripts/things/model_builder.gd; scripts/things/thing.gd |
| Regras | scripts/gameplay/gameplay_director.gd; scripts/gameplay/chaos_policy.gd; scripts/gameplay/tower_defense.gd; scripts/gameplay/region_effects.gd |
| IA/física | scripts/things/move/move_chase_enemy.gd; scripts/things/move/move_physics.gd; scripts/things/physics_layers.gd |
| Rede | scripts/network/network_session.gd; scripts/network/forge_replication.gd; scripts/network/world_replication.gd; scripts/network/thing_network_state.gd; scripts/network/session_compatibility.gd |
| UI | scripts/gameplay/creative_hud.gd; scripts/gameplay/creative_menu.gd; scripts/gameplay/creation_review.gd |
| Lab | scripts/dev/debug_lab.gd; scenes/dev/debug_lab.tscn |

## Schemas e extensões

Recipe.new_node(id) cria thing, mods, control, movement e behaviors. Cada behavior contém when e do; uma subárvore fica em do.arg. Use Recipe.from_data() para normalizar e Recipe.set_mod() para elementos/modificadores cumulativos.

Tipo novo exige defs/things, balance, léxico e modelo. Armas também precisam dos números de weapons.id por rear/front/muzzle. Uma palavra nova não implementa uma mecânica. Uma classe nova não se registra sozinha em Assembler.

ThingAction implementa run(ctx: ActionContext), não execute(). Ações novas entram em Assembler.ACTIONS e defs/actions, com linguagem e custo coerentes. Movimentos e gatilhos seguem registros próprios.

[[08 - Receitas e dados]] contém o esquema. [[09 - Implementar uma arma]], [[10 - Implementar um animal]] e [[11 - Implementar construcoes]] são roteiros de extensão.

## Limites e decisões de desempenho

80 entidades por jogador, 256 globais online, 32 animais ativos de horda, 24 pads TD, 6 slots, 1 fila, até 112 peças por planta composta. A busca de alvo é a 5 Hz; Combat compartilha candidatos por passo físico; caches de modelo e Caos evitam repetir trabalho. Confira os arquivos de configuração antes de mudar números.

O desvio de IA é local e pode falhar em labirintos fechados. Física é arcade. Móveis de casas são cenário. Destruição composta por vida/peças não é uma simulação estrutural integral de qualquer edifício.

## Build e testes

Use Godot/bytecode compatível com 4.7.2 e o engine original. Preserve recursos importados originais; reexportar GLBs recuperados pode alterar o checksum do robô e impedir rede. Patch em arquivo novo, nunca entrada=saída. A chave PCK é pré-requisito privado local e não pertence ao cofre, Git ou logs públicos.

Scripts compilados exigem .gdc e remap .gd.remap. Classes globais novas podem exigir o cache de classes no pacote. O fluxo nativo de testes usa cena inicial dedicada via project.binary; não suponha que --script no EXE da distribuição rode a fixture.

Fixtures locais: mod_validation, mod3_validation, mod4_validation e network4_validation (scripts/cenas na raiz do projeto). Fonte recuperada no editor pode não reproduzir os assets importados exatos exigidos no teste online; valide o EXE nativo final.

Evidência anterior: 7.982 checks locais do jogo; 245 checks com seis processos de rede locais; 638 checks de auditoria e 29 de interface no laboratório; 191 + 4 capturas. Internet, voz e todas as combinações livres não foram cobertas. Playwright falhou antes de executar no parser do RTK; fallback nativo documentado.

## Artefatos locais para retomada

- **work/MOD4-STATE.json**: versão normal, hashes, testes e localização da distribuição.
- **work/DEBUG-LAB-STATE.json**: laboratório, hashes, testes e localização dos relatórios.
- **work/patch-plan-mod4.json**: mapeamento dos arquivos alterados para os caminhos res:// do pacote.
- **work/mod4-source**: snapshot antes de acrescentar o laboratório.
- **outputs**: pacotes e documentação entregues; **work**: fontes, ferramentas e intermediários.

Descubra esses arquivos no workspace atual; não são incluídos automaticamente no cofre nem são um manifesto público de todos os fontes.

## Armadilhas do ambiente

GDRE --compile grava o .gdc pelo basename no cwd de trabalho, não necessariamente junto do .gd. Basenames iguais podem sobrescrever intermediários. A engine nativa dessa distribuição ignora os atalhos de cena/script usados normalmente no editor; fixtures exigiram project.binary com cena própria em um EXE separado.

Argumentos da engine ficam antes de **--**; argumentos do jogo, como --sem-voz e --auditar, ficam depois. O helper MobileDev lê OS.get_cmdline_user_args(). Não passe um caminho vazio de resultado ao fixture.

EXEs de distribuição podem ser hardlinks locais de um arquivo em work. Nunca sobrescreva o caminho publicado in-place; gere outra saída. Processos nativos lançados por certas chamadas Node perderam o ambiente de pasta de usuário/cache; testes gráficos finais devem usar o shell Windows/PowerShell com o ambiente normal. Neste workspace, os comandos de shell usam o prefixo RTK conforme as instruções locais.

## Próxima ação de um agente

1. Descobrir o workspace real e a versão dos arquivos; não inferir um caminho absoluto deste cofre.
2. Ler o guia do sistema afetado e reproduzir o problema.
3. Preservar snapshot/binários distribuídos.
4. Alterar o menor ponto de extensão sem contornar autoridade/economia.
5. Testar o caso e suas transições/limites relevantes.
6. Atualizar notas, comandos e evidência.
7. Publicar ou enviar arquivos somente quando houver autorização da sessão atual.

[[22 - Depuracao e testes]] · [[23 - Build e publicacao]] · [[24 - Contribuir e evoluir]] · [[00 - Comece aqui]]
