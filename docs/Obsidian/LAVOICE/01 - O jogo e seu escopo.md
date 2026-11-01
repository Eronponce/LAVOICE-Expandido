---
title: "O jogo e seu escopo"
version: mod4-lab1
updated: 2026-11-01
tags:
  - lavoice
  - lavoice/geral
---

# O jogo e seu escopo

LAVOICE combina combate, criação por linguagem e cenários destrutíveis. O jogador pede objetos, armas, criaturas e efeitos por voz ou texto; o jogo interpreta uma receita, mostra o resultado entendido e, desde o Mod 4, aguarda confirmação antes de materializar criações.

O H4 original é de **Tsomyst / Somyst Game Studio**. Expandido é uma modificação comunitária não oficial. Créditos da engine, fontes, reconhecimento de voz e bibliotecas acompanham os pacotes; consulte CREDITOS.txt e a pasta licenses do jogo.

## O ciclo de jogo

1. Explore o mapa e reúna matéria quando o modo permitir.
2. Formule um pedido: por exemplo, uma arma com projétil e efeito.
3. Confira a prévia, o preço e as restrições.
4. Confirme, recuse ou guarde um pedido na fila.
5. Use, compartilhe ou modifique suas criações e enfrente os objetivos da partida.

As decisões competitivas são do anfitrião: custos, coleta de Caos, pontos, criação e dano precisam concordar em todos os jogadores. Veja [[07 - Pipeline de criacao]] e [[17 - Multiplayer e autoridade]].

## O que a edição atual acrescenta

A expansão inclui combinações de elementos, montaria, ferramentas de física, vestíveis, mais conteúdos, seis jogadores, inventário de seis posições, construções compostas, manipulação regional de terreno, modos de eliminações e bases, Tower Defense cooperativo e um laboratório de inspeção.

Os cenários gerais são **Original, Tokyo 3 e Espaço**. O Tower Defense usa um mapa próprio ligado ao modo. Mapas e modos não são a mesma coisa: [[05 - Modos e regras]] explica as regras; [[16 - Mapas e terreno]] explica a geometria.

## Voz e GPU

A renderização do pacote Windows usa **Direct3D 12 / GPU**. O reconhecimento offline mantido é **sherpa-onnx com Parakeet**, no caminho original de CPU. Não confunda usar GPU para gráficos com ter transferido o reconhecimento de voz para GPU.

No jogo normal, o reconhecimento por voz continua disponível. A conversa de voz entre jogadores vem silenciada por padrão e pode ser alterada na oficina. No laboratório, a voz inicia desligada e os pedidos de teste usam texto.

## Limites importantes

A física adicionada é arcade e usa colisores simples; não é uma simulação mecânica completa de veículos. Móveis das casas são peças de cenário. O desvio de animais é local, não um solucionador geral de labirintos. A confirmação de criação não transforma todas as interações de edição em transações reversíveis.

> [!tip] Para testar uma ideia
> Use primeiro texto no laboratório para separar um problema de interpretação de um problema de microfone. Depois valide o comportamento no jogo normal. Veja [[22 - Depuracao e testes]].

---

[[00 - Comece aqui|Voltar ao índice]]
