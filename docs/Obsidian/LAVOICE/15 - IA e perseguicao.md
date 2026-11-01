---
title: "IA e perseguição"
version: mod4-lab1
updated: 2026-11-01
tags:
  - lavoice
  - lavoice/ia
---

# IA e perseguição

O controlador atual é **scripts/things/move/move_chase_enemy.gd**, classe MoveChaseEnemy. Ele melhora perseguição local e subida de obstáculos sem introduzir um sistema completo de navegação global.

## O que ele faz

- Atualiza alvos aproximadamente a cada **0,2 s** por perseguidor.
- Seleciona adversários por Combat, ou o dono no modo follow_owner.
- Segue pontos de rota do Tower Defense quando a receita tem mods.horde=true; a rota é identificada por mods.horde_lane.
- Restringe a busca de alvos quando existe guard_point.
- Testa desvios laterais quando o avanço está bloqueado.
- Tenta subir degraus em alturas de **0,27, 0,53 e 0,8 m**, verificando espaço com test_move().
- Detecta falta de progresso e tenta salto/escape local.
- Distingue movimento aéreo, veículo e perseguidor terrestre.

O alvo não é procurado de novo por todos os caminhos a cada quadro. A lista de candidatos de combate também é reaproveitada por passo físico.

## Ler o problema antes de modificar

| Sintoma | Primeira hipótese |
| --- | --- |
| Animal segue alguém errado | Equipe, dono, Combat.affects e alvo |
| Para em pequeno degrau | Forma de colisão, grounded, espaço acima e teste de subida |
| Fica oscilando numa parede | Direção de escape e atualização de alvo |
| Não alcança jogador num labirinto | Limite do desvio local; falta de planejamento global |
| Voa sem intenção | Movimento/role/airborne herdado da receita |
| Horda ignora caminho | Marcação mods.horde, mods.horde_lane e TowerDefense.goal_for |

A estatística estática **navigation_stats** contém target_updates, step_tests, steps_climbed e avoidance_tests. Ela ajuda a separar custo de busca de custo de locomoção. Não transforme uma redução de chamadas em promessa de ganho de FPS.

## Melhorar sem duplicar o controlador

Reproduza um obstáculo mínimo no laboratório ou numa fixture nativa. Meça o resultado com a mesma escala e o mesmo corpo usado no jogo. Se precisar de navegação global, mantenha a saída como ponto/direção desejada e reutilize o movimento físico para a etapa final.

Uma futura malha de navegação ou grade precisa lidar com terreno destruído, construções móveis e gravidade de planetas. Não é suficiente adicionar um NavigationAgent e assumir que todos os mundos foram cobertos. A invalidação da rota deve ter orçamento de desempenho e regra autoritativa.

## Testes mínimos

Degrau isolado; teto baixo sobre degrau; parede larga; quina; passagem de largura próxima ao corpo; alvo em cima da estrutura; caminho fechado; voo; veículo pilotado; 32 animais na mesma rota; mudança de mapa durante a perseguição.

> [!note] Limite conhecido
> A implementação atual ainda pode se prender em labirintos fechados ou barreiras grandes. Documente o cenário e a posição em vez de afirmar que a IA atravessa qualquer construção.

Veja [[20 - Tower Defense cooperativo]] para rotas e [[21 - Performance e limites]] para orçamento de consultas.

---

[[00 - Comece aqui|Voltar ao índice]]
