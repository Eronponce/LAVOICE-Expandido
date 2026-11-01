---
title: "Arquitetura e arquivos"
version: mod4-lab1
updated: 2026-11-01
tags:
  - lavoice
  - lavoice/arquitetura
---

# Arquitetura e arquivos

A raiz do projeto local é o diretório que contém **project.godot**. Na área de trabalho usada para esta edição, ele está em **work/recovered**. Todos os caminhos a seguir são relativos a essa raiz.

## Mapa dos sistemas

| Responsabilidade | Arquivo principal |
| --- | --- |
| Cena de partida e ciclo de vida | scenes/main.gd e scenes/main.tscn |
| Estado e geometria da arena | scenes/arena/arena.gd |
| Personagem, habilidades e entrada | scenes/player/player.gd |
| Entrada central de criações | scripts/autoload/forge.gd |
| Léxico carregado e regras | scripts/autoload/lexicon.gd; scripts/language/lexicon_data.gd |
| Padrões avançados de comando | scripts/gameplay/command_interpreter.gd |
| Parser de receitas do catálogo | scripts/language/phrase_parser.gd |
| Árvore e modificadores de receita | scripts/language/recipe.gd |
| Proposta, preço, fila e débito | scripts/gameplay/creation_orders.gd |
| Montagem de entidades | scripts/things/assembler.gd |
| Construção de modelos | scripts/things/model_builder.gd |
| Corpo, dano e estado da criação | scripts/things/thing.gd |
| Regras de partida | scripts/gameplay/gameplay_director.gd |
| Hordas e torres | scripts/gameplay/tower_defense.gd |
| Regiões de terreno | scripts/gameplay/region_effects.gd |
| Sessão e compatibilidade | scripts/network/network_session.gd; scripts/network/session_compatibility.gd |
| Sincronização de mundo e criações | scripts/network/world_replication.gd; scripts/network/forge_replication.gd |
| Laboratório separado | scripts/dev/debug_lab.gd; scenes/dev/debug_lab.tscn |

~~~mermaid
flowchart LR
    Entrada[Voz ou texto] --> Forge[Forge]
    Forge --> Receita[Interpretadores e Recipe]
    Receita --> Pedidos[CreationOrders]
    Pedidos --> Montagem[Assembler e ModelBuilder]
    Montagem --> Mundo[Thing na partida]
    Diretor[GameplayDirector] --> Pedidos
    Diretor --> Mundo
    Host[Autoridade do host] --> Forge
    Mundo --> Rede[Replicação]
~~~

## Dados e código se complementam

**data/defs** descreve tipos neutros de idioma. **data/lexicon/pt_br** contém palavras e exibição em português. **data/balance.json** concentra números. **data/rules** contém colocação, elementos e regras auxiliares. **data/models** contém modelos descritos por peças.

Adicionar uma palavra não cria uma mecânica. Adicionar uma classe GDScript também não a torna reconhecível pelo parser. [[08 - Receitas e dados]] conecta essas duas pontas.

## Vocabulário técnico

**Recipe** é uma descrição de intenção serializável. **Thing** é uma entidade montada. **Role** define como a mesma coisa se comporta quando é raiz, projétil, invocação ou peça acoplada. **Draft** é a proposta ainda não confirmada. **Host** é a autoridade da sessão; o cliente solicita e representa, mas não deve decidir os resultados globais.

Não reimplemente esses conceitos em um segundo sistema paralelo. Uma mecânica nova deve atravessar os mesmos contratos de preço, execução, limpeza e rede.

---

[[00 - Comece aqui|Voltar ao índice]]
