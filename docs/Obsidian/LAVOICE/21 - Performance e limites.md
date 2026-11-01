---
title: "Performance e limites"
version: mod4-lab1
updated: 2026-11-01
tags:
  - lavoice
  - lavoice/performance
---

# Performance e limites

Antes de otimizar, reproduza um cenário e registre contagem de entidades, tempo de física, draw calls e tempos de quadro. Uma consulta a menos no código não prova aumento proporcional de FPS.

## Orçamentos atuais

| Recurso | Limite ou política |
| --- | --- |
| Jogadores | 6 |
| Entidades vivas por jogador | 80, configurado em balance.caps |
| Entidades globais online | 256, em data/network.json |
| Horda ativa | 32 animais |
| Inventário | 6 posições |
| Fila de criação | 1 por jogador |
| Profundidade da árvore | 3 em balance.caps.tree_depth |
| Divisão de projétil | split_max 8 |
| Acoplamentos | profundidade 2; orçamento de 8 por receita |
| Explosões | orçamento de 6 por segundo por caminho limitado no Forge |
| Vida máxima de projétil | 10 s no limite configurado |
| Planta composta | até 112 peças |
| Desenho de colisões no laboratório | até 120 formas do corpo selecionado |

Esses limites pertencem a sistemas diferentes e não são todos uma única contagem. Hordas, projéteis, objetos segurados e entradas de rede precisam ser avaliados nos respectivos orçamentos.

## Otimizações já presentes

MoveChaseEnemy atualiza a busca de alvo a 5 Hz. Combat reaproveita candidatos por passo físico. ModelBuilder tem caches de malhas/modelos/materiais; modificadores de horda que não alteram geometria não devem criar outra malha idêntica. ChaosPolicy tem cache limitado de avaliação de receitas.

A horda aguarda vaga quando necessário, sem congelar inimigos ativos. A remoção por limite prioriza projéteis antigos antes de construções. Drops no chão têm expiração e limite por pessoa; itens segurados ficam fora da limpeza comum.

## Onde medir

O laboratório exibe FPS, física, nós e draw calls. Os dados de captura incluem câmera, mapa, tempos recentes e estado. **scripts/dev/performance_recorder.gd** e **dev_probe.gd** fornecem instrumentação de cenários/trechos quando habilitada no build e nos argumentos apropriados.

Meça após o carregamento e o aquecimento do cache. Captura de GPU, criação de modelos, compilação de shaders e escrita de PNG podem provocar picos que não representam combate estável. Oculte colisões antes de medir: as malhas diagnósticas aumentam o custo.

## Critérios para uma melhoria

- Mesmo cenário, câmera, regras, número de entidades e duração.
- Contadores e tempos antes/depois; percentis além da média quando úteis.
- Nenhuma mudança não intencional de custo, colisão, alcance ou alvo.
- Memória/objetos voltam a um patamar estável após limpar e trocar de mapa.
- Host e clientes continuam recebendo estado suficiente.

No ensaio documentado do Mod 4, 120 passos simulados produziram 10 atualizações de alvo no trecho otimizado. Isso é redução de chamadas nesse caminho; não foi uma medição de 92% de ganho de FPS.

Se o gargalo for desenho, reduzir IA não o resolve. Se for física, acrescentar materiais e partículas pode piorar o sintoma sem tocar a causa. [[22 - Depuracao e testes]] descreve como registrar uma reprodução.

---

[[00 - Comece aqui|Voltar ao índice]]
