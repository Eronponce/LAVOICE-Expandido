---
title: "Modos e regras"
version: mod4-lab1
updated: 2026-11-01
tags:
  - lavoice
  - lavoice/modos
---

# Modos e regras

A configuração principal está em **scripts/gameplay/gameplay_director.gd**, em DEFAULTS e sanitize(). A interface F3 apresenta regras; o anfitrião decide as regras online. Aplicar uma troca de modo reinicia a partida, preservando a sessão pelo fluxo de transição da rede.

| Modo | Objetivo | Economia e renascimento |
| --- | --- | --- |
| Rodadas | Duelo original por rodadas | Fluxo de rodada preservado |
| Sandbox | Criar e experimentar livremente | Sem custo de matéria ou Caos |
| Eliminações | Atingir o objetivo de eliminações | Placar, renascimento e proteção configuráveis; Caos |
| Bases | Destruir o núcleo rival e eliminar a equipe | Dois times; sem núcleo, a equipe deixa de renascer; Caos |
| Tower Defense | Defender núcleo contra ondas | Um time cooperativo, materiais compartilhados e torres em pontos permitidos |

## Corrida de Eliminações

O padrão de objetivo é 25, com configuração de 1 a 1.000. O renascimento padrão é de 3 segundos e a proteção padrão também é de 3 segundos; os valores são sanitizados pelo host. Eliminações e mortes têm contadores separados. Equipes são opcionais.

Não incremente o placar no HUD: ele deve refletir o estado autoritativo. Para alterar regras de pontuação, trabalhe no diretor e replique o snapshot; veja [[17 - Multiplayer e autoridade]].

## Invasão de Bases

Há duas equipes equilibradas, até 3 contra 3 com seis jogadores. O modo força equipes e cria um núcleo por equipe com jogador correspondente. A destruição do núcleo impede novos renascimentos daquele time; a equipe ainda precisa ser eliminada para encerrar a disputa.

A resistência das construções e o limite de dano por impacto evitam que uma única bala apague um prédio. Não equivale a tornar construções indestrutíveis.

## Tower Defense

O modo força cooperação e desliga loot aleatório, eventos naturais e regeneração de terreno nas regras sanitizadas. A economia e a colocação de torres têm regras próprias. Consulte [[20 - Tower Defense cooperativo]] antes de mudar qualquer uma delas.

## Ajustar uma regra com segurança

1. Adicione o valor padrão em DEFAULTS.
2. Defina tipo e faixa em sanitize().
3. Acrescente a opção na oficina e descreva o efeito.
4. Faça o host aplicar e incluir o valor no estado necessário.
5. Teste limites, troca de modo com entidades ativas e todos os clientes.

> [!note] Valores pedidos não são valores confiáveis
> sanitize() copia apenas chaves conhecidas com o tipo correto e limita faixas. Regras recebidas de interface ou rede continuam precisando dessa validação.

Modos Apocalipse, Rei da Colina e uma fase dedicada de construção antes de lutar não foram entregues como sistemas próprios. Não confunda o TD por ondas com esses modos futuros. [[24 - Contribuir e evoluir]] sugere como planejar a evolução.

---

[[00 - Comece aqui|Voltar ao índice]]
