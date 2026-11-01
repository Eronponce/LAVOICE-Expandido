---
title: "Elementos e reações"
version: mod4-lab1
updated: 2026-11-01
tags:
  - lavoice
  - lavoice/implementar
---

# Elementos e reações

Elementos combinam aparência, status e consequências de combate. Eles não são apenas palavras no nome da arma. Os registros principais ficam em **data/rules/elements.json**, **data/defs/modifiers.json**, **data/lexicon/pt_br/modifiers.json**, **data/balance.json → status/reactions** e nos consumidores de combate.

## Exemplo existente: fogo

A definição de fire em elements.json tem tint, mix, glow, explosion e status burning. O modificador fire usa key element, value fire e descends copy. O léxico fornece as palavras reconhecíveis. Recipe.set_mod() acumula elementos e preserva o primeiro no campo element por compatibilidade.

Os elementos visuais e comportamentais incluem fogo, gelo, laser, choque, veneno, ácido, água, vento, terra, luz, sombra, gravidade e plasma. Uma receita pode acumular elementos; o comportamento final depende dos consumidores implementados.

## Reações existentes

As notas da expansão descrevem choque térmico de fogo com gelo, eletrocussão de água com choque, combustão tóxica de veneno com fogo, cristalização de terra com gelo, tempestade de fogo, eclipse, geada elétrica e pressão gravitacional. Confira os números e condições em **balance.reactions** e no caminho de Combat antes de alterar uma reação.

A arma passa elementos aos projéteis pelo caminho de herança da Recipe. Não aplique dano tanto no disparo quanto no impacto só para “garantir”: isso pode duplicar o efeito e invalidar o preço de Caos.

## Acrescentar um elemento

1. Escolha um ID neutro de idioma e um status existente, ou implemente um novo status completo.
2. Cadastre cor/brilho e status em elements.json.
3. Adicione o modificador neutro e as palavras no léxico.
4. Acrescente os parâmetros de status/reação no balance.
5. Implemente os consumidores de efeito real: Combat, Thing ou Player, conforme o alvo.
6. Confira aura em **scripts/things/element_aura.gd**, materiais compartilhados e cor do dono.
7. Verifique herança por munição, anexos e subárvores, além do custo de poder.

Se só foram adicionadas cor e palavras, documente o elemento como visual. Um novo ID de status não ganha automaticamente dano por tempo ou movimentação própria.

## Nova mecânica reutilizável

Para congelar, empurrar, puxar, incendiar ou explodir, procure primeiro ações existentes em **scripts/things/action**. Uma ação nova deriva de ThingAction e implementa **run(ctx)**, registra o ID em Assembler.ACTIONS e verifica autoridade de simulação.

O dano deve passar por **scripts/things/combat.gd**, respeitando equipes, proteção e limites. Spawns devem passar por Forge, para conservar profundidade máxima, limites de entidades e replicação.

## Matriz mínima de teste

Teste um elemento sozinho, em dupla, em projétil, em arma, em criatura, durante recusa de pedido, no limite de vida e após trocar de mapa. Compare host e cliente: os efeitos podem ser visuais em ambos, mas a decisão de dano deve acontecer uma vez.

Veja [[14 - Fisica e montaria]] para efeitos que mudam o movimento e [[19 - Materiais e Caos]] para custo.

---

[[00 - Comece aqui|Voltar ao índice]]
