---
title: "Materiais e Caos"
version: mod4-lab1
updated: 2026-11-01
tags:
  - lavoice
  - lavoice/economia
---

# Materiais e Caos

Matéria e Caos têm funções diferentes. Matéria é o recurso de criação; Caos limita poderes destrutivos nos modos competitivos. No TD, matéria vira saldo compartilhado. No Sandbox, os custos são liberados para experimentar.

## Custo de matéria

**scripts/language/cost.gd** calcula custo da árvore a partir dos dados. Forge inclui novidade e contexto de preço. **CreationOrders** conserva a proposta e escolhe o saldo disponível: individual ou do time no TD.

Ao confirmar, o host revalida e chama try_spend(). O caminho de montagem recebe a marca de pré-pagamento para não cobrar novamente. Na fila, o preço guardado é preservado e a disponibilidade é reavaliada ao executar. Se dois aliados disputam o mesmo saldo, só os pedidos que couberem podem ser aceitos.

Uma prévia não deve consumir recurso. Recusar não pode deixar uma Thing criada. Um sucesso local não deve ser mostrado antes da aceitação autoritativa.

## Caos por poder real

**scripts/gameplay/chaos_policy.gd** monta/avalia a árvore, considerando comportamentos efetivos, projéteis, explosão, cadência, canos, potência, elementos, anexos e munição. Chamar algo de “gatinho” não evita o custo se a subárvore provoca uma explosão nuclear.

O custo base é de 0 a 100. O diretor aplica multiplicador para poderes especiais e custo configurável para a faixa nuclear. A política tem orçamento de profundidade/nós e cache limitado; não deixe uma árvore arbitrária executar uma expansão infinita durante a avaliação.

## Orbes

O padrão é aparecer um orbe a cada 60 segundos, valendo 25 pontos, com 30 segundos de vida. Raridades são opcionais: 15, 35 e 75 pontos por padrão. Eliminações também podem conceder Caos se configuradas.

O host anuncia, decide a coleta e remove o orbe. Dois clientes que tocam o mesmo orbe não podem receber recompensa duplicada. O minimapa deve representar o estado recebido, não criar seus próprios orbes.

## Como alterar a economia

- Mude números em balance ou nas regras sanitizadas, conforme a origem do custo.
- Acrescente o risco de uma nova ação à ChaosPolicy; comportamento novo sem classificação pode ficar grátis indevidamente.
- Verifique armas aparentemente comuns com munição, anexos ou subárvores perigosas.
- Teste saldo exato, saldo insuficiente, cancelamento, fila, morte e troca de modo.
- Não transforme extração/reciclagem em fonte de material de TD sem redesenhar a regra coletiva.

> [!note] Diagnóstico não é equilíbrio
> O laboratório usa Forge.test_free_matter e cria um ambiente de teste livre. O resultado ali prova montagem/interação, não preço ou dificuldade. Para economia, teste a distribuição normal Mod 4 com as regras reais.

[[20 - Tower Defense cooperativo]] descreve recompensas e [[07 - Pipeline de criacao]] explica a transação.

---

[[00 - Comece aqui|Voltar ao índice]]
