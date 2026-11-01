---
title: "Vestíveis e habilidades"
version: mod4-lab1
updated: 2026-11-01
tags:
  - lavoice
  - lavoice/implementar
---

# Vestíveis e habilidades

Habilidades do jogador não precisam ser objetos segurados. A receita pode usar **ability** e **duration**. As definições, palavras e parâmetros ficam em **data/defs/abilities.json**, **data/lexicon/pt_br/abilities.json** e **data/balance.json → abilities**.

## Habilidades existentes

Há cura, regeneração, salvaguarda, visão noturna, visão ampla, salto, corrida, voo, jetpack e escavação, além de roupas com bônus. Teletransporte, invisibilidade e escudo de energia também têm caminhos no interpretador/diretor. O limite de vida do jogador continua em 150.

O Mod 4 coloca novas habilidades no fluxo de prévia e confirmação. Uma implementação não deve aplicá-las no cliente antes de a criação ser aceita pelo host.

## Vestível orientado a dados

A configuração existente de fire_armor em balance.abilities contém:

~~~json
{
  "duration": 180,
  "cost": 35,
  "wear_slot": "chest",
  "elements": ["fire"],
  "tint": "#e46a37",
  "damage_mult": 0.8,
  "resist_elements": ["fire", "plasma"]
}
~~~

Este bloco é de uma habilidade existente. Para uma **extensão proposta**, crie outro ID e adicione definição e léxico correspondentes. Ajuste apenas campos que Player realmente consome. Um atributo inventado no JSON é ignorado até existir código para aplicá-lo.

**scripts/player_wearables.gd** observa as habilidades ativas e monta as formas visuais. Os slots atuais incluem chest, boots, cloak e helmet. **scenes/player/player.gd** remove outra habilidade do mesmo wear_slot quando uma nova ocupa essa posição. Slots diferentes podem combinar.

## Bônus já consumidos

O código do jogador consulta multiplicadores como damage_mult, speed_mult e gravity_mult e resistências elementais. Regen, voo, visão e habilidades especiais têm seus próprios caminhos. Antes de criar um bônus novo, procure o consumidor no jogador, não apenas a declaração em balance.

A geometria de roupa é simples e acompanha o robô. Em primeira pessoa há tratamento de camadas para não bloquear a câmera. Uma roupa nova precisa ser conferida em primeira e terceira pessoa, montado e sob gravidade de planeta.

## Implementar uma habilidade nova

1. Defina duração, custo e limites.
2. Cadastre ID e palavras.
3. Acrescente o efeito no caminho autoritativo de Player ou no executor correto do diretor.
4. Implemente atualização, expiração, remoção e reinício ao morrer/trocar de modo.
5. Acrescente representação de rede do estado necessário, reutilizando snapshots.
6. Se for roupa, mantenha a exclusão por slot e os visuais em player_wearables.
7. Teste combinação, troca por outra roupa, morte, cura perto de 150 e remoção de efeitos.

> [!note] Não multiplicar o bônus a cada quadro
> Recalcule a partir do estado base e das habilidades ativas. Multiplicar permanentemente a velocidade atual em _process() gera crescimento cumulativo e dificulta voltar ao normal.

[[07 - Pipeline de criacao]] explica a confirmação; [[18 - Interface e personalizacao]] explica como expor a habilidade ao jogador.

---

[[00 - Comece aqui|Voltar ao índice]]
