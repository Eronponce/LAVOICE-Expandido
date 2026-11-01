---
title: "Multiplayer e autoridade"
version: mod4-lab1
updated: 2026-11-01
tags:
  - lavoice
  - lavoice/rede
---

# Multiplayer e autoridade

O anfitrião centraliza regras e estado compartilhado. O cliente solicita ações e mantém apresentação/predição conforme os sistemas existentes. Não dê ao cliente a decisão final sobre saldo, dano, pontuação ou coleta.

## Componentes

| Sistema | Arquivo |
| --- | --- |
| Sessão e jogadores | scripts/network/network_session.gd |
| Lobby | scripts/network/lobby_session.gd |
| Transporte | scripts/network/network_transport.gd |
| Estado dos jogadores | scripts/network/player_replication.gd |
| Criações e propostas | scripts/network/forge_replication.gd |
| Estado de cada criação | scripts/network/thing_network_state.gd |
| Mundo, rodadas e regras | scripts/network/world_replication.gd |
| Compatibilidade | scripts/network/session_compatibility.gd |
| Voz de conversa | scripts/network/voice_replication.gd |
| Limites de mensagens | data/network.json |

**Session.creations** é uma instância de ForgeReplication. O nome da propriedade não é o nome do arquivo.

## Compatibilidade da entrega

A versão de protocolo é **25** e GAMEPLAY_VERSION é **h4-community-defense-4**. O manifesto também considera dados JSON, recursos validados do personagem e configurações de física. Mudar apenas um número de versão não torna catálogos diferentes compatíveis.

O limite da sessão é seis jogadores. IDs e remetentes são validados. O limite global configurado de criações online é 256. Não remova verificações só porque um teste local confia no cliente.

~~~mermaid
sequenceDiagram
    participant C as Cliente
    participant H as Host
    participant M as Mundo
    C->>H: Texto do pedido
    H->>H: Interpretar e propor
    H-->>C: Receita, preço e prévia
    C->>H: Confirmar ou enfileirar
    H->>H: Revalidar e debitar
    H->>M: Materializar uma vez
    H-->>C: Criação e estado autoritativo
~~~

## Snapshot e estado novo

GameplayDirector.snapshot() reúne rules, kills, deaths, chaos, respawns, shields, orbs, message, winner, clock, core_down, regions, tower_defense e orders. WorldReplication o transporta no estado de rodada.

Os drops não estão nessa lista do snapshot de rodada. Seu acompanhamento e tempo de vida são controlados pelo diretor autoritativo; as entidades correspondentes e seu estado passam pelos caminhos de ForgeReplication e ThingNetworkState. Esses componentes cuidam dos IDs, poses e propriedades necessárias das criações.

Ao adicionar uma propriedade, defina o formato, tipo, faixa, autoridade e limpeza. Teste serialização e aplicação no cliente, inclusive entrada tardia e baseline. Não replique toda a árvore de nós a cada quadro quando uma receita determinística e alguns campos bastam.

## Troca de modo

A troca de regras tem coordenação em fases: suspender/finalizar o estado antigo, despawnar entidades, aguardar clientes limparem/confirmarem e recarregar com a sessão preservada. Em Match, preserve_session_on_exit impede o encerramento indevido da sessão nessa transição.

Um atalho que recarrega a cena sem esse acordo pode deixar objetos antigos, RPCs contra nós ausentes ou desconectar jogadores. Reutilize change_match_rules() e o fluxo existente.

## Verificação necessária

Teste um host e cinco clientes com pedido remoto, confirmação, recusa, fila, inventário, débito compartilhado, orbe disputado, dano, morte, troca de mapa e reconexão. O teste entregue usou seis processos na mesma máquina; a internet real ainda requer ensaio separado.

Atualize compatibilidade quando alterar semântica ou formato incompatível. Preserve os recursos originais importados do robô: reconstruções a partir de arquivos recuperados podem produzir checksums diferentes e falhar na sessão.

---

[[00 - Comece aqui|Voltar ao índice]]
