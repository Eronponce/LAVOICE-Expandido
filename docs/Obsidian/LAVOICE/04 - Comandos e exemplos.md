---
title: "Comandos e exemplos"
version: mod4-lab1
updated: 2026-11-01
tags:
  - lavoice
  - lavoice/comandos
---

# Comandos e exemplos

Use uma frase curta, confira a prévia e acrescente complexidade aos poucos. O catálogo da distribuição é mais amplo que esta seleção. O parser usa termos cadastrados e padrões estruturais; uma palavra desconhecida não ganha comportamento automaticamente.

## Pedidos de criação

| Experimento | Pedido de exemplo |
| --- | --- |
| Arma comum | pistola |
| Combinar projétil e efeito | metralhadora que atira pombos explosivos |
| Elementos juntos | laser de fogo e gelo |
| Escala de animal | gato gigante |
| Montável fora da mão | carro montável |
| Física arcade | ponte com física |
| Ferramenta | raio encolhedor |
| Manipular gravidade | arma antigravidade |
| Roupa | armadura de fogo |
| Mobilidade | jetpack |
| Visibilidade | visão noturna |

A interpretação exata de uma composição deve ser conferida no painel **Entendi**. Um pedido pode ter significado válido sem resultar no comportamento que você imaginou. [[07 - Pipeline de criacao]] mostra como investigar isso.

## Construções completas

- **casa completa**: pede casa mobiliada.
- **casa de 3 andares**: usa a estrutura composta com pisos e escadas.
- **casa largura 12 altura 6 comprimento 10**: dimensões explícitas.
- **casa 12 x 6 x 10**: ordem largura × altura × profundidade.
- **ponte de aço**, **torre de pedra**, **fortaleza**, **prisão**, **labirinto**.
- **quatro paredes formando uma caixa ao meu redor**.

Há limites de dimensões, andares e peças; eles protegem a montagem e a rede. Móveis são cenográficos. Veja [[11 - Implementar construcoes]].

## Edição e terreno

Mire no alvo adequado antes do pedido:

- **duplique aquela torre**
- **transforme essa parede em aço**
- **mova aquela construção**
- **faça essa criatura proteger minha base**
- **marcar região** e depois um pedido de **fogo no chão**, **gelo no terreno**, **lava**, **cratera**, **terremoto** ou **montanha**

A seleção contextual é controlada por código e pelas regras do modo. Ela não identifica semanticamente toda árvore ou montanha citada em uma frase. Marcar uma região fornece contexto geométrico pela mira. TD bloqueia ações que prejudicariam as rotas e a economia.

## Organização e compartilhamento

**largar arma**, **pegar arma**, **salvar favorito nome**, **usar favorito nome**, **desfazer** e **iniciar onda** são comandos do interpretador avançado. Desfazer é limitado ao histórico implementado: não reverte toda a partida, dano em jogadores ou qualquer alteração arbitrária.

> [!tip] Separar falhas
> Se o texto funciona e a voz não, investigue áudio/transcrição. Se a receita está errada, investigue o léxico ou interpretador. Se a receita está certa e o objeto falha, investigue montagem, execução ou rede. Veja [[22 - Depuracao e testes]].

---

[[00 - Comece aqui|Voltar ao índice]]
