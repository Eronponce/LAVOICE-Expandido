---
title: "Depuração e testes"
version: mod4-lab1
updated: 2026-11-01
tags:
  - lavoice
  - lavoice/testes
---

# Depuração e testes

A validação deve separar parser, regras, física, apresentação e rede. Comece por uma reprodução pequena, registre o pedido exato e só depois acrescente efeitos e jogadores.

## Laboratório entregue

Abra o pacote separado LAVOICE-Laboratorio. **ABRIR-LABORATORIO.bat** entra na ferramenta interativa. **AUDITAR-TUDO.bat** percorre a bateria gráfica e fecha ao concluir; relatórios ficam em Diagnosticos, com uma pasta por sessão.

| Controle | Função |
| --- | --- |
| F1 | Inspeção ou jogador |
| WASD + Q/E | Movimento da câmera |
| Shift | Acelerar câmera |
| Botão direito arrastado | Girar câmera |
| F8 | Próxima vista predefinida |
| F9 | Imagem e estado do relato |

Há seletor de mapas/modelos, pausa, 0,25x e desenho de colisões. A galeria mantém amostras paradas. Para IA, montagem, disparos e veículos em ação, use o campo de pedido no mundo. O laboratório é offline, sem voz e com materiais livres de teste.

## Evidência preservada

| Rodada | Resultado |
| --- | --- |
| Regressão nativa Mod 4 | 7.717 verificações |
| Recursos anteriores | 206 verificações |
| Novos recursos Mod 4 | 59 verificações |
| Total local do jogo | 7.982 aprovadas |
| Rede, host + cinco clientes locais | 245 aprovadas |
| Auditoria gráfica/física do laboratório | 638 aprovadas |
| Controles do laboratório | 29 aprovadas |
| Capturas do laboratório | 191 da auditoria + 4 dos controles |

Os testes do laboratório abrangem quatro mapas, seis spawns por mapa, nove vistas gerais, edifícios/interiores selecionados, oito planetas, 28 modelos, colisões básicas, destruição parcial e primeira onda com sete torres. Os logs finais dessa rodada não registraram SCRIPT ERROR ou ERROR.

Esses resultados são evidência da entrega, não promessa de ausência de bugs. Não cobrem todas as frases, todas as sequências de deformação, todos os labirintos, voz em ambientes diferentes nem latência real de internet.

## Fixtures locais do desenvolvimento

Os arquivos de teste disponíveis no projeto recuperado incluem **mod_validation.gd/.tscn**, **mod3_validation.gd/.tscn**, **mod4_validation.gd/.tscn** e **network4_validation.gd/.tscn**. Eles não precisam integrar a cena principal do pacote normal.

Para rodar no motor original, a sessão usou PCKs/EXEs de teste com uma cena inicial dedicada. A distribuição customizada não foi validada simplesmente passando --script para o EXE normal. Veja [[23 - Build e publicacao]].

## Relato reproduzível

Registre versão/hash, modo/mapa, host ou cliente, texto exato, ações, esperado, ocorrido e frequência. Guarde imagem, relatorio.json e log da sessão. O snapshot diagnóstico registra câmera, regras, inventário e pedido pendente; não é um salvamento completo do terreno modificado.

Teste uma consulta física positiva: por exemplo, a parede deve bloquear e a porta deve deixar passar. Uma consulta na camada errada pode dar “livre” para todos os casos e esconder uma falha do teste.

## Ambiente de validação

A tentativa de Playwright falhou no parser do RTK antes de executar. O fallback foi o Godot nativo com eventos de mouse, física e captura GPU. Nesta documentação, a conferência é estática: links, caminhos, exemplos e coerência com os arquivos; não é alegado um novo ensaio visual no Obsidian.

Ao iniciar processos Windows fora do shell normal, confira APPDATA/LOCALAPPDATA. O ambiente usado por algumas chamadas Node não ofereceu a pasta de usuário ao Godot; os ensaios finais via PowerShell usaram o ambiente Windows correto e cache de shaders disponível.

---

[[00 - Comece aqui|Voltar ao índice]]
