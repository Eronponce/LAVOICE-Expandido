---
title: "Receitas e dados"
version: mod4-lab1
updated: 2026-11-01
tags:
  - lavoice
  - lavoice/dados
---

# Receitas e dados

Uma Recipe descreve a criação sem exigir uma cena montada. O esquema está em **scripts/language/recipe.gd**. Recipe.new_node(id) devolve os campos-base; Recipe.from_data() normaliza subárvores e comportamentos recebidos como dados.

~~~json
{
  "thing": "pistol",
  "mods": {},
  "control": "none",
  "movement": null,
  "behaviors": []
}
~~~

- **thing**: identificador neutro de idioma em data/defs/things.json.
- **mods**: escala, elementos, cor, quantidade, física, munição e outras opções aceitas.
- **movement**: substituição do movimento, ou null para usar regras/defaults.
- **control**: none, player ou auto, conforme os controles registrados.
- **behaviors**: pares de gatilho e ação, com subárvore em do.arg quando a ação recebe outra coisa.

## Exemplo com comportamento

Este fragmento usa tipos já existentes e substitui o disparo por um pombo explosivo. Ele é um exemplo de árvore, não um comando para contornar o preço no jogo:

~~~gdscript
var recipe: Dictionary = Recipe.new_node("pistol")
var payload: Dictionary = Recipe.new_node("pigeon")
payload.mods = {"explosive": true}
recipe.behaviors = [{
    "when": {"type": "on_fire"},
    "do": {"type": "shoot", "arg": payload}
}]
Recipe.set_mod(recipe, {"key": "element"}, "fire")
Recipe.set_mod(recipe, {"key": "element"}, "ice")
~~~

Use Recipe.set_mod() para os modificadores cumulativos. Elementos mantêm elements e o primeiro element por compatibilidade. Efeitos físicos também preservam uma lista. A escala aplicada por esse caminho fica entre 0,3 e 10; speed, damage, durability, fire_rate, weight e accuracy têm limites de 0,2 a 4. Não suponha que preencher um Dictionary manualmente aplique todas essas proteções.

## As quatro camadas de um tipo

| Camada | Exemplo de responsabilidade |
| --- | --- |
| data/defs/things.json | Categoria, projétil, movimento e comportamentos |
| data/balance.json | Custo, vida, velocidade, dano e parâmetros de armas |
| data/lexicon/pt_br/things.json | Nome, palavras e plurais em português |
| data/models/id.json | Modelo por peças, tags, juntas e âncoras |

data/rules/placement.json escolhe onde cada categoria chega: weapon/tool na mão, structure no chão da mira, creature/vehicle à frente, ammo para recarga e attachment para acoplamento. Acrescentar montável pode mudar a colocação de um item normalmente segurado.

## Comportamentos e papéis

Assembler combina defaults do tipo, defaults do papel e comportamentos explícitos. Os papéis incluem head, projectile, spawned, summoned e mounted. Um gato lançado como projétil pode precisar de regras diferentes de um gato colocado no mundo.

Uma ação precisa existir em data/defs/actions.json e em Assembler.ACTIONS; um gatilho precisa existir no registro correspondente. Texto, dados e classe executora são contratos separados. [[09 - Implementar uma arma]] e [[10 - Implementar um animal]] mostram exemplos completos do processo.

---

[[00 - Comece aqui|Voltar ao índice]]
