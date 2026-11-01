---
title: "Pipeline de criação"
version: mod4-lab1
updated: 2026-11-01
tags:
  - lavoice
  - lavoice/pipeline
---

# Pipeline de criação

A separação entre entender um pedido e executá-lo é o principal contrato da expansão. O fluxo está em **scripts/autoload/forge.gd** e **scripts/gameplay/creation_orders.gd**.

~~~mermaid
flowchart TD
    Texto[Texto reconhecido ou digitado] --> Pedido[Forge.request]
    Pedido --> Autoridade{Cliente online?}
    Autoridade -->|Sim| Host[Enviar pedido ao host]
    Host --> Interpretar
    Autoridade -->|Não| Interpretar[CommandInterpreter.parse]
    Interpretar --> Fallback{Reconheceu padrão?}
    Fallback -->|Não| Parser[PhraseParser.parse]
    Parser --> Resultado[Receita e avisos]
    Fallback -->|Sim| Resultado
    Resultado --> Tipo{Comando ou criação?}
    Tipo -->|Comando| Executar[GameplayDirector.execute ou comando existente]
    Tipo -->|Criação| Propor[CreationOrders.propose]
    Propor --> Previa[Shaper e CreationReview]
    Previa --> Escolha{Mouse}
    Escolha -->|Direito| Cancelar[Cancelar sem cobrar]
    Escolha -->|Meio| Fila[Guardar uma posição]
    Escolha -->|Esquerdo| Validar[Validar e debitar no host]
    Fila --> Validar
    Validar --> Materializar[Forge._materialize]
    Materializar --> Montar[Assembler e BuildAnimator]
~~~

## Entender não gasta material

propose() conserva a receita, o texto e o multiplicador de novidade para a prévia. O preço considera a receita resolvida. No Sandbox e nos testes livres, o preço é zero. A leitura do saldo muda no TD: vem do recurso compartilhado.

**CommandInterpreter** trata padrões de estruturas, regiões, favoritos e comandos contextuais. Quando devolve vazio, Forge usa **PhraseParser**, orientado pelo catálogo. Isso preserva os significados antigos e evita reescrever o parser.

## Confirmar é uma operação autoritativa

confirm() resolve dimensões, calcula o local e pode alinhar uma torre ao pad. _commit() verifica vida, prontidão, montagem atual, limites, saldo e regras do modo. Só depois chama try_spend(). A marca prepaid_player informa ao caminho de montagem que o custo já foi pago: a animação não deve debitar de novo.

A fila é uma posição por jogador. Ela guarda receita, texto, preço, posição e direção. Ao executar, o host revalida condições. Uma segunda proposta não pode substituir silenciosamente uma fila existente; cancelar a prévia não implica necessariamente cancelar a fila.

## O que continua direto

Comandos de pegar, largar, montar e edição seguem seus caminhos de ação. Spawns automáticos e projéteis não passam por confirmação a cada entidade. Colocar uma confirmação em todos os tiros quebraria armas e hordas.

## Ao estender o sistema

- Uma nova criação deve retornar uma Recipe ou habilidade reconhecida, para herdar preço e confirmação.
- Uma nova edição deve validar alvo, propriedade, modo e limites no executor autoritativo.
- Não crie uma Thing diretamente na callback do HUD para contornar a confirmação.
- Não cobre matéria tanto no clique quanto no BuildAnimator.
- Teste recusa, fila sem saldo, dois pedidos simultâneos e inventário cheio.

[[19 - Materiais e Caos]] detalha os custos; [[17 - Multiplayer e autoridade]] descreve o transporte.

---

[[00 - Comece aqui|Voltar ao índice]]
