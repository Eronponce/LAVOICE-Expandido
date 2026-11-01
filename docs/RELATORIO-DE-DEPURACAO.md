# LAVOICE — laboratório de depuração

Edição separada, baseada no Mod 4, para inspecionar cenários e reproduzir problemas. O executável normal do Mod 4 conserva o SHA-256 original a511bef512ebbebd88342720b1db07c305af485c004a1e2a032e65731bd416a4.

## Ferramentas entregues

- Câmera livre com WASD, Q/E, Shift e giro pelo botão direito.
- F1 alterna inspeção e controle do jogador; F8 troca o ângulo; F9 registra imagem e estado.
- Seletor dos quatro mapas e nove vistas predefinidas.
- Galeria com 28 modelos, enquadramento ajustado ao tamanho e formas de colisão por objeto.
- Pausa, câmera durante a pausa, velocidade 0,25x, criação por texto e início de onda TD.
- Relatos com imagem, câmera, regras, inventário, pedido pendente e estado da partida.
- Auditoria automatizada com imagens e JSON; relatório HTML com filtros.

## Evidência da rodada final

| Cobertura | Resultado |
| --- | --- |
| Auditoria gráfica/física | 638 verificações, 0 falhas |
| Interface do executável | 29 verificações, 0 falhas |
| Capturas | 191 da auditoria + 4 dos controles, 1280 × 720 |
| Mapas | Original, Tokyo 3, Espaço, Tower Defense |
| Spawns | 24, com apoio físico e teste de espaço para cápsula |
| Estruturas fixas | 52 no Original + 67 em Tokyo 3, validadas por dados/corpos |
| Vistas específicas | 8 interiores da cidade; 16 tomadas dos 8 planetas |
| Galeria | 12 construções + 16 animais/veículos/armas/poderes; três ângulos por modelo |
| Física de construções | Porta livre, parede traseira e piso com colisão; dano remove peças e suas colisões |
| Hordas | Primeira onda e sete tipos de torre registrados |
| Controles | Confirmação/cancelamento por mouse, slot livre, pausa, câmera, troca de mapa, colisões e relato |
| Logs finais | Sem SCRIPT ERROR ou ERROR |
| Renderização usada | D3D12 / Forward+ / NVIDIA GeForce RTX 5060 Ti |

A inspeção das imagens orientou correções no laboratório: câmera escondida dentro do personagem nos spawns, enquadramento distante de armas pequenas, colisões removidas ao congelar amostras e título sobreposto ao painel. A bateria de inventário foi ajustada para aguardar o fim real da montagem em vez de contar apenas quadros renderizados.

## Limites

As verificações aprovadas não significam que todos os bugs possíveis foram eliminados. Esta rodada é local/offline: não revalida voz, latência pela internet, seis máquinas diferentes nem todas as combinações de linguagem e efeitos. Os modelos da galeria ficam parados; comportamento real é testado pelo campo Pedido de teste no mundo.

O laboratório inicia com material de teste ilimitado e sem voz. Use o Mod 4 normal para testar economia, Caos, competição, voz e multiplayer. O estado exportado não restaura uma cópia completa do terreno deformado; registre a sequência de pedidos.

Tempos de quadro durante capturas e carregamento servem para diagnóstico, sem equivaler a benchmark de uma partida. A visualização de colisões mostra até 120 formas do objeto e deve ser ocultada ao medir desempenho.

Playwright foi tentado conforme RTK.md, mas o parser do RTK falhou antes da execução. A verificação alternativa foi feita no Godot nativo, com renderização real, eventos de mouse e capturas da interface.

Abra Auditoria-inicial/index.html no pacote ou outputs/Auditoria-LAVOICE/index.html no workspace. Consulte ROTEIRO-DE-TESTES.md para reproduções adicionais.
