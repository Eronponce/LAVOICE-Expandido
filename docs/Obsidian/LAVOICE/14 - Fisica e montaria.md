---
title: "Física e montaria"
version: mod4-lab1
updated: 2026-11-01
tags:
  - lavoice
  - lavoice/fisica
---

# Física e montaria

O modelo de corpo atual é Thing, com movimentos plugáveis. O caminho **scripts/things/move/move_physics.gd** implementa impulso, gravidade, amortecimento, quique e transferência de impulso entre criações. Ele usa move_and_collide() e limita velocidade. A rotação aplicada ao modelo visual não transforma isso em uma simulação rígida completa do veículo.

## Ativar física

A seleção de movimento em Assembler dá prioridade a **mods.physics** e escolhe physics. O pedido “com física” deve chegar ao modificador correspondente; não dependa do nome do objeto. Ferramentas como antigravidade também podem chamar enable_dynamic_physics() em alvos elegíveis.

Thing.apply_physics_effect(kind, source) já trata shrink, grow, antigravity, push, pull, vortex e stasis. Há verificações de autoridade, morte e item segurado antes de aplicar o efeito. Encolher e ampliar usam set_effect_scale(), que atualiza a geometria e as colisões. Alterar somente model.scale deixa o corpo físico errado.

## Camadas físicas

As constantes estão em **scripts/things/physics_layers.gd**:

| Camada | Bit |
| --- | --- |
| WORLD | 1 |
| PLAYERS | 2 |
| THINGS | 4 |
| PROJECTILES | 8 |
| DEBRIS | 16 |
| PORTAL_TUNNEL | 32 |

SOLID combina mundo, jogadores e criações. DAMAGEABLE combina jogadores, criações e projéteis. Uma consulta que só usa WORLD não testa a parede de uma casa invocada que está em THINGS.

## Montaria e veículos

Veículos usam categoria vehicle e recebem controle de jogador no Assembler quando apropriado. O fluxo de pilotagem e a referência piloting estão em **scenes/player/player.gd**; os componentes de controle ficam em **scripts/things/control**. F monta e sai pelo caminho existente.

Acrescentar mountable permite colocar no mundo itens que normalmente iriam para a mão. Isso não torna todo corpo elegível a qualquer momento: objetos segurados, projéteis, núcleos protegidos e montarias ocupadas têm exclusões. O Mod 3 ampliou a interação com criações livres de outros jogadores.

## Acrescentar uma mecânica de física

1. Defina o efeito e o estado temporário necessário em Thing.
2. Aplique apenas na autoridade de simulação.
3. Use up()/Gravity em vez de assumir que cima é sempre Vector3.UP.
4. Atualize geometria, colisão e limites juntos se houver escala.
5. Inclua o estado necessário no caminho de rede de Thing.
6. Garanta expiração, limpeza e comportamento ao montar/segurar.
7. Teste efeito repetido, tamanho mínimo/máximo, estase, impacto e troca de mapa.

> [!bug] Armadilha de depuração
> Desativar process_mode de um CollisionObject pode retirá-lo da física conforme disable_mode. No laboratório, parar callbacks de movimento é diferente de remover o corpo. Confira colisão com uma consulta positiva, não apenas com uma porta supostamente vazia.

[[15 - IA e perseguicao]] reutiliza o corpo para testes de obstáculo; [[22 - Depuracao e testes]] ensina a observar essas formas.

---

[[00 - Comece aqui|Voltar ao índice]]
