---
title: "Implementar um animal"
version: mod4-lab1
updated: 2026-11-01
tags:
  - lavoice
  - lavoice/implementar
---

# Implementar um animal

Animais são tipos de Thing da categoria **creature**. Eles compartilham modelo, colisão, dono, equipe, dano e replicação com outras criações. Não precisam de uma cena independente para cada espécie.

## Variação básica

Para uma **extensão proposta** animal_lab:

1. Copie a entrada de dog ou cat em **data/defs/things.json**.
2. Use category creature e movement chase_enemy para perseguição padrão.
3. Copie e ajuste **data/balance.json → things.id**: peso, custo, hp, speed e impact_damage.
4. Cadastre nome e sinônimos nos léxicos.
5. Copie o modelo para **data/models/animal_lab.json**, mantendo a organização necessária à animação; depois modifique a forma.

Uma definição básica segue um esquema já usado por cat:

~~~json
{
  "animal_lab": {
    "category": "creature",
    "movement": "chase_enemy",
    "impact": "stop"
  }
}
~~~

“Mais inteligente” não é uma flag universal. Escolher alvos, seguir dono, vigiar uma região e atravessar obstáculos são decisões diferentes. [[15 - IA e perseguicao]] mostra o que o movimento atual realmente faz.

## Dono, equipe e alvo

Criações recebem dono/equipe no caminho de Forge. O movimento consulta Combat para encontrar adversários. Para seguir o dono, existe o movimento follow_owner. A edição de guarda usa guard_point e restringe o alvo a uma região próxima. Não substitua essas referências por uma busca global a cada quadro.

Para uma criatura voadora, confira a regra de movimento e os papéis do tipo, além de airborne quando aplicável. Uma mesma espécie pode ter behavior por role: como projectile, não deve necessariamente perseguir como uma criatura invocada no chão.

## Modelo e animação

Use peças e tags compatíveis com o sistema de animação existente. Confira a forma de dog/cat e a configuração **creature_anim** no balance. Um modelo que só tem cubos com tags genéricas aparece, mas não herda automaticamente uma animação de quatro patas convincente.

A cor do dono e os elementos podem tingir o modelo. Se uma espécie parece azul ou laranja, confira primeiro essa composição antes de concluir que o arquivo de modelo está errado.

## Integrar ao Tower Defense

O conjunto de animais da horda está em **TowerDefense.ANIMALS**, em scripts/gameplay/tower_defense.gd. A horda cria versões com modificadores de vida, velocidade, tamanho e rota. Acrescente uma espécie nessa lista apenas depois de validar a definição no catálogo e o comportamento físico.

Teste com até 32 inimigos ativos e confira se a rota, a altura, a vida e a colisão não causam congestionamento. Inimigos que aguardam vaga na onda não são um erro de spawn: há um limite intencional.

## Testes úteis

Degraus baixos, borda de plataforma, rampa, parede larga, passagem estreita, jogador em altura, ausência de alvo, dono removido, mudança de mapa e montaria. Experimente também o animal como projétil. Um novo visual não justifica duplicar o controlador de perseguição inteiro.

---

[[00 - Comece aqui|Voltar ao índice]]
