---
title: "Instalar e jogar"
version: mod4-lab1
updated: 2026-11-01
tags:
  - lavoice
  - lavoice/jogar
---

# Instalar e jogar

Na [release atual](https://github.com/Eronponce/LAVOICE-Expandido/releases/tag/mod4), o arquivo **LAVOICE-H4-Expandido-Mod4.zip** é o pacote de jogo. O ZIP original H4 serve como referência da base; o laboratório e a documentação são downloads separados.

## Instalação

1. Extraia o ZIP inteiro para uma pasta gravável.
2. Mantenha LAVOICE.exe, bibliotecas, pasta voice, x86_64 e licenses na organização recebida.
3. Abra LAVOICE.exe. Não execute apenas o EXE arrastado para outra pasta.
4. Para jogar com amigos, todos devem baixar a mesma versão. Uma instalação antiga misturada com arquivos novos pode falhar na compatibilidade.

O pacote é Windows de 64 bits e usa o caminho gráfico Direct3D 12. O reconhecimento offline já acompanha os arquivos de voz. Não é preciso trocar pesos ou instalar outro modelo para usar esta entrega.

## Controles de criação e comunidade

| Entrada | Ação |
| --- | --- |
| T | Digitar um pedido |
| V segurado | Pedir por voz |
| V rápido | Alternar extração de matéria |
| Mouse esquerdo na prévia | Aceitar a criação |
| Mouse direito na prévia | Recusar sem criar |
| Mouse do meio na prévia | Guardar um pedido na fila |
| Backspace | Cancelar a fila |
| 1 a 6 | Selecionar posição do inventário |
| E | Pegar arma próxima |
| G | Largar arma atual |
| F | Montar/sair de uma criação montável próxima |
| M | Mostrar/ocultar minimapa |
| F2 | Editar nick |
| F3 | Perfil, regras e oficina |
| F4 no TD | Anfitrião inicia a próxima onda durante preparação |

Movimento, mira, salto e demais controles podem ser conferidos na tela de opções e no LEIA-ME da distribuição.

## Primeira sessão recomendada

Abra Sandbox, digite **pistola**, leia a prévia e confirme. Faça uma segunda arma: ela deve ir para um espaço livre sem tirar a primeira da seleção. Depois peça **casa completa** e confira a montagem. Teste **gato gigante**, **carro montável** e **armadura de fogo**.

Em modos com economia, o preço importa; no Sandbox a criação não consome matéria ou Caos. No TD o saldo é coletivo. Veja [[19 - Materiais e Caos]].

## Com amigos

A base usa sessões por IP/rede local e transportes existentes. A porta padrão do caminho IP é **UDP 27840**. Ferramentas de rede virtual podem fazer as máquinas se enxergarem, mas não substituem a validação de compatibilidade do jogo.

A validação de seis processos foi local. Firewall, NAT, latência de internet e estabilidade entre computadores precisam de ensaio real. [[17 - Multiplayer e autoridade]] explica a implementação e [[22 - Depuracao e testes]] orienta a reprodução.

---

[[00 - Comece aqui|Voltar ao índice]]
