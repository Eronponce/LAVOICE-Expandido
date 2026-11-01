---
title: "Mapas e terreno"
version: mod4-lab1
updated: 2026-11-01
tags:
  - lavoice
  - lavoice/mundo
---

# Mapas e terreno

**scenes/arena/arena.gd** escolhe a arena, constrói os volumes, oferece spawns e informa quando o mundo está pronto. Mapas gerais são definidos em **data/world/maps.json**; seus layouts incluem **arena.json**, **tokyo3.json** e **space.json**. O TD usa **tower_defense.json** e decoração própria do modo.

## Tipos de mundo

| Mapa | Característica |
| --- | --- |
| Original | Arena de blocos, construções e natureza espelhadas, terreno escavável |
| Tokyo 3 | Ilha urbana maior, edifícios com interiores, viaduto e destruição por blocos |
| Espaço | Planetas e superfícies com gravidade local, orientação variável |
| Tower Defense | Praça central, quatro rotas e 24 pads de torres |

O laboratório encontrou 52 estruturas fixas no Original e 67 em Tokyo 3 na rodada registrada. Esses números incluem elementos de cenário conforme o layout; não equivalem a 119 edifícios novos criados pelo mod.

## Acrescentar uma estrutura fixa

As plantas fixas passam por **scripts/world/structure_blueprints.gd**. Os dados ficam em **data/world/blueprints.json** e **blueprints_city.json**; a cidade usa também **scripts/world/city_blueprints.gd**. Um layout contém entradas com blueprint, pos e rot.

Copie uma planta compatível, altere sua geometria e adicione uma entrada ao layout. Confira tamanho de célula, custo de chunks, apoios, portas, escadas e colisão. Evite colocar um spawn dentro de uma parede nova.

## Acrescentar um mapa

1. Crie um layout com dimensões e spawns válidos.
2. Acrescente o ID no seletor de mapas e no caminho de construção de Arena.
3. Preserve a ordem de votação dos IDs existentes quando o código a usa por índice.
4. Ofereça seis posições seguras ou confira a expansão de spawns feita por Arena.get_spawn().
5. Espere is_world_ready() antes de começar a física/testes.
6. Inclua dados e regras no cálculo de compatibilidade e na distribuição.
7. Acrescente o mapa ao laboratório e ao roteiro de teste.

No Espaço, **scripts/world/space_map.gd** constrói planetas e ambientes. Use Gravity.up_at() e o basis do spawn para câmera e movimento; World Y não representa cima em toda a superfície.

## Efeitos regionais

**scripts/gameplay/region_effects.gd** coordena fogo, gelo, lava, crateras, terremotos, montanhas e eventos do mapa. O interpretador transforma o pedido em intenção, e o diretor aplica na autoridade. A marca de região usa a mira; ela não identifica arbitrariamente um objeto mencionado em linguagem.

Uma região precisa de raio limitado, duração ou limpeza, orçamento de efeitos e sincronização adequada. Regeneração automática é opcional. No TD, a sanitização desliga regeneração/eventos e protege o terreno/rotas das ações que quebrariam o percurso.

## Validação

Teste seis spawns com cápsula e apoio físico, todos os lados do mapa, vista superior, interiores, bordas, extração e restauração. Depois repita após criar e destruir objetos e após trocar de modo. [[22 - Depuracao e testes]] documenta as capturas reproduzíveis.

---

[[00 - Comece aqui|Voltar ao índice]]
