---
title: "Tower Defense cooperativo"
version: mod4-lab1
updated: 2026-11-01
tags:
  - lavoice
  - lavoice/td
---

# Tower Defense cooperativo

O modo está em **scripts/gameplay/tower_defense.gd**, coordenado por GameplayDirector. Todos defendem um núcleo central no mesmo time. Os animais invasores são outro time, com rotas e recompensas geridas pelo host.

## Padrões da entrega

| Regra | Valor padrão |
| --- | --- |
| Material inicial compartilhado | 300 |
| Recompensa por inimigo | 3 |
| Recompensa por onda vencida | 80 |
| Vida do núcleo | 2.000 |
| Preparação | 20 s |
| Intervalo de spawn | 0,8 s |
| Objetivo | 10 ondas |
| Animais simultâneos | até 32 |
| Pontos de torre | 24 |
| Rotas | 4 |

As regras configuráveis são sanitizadas. O saldo é limitado; extração do cenário, reciclagem e espólios de morte não devem criar recursos coletivos por fora das recompensas definidas. O modo protege as rotas e desativa loot aleatório/eventos/regeneração que interfeririam no objetivo.

## Estrutura do modo

TowerDefense.route(lane) produz os pontos curvos de cada rota. pads() gera as posições das torres; decorate() desenha a praça, estradas e marcações. O layout de terreno está em **data/world/tower_defense.json**.

A fase de preparação permite gastar o recurso e o anfitrião pode iniciar a onda com F4. A horda respeita vagas de animais e capacidade da rede: o restante aguarda, sem pausar quem já está ativo. A cada cinco ondas pode haver chefe. Ao fim, vitória e derrota param a atuação das torres/inimigos e limpam o estado apropriado.

## Torres

IDs atuais: td_gun_tower, td_fire_tower, td_ice_tower, td_shock_tower, td_cannon_tower, td_sniper_tower e td_poison_tower. Cada uma usa definição de Thing, modelo e comportamento de disparo automático.

A interpretação de “torre” depende do contexto: em TD ela deve virar torre de defesa; no Sandbox pode virar construção composta. No TD, a colocação exige pad livre, uma torre por pad e tamanho permitido. Essa exigência de pads não se aplica às criações livres do Sandbox. Uma arma ou criatura qualquer não deve contornar essa regra só por receber outro nome.

## Acrescentar uma torre

1. Crie definição de estrutura estática e comportamento automático no catálogo.
2. Defina custo/vida/arma e modelo.
3. Acrescente o ID em TOWER_IDS e ao reconhecimento apropriado em CommandInterpreter.
4. Garanta alcance e duração de projétil coerentes.
5. Reutilize validate_recipe(), nearest_pad() e register_tower().
6. Teste pad ocupado, falta de saldo, fila e dois aliados confirmando juntos.
7. Confira alvo inimigo, proteção de núcleo/aliados e limpeza na troca de modo.

## Acrescentar um inimigo ou onda

A lista ANIMALS limita as espécies disponíveis; o spawn acrescenta modificadores e a marcação de horda. goal_for() oferece o próximo destino conforme a lane e o progresso. Reutilize MoveChaseEnemy, em vez de mover o animal em linha reta ignorando colisão.

Teste o núcleo recebendo dano, torres matando inimigos, recompensa exatamente uma vez, limite de 32, vaga liberada após morte, chefe, última onda, derrota e recarga de cena com seis clientes. [[17 - Multiplayer e autoridade]] cobre a transição.

---

[[00 - Comece aqui|Voltar ao índice]]
