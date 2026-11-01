---
title: "Implementar construções"
version: mod4-lab1
updated: 2026-11-01
tags:
  - lavoice
  - lavoice/implementar
---

# Implementar construções

Há dois caminhos diferentes: construções invocadas como Thing e estruturas do mapa feitas de voxels. Escolha conforme o problema; não transforme tudo no mesmo tipo de corpo.

## Construções invocadas simples

Um objeto de catálogo usa uma entrada de categoria structure em **data/defs/things.json**, parâmetros em **data/balance.json**, nome nos léxicos e modelo em **data/models**. A regra de colocação usa o chão da mira. Categoria, vida e colisões precisam ser coerentes com o modelo.

## Construções compostas por linguagem

**scripts/gameplay/command_interpreter.gd** produz uma Recipe de **compound_structure** com um plano em mods.blueprint. **scripts/gameplay/structure_geometry.gd** transforma esse plano em peças determinísticas em cada participante.

~~~json
{
  "thing": "compound_structure",
  "mods": {
    "blueprint": {
      "kind": "house",
      "width": 12,
      "height": 6,
      "depth": 10,
      "floors": 2,
      "material": "brick",
      "furnished": false
    },
    "around": false,
    "mountable": false
  },
  "control": "none",
  "movement": null,
  "behaviors": []
}
~~~

Este é um formato de receita completo compatível com a implementação. O kind atual pode representar casa, caixa, torre, ponte, fortaleza, prisão, labirinto ou montanha, conforme o caminho que o produz.

### Limites do plano

O interpretador limita largura a 3–24 m, altura a 2,5–18 m, profundidade a 3–28 m e andares a 1–3. Casas mobiliadas recebem pelo menos 8 × 8 m. A geometria acomoda altura mínima de 3 m por nível e limita o resultado a 112 peças. A validação de custo e posicionamento continua sendo necessária.

### Acrescentar uma planta

1. Defina um kind e seu conjunto de parâmetros limitado.
2. Acrescente uma geração determinística em StructureGeometry.pieces().
3. Use peças com shape, size, pos, color e tag; dimensões devem ser positivas.
4. Cadastre a linguagem em CommandInterpreter sem capturar frases de armas que contêm “atira”.
5. Faça piso, entradas e janelas realmente vazados.
6. Confira limites de custo, colisores e replicação do plano.

O tipo compound_structure tem **hollow: true**. ModelBuilder produz informações para colisões por peça. Não substitua isso por uma única caixa que bloqueia o interior inteiro.

## Móveis de uma casa

StructureGeometry.furniture() cria cama, colchão, travesseiro, guarda-roupa, bancada, pia, fogão, geladeira, sofá, mesa, cadeiras, vaso, chuveiro, luz e estante. Eles são geometria cenográfica; não implementam eletrodomésticos funcionais. Preserve circulação e o espaço da escada.

## Dano e remoção

Thing acompanha a vida de construções e oculta partes conforme o dano, desabilitando as colisões correspondentes por solid_index. Em modos competitivos, resistência e teto de dano por impacto protegem contra destruição instantânea. A regra não simula integralmente engenharia estrutural de edifícios.

As estruturas originais do mapa usam **scripts/world/structure.gd** e **block_volume.gd**, com dano por blocos. Novas plantas fixas do mapa seguem StructureBlueprints e os JSONs de mundo, descritos em [[16 - Mapas e terreno]].

> [!tip] Validar o que não aparece
> Teste com corpo de personagem e visualização de colisões. Um raycast passando pela porta não prova que uma cápsula inteira consegue atravessar. Confira escada, desembarque no andar e teto. [[22 - Depuracao e testes]] inclui o laboratório.

---

[[00 - Comece aqui|Voltar ao índice]]
