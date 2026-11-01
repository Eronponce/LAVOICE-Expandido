---
title: "Implementar uma arma"
version: mod4-lab1
updated: 2026-11-01
tags:
  - lavoice
  - lavoice/implementar
---

# Implementar uma arma

A forma mais segura é criar uma variação de arma existente antes de inventar uma ação nova. O exemplo abaixo é uma **extensão proposta** chamada pistol_lab, reconhecida como “pistola laboratório”. Ela ainda não faz parte do catálogo entregue.

## 1. Registrar o tipo

Acrescente uma entrada em **data/defs/things.json**, preservando as demais:

~~~json
{
  "pistol_lab": {
    "category": "weapon",
    "projectile": "bullet",
    "behaviors": [
      {
        "when": {"type": "on_fire"},
        "do": {"type": "shoot", "arg": {"thing": "bullet"}}
      }
    ]
  }
}
~~~

Esse é um fragmento para mesclar no objeto raiz do JSON, não um arquivo substituto completo. O gatilho on_fire e a ação shoot já são executados pelo Assembler.

## 2. Definir números e partes

Em **data/balance.json**, adicione **things.pistol_lab** copiando inicialmente o formato de things.pistol, como custo e peso. Adicione também **weapons.pistol_lab** copiando **weapons.pistol**. Esta segunda entrada é necessária para preservar os parâmetros de rear, front e muzzle: cadência, pente, recarga, potência, zoom, canos e abertura.

Mude um parâmetro por vez. Uma arma pode ter modelo correto e disparo incorreto se o conjunto de partes não tiver os números esperados. Os eixos e as tags estão em **data/rules/weapon_sections.json**.

## 3. Tornar o nome reconhecível

Em **data/lexicon/pt_br/things.json**:

~~~json
{
  "pistol_lab": {
    "name": "pistola laboratório",
    "words": ["pistola laboratório", "pistola de laboratório"],
    "forms": ["pistolas de laboratório"]
  }
}
~~~

Se a distribuição suporta outro idioma, acrescente a entrada correspondente em **data/lexicon/en_us/things.json** e valide esse idioma também. Não traduza o ID: a receita e a rede continuam usando pistol_lab.

## 4. Dar um modelo ao ID

Copie **data/models/pistol.json** para **data/models/pistol_lab.json**. Comece pela cópia intacta e confirme que o modelo aparece. Depois altere cores, peças e dimensões. Preserve anchor, joints.trigger, joints.muzzle e tags como grip, body e barrel enquanto não houver motivo para mudar o encaixe.

Um novo modelo mínimo pode conter pieces com shape, size, pos, color e tag, mas copiar uma arma existente evita perder os encaixes e a divisão de partes. Veja [[08 - Receitas e dados]].

## 5. Verificar pelo caminho real

- Recarregue o catálogo e confira erros/avisos de LexiconData.
- Digite “pistola laboratório” e confira a Recipe e a prévia.
- Confirme com clique esquerdo, teste recusa e fila.
- Dispare; confira munição, recarga, origem do projétil e colisão.
- Crie outra arma com slot livre e depois com seis slots ocupados.
- Teste custo de matéria e Caos, inclusive com fogo, explosão, vários canos e munição composta.
- Teste host e cliente usando o mesmo catálogo.

## Adicionar uma ação de verdade

Se não existir uma ação equivalente, implemente uma classe em scripts/things/action derivada de **ThingAction**. O contrato executável é **run(ctx: ActionContext)**; setup() já guarda thing e spec. Uma ação que altera estado deve começar validando **thing.has_simulation_authority()**.

Depois registre o ID em Assembler.ACTIONS, acrescente a definição em data/defs/actions.json e as regras linguísticas necessárias. Reutilize Combat e Forge para dano e spawns, em vez de criar um segundo caminho sem limites. Atualize [[19 - Materiais e Caos|a avaliação de poder]] e [[17 - Multiplayer e autoridade|a replicação]] quando o estado novo exigir isso.

---

[[00 - Comece aqui|Voltar ao índice]]
