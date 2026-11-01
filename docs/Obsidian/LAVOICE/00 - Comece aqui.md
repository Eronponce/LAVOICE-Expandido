---
title: "LAVOICE — comece aqui"
version: mod4-lab1
updated: 2026-11-01
tags:
  - lavoice
  - lavoice/indice
---

# LAVOICE — comece aqui

Este cofre documenta a edição comunitária **LAVOICE H4 Expandido Mod 4**, com o laboratório **mod4-lab1**. É um guia para jogar, compreender a implementação atual e continuar o desenvolvimento sem reconstruir sistemas que já funcionam.

> [!info] Como abrir
> Extraia o ZIP da documentação. No Obsidian, escolha **Abrir pasta como cofre** e selecione a pasta **LAVOICE**. Comece por esta nota. Não precisa instalar plugins comunitários.

## Para quem vai jogar

1. [[01 - O jogo e seu escopo|Entenda a proposta e os limites]].
2. [[03 - Instalar e jogar|Instale e veja os controles]].
3. [[04 - Comandos e exemplos|Experimente pedidos de voz ou texto]].
4. [[05 - Modos e regras|Escolha o modo]], [[19 - Materiais e Caos|entenda a economia]] e [[20 - Tower Defense cooperativo|defenda o núcleo com amigos]].
5. [[18 - Interface e personalizacao|Configure nick, aparência, voz e regras]].

## Para quem vai implementar

Para retomar rapidamente, leia [[CONTEXTO PARA AGENTES]]. Depois comece por [[06 - Arquitetura e arquivos]], [[07 - Pipeline de criacao]] e [[08 - Receitas e dados]]. Depois siga o guia da mudança:

- [[09 - Implementar uma arma]]
- [[10 - Implementar um animal]]
- [[11 - Implementar construcoes]]
- [[12 - Elementos e reacoes]]
- [[13 - Vestiveis e habilidades]]
- [[14 - Fisica e montaria]] e [[15 - IA e perseguicao]]
- [[16 - Mapas e terreno]]
- [[17 - Multiplayer e autoridade]]
- [[21 - Performance e limites]], [[22 - Depuracao e testes]] e [[23 - Build e publicacao]]

[[02 - Do original ao Mod 4|Histórico do original até aqui]] · [[24 - Contribuir e evoluir|Fluxo de contribuição e próximos trabalhos]]

## Convenções deste cofre

Os caminhos citados são relativos à **raiz do projeto Godot recuperado**, como **scripts/autoload/forge.gd**. No workspace de desenvolvimento, essa raiz está em **work/recovered**. Esses caminhos explicam onde trabalhar; não são links para arquivos distribuídos neste cofre.

O repositório público reúne **documentação e binários compilados**. Ele não contém, por si só, o projeto completo com todos os recursos importados necessários para reconstruir o jogo. Consulte [[23 - Build e publicacao]] antes de tentar compilar.

Exemplos identificados como **extensão proposta** ensinam a adicionar algo novo: não significam que esse item já exista na versão publicada. As demais descrições foram conferidas no código e nos relatórios locais da entrega.

> [!note] Cobertura da documentação
> O jogo usa catálogo, regras e padrões de linguagem. Não é um modelo geral capaz de interpretar qualquer frase. A documentação descreve o que existe e distingue sugestões de implementação.

## Fontes desta edição

- PATCH-NOTES-MOD2.md, PATCH-NOTES-MOD3.md e PATCH-NOTES-MOD4.md da distribuição.
- RELATORIO-DE-DEPURACAO.md e relatórios JSON do laboratório.
- Código e dados da versão Mod 4 no projeto Godot recuperado.
- [Repositório e releases](https://github.com/Eronponce/LAVOICE-Expandido).
- [Godot — documentação oficial](https://docs.godotengine.org/en/stable/).
- [Obsidian — links internos](https://help.obsidian.md/links).

---

[[00 - Comece aqui|Voltar ao índice]]
