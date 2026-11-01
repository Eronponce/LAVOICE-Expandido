---
title: "Contribuir e evoluir"
version: mod4-lab1
updated: 2026-11-01
tags:
  - lavoice
  - lavoice/contribuir
---

# Contribuir e evoluir

Uma mudança boa preserva os contratos existentes e demonstra o novo comportamento com um caso pequeno. A documentação deve ser atualizada junto da implementação, sem prometer tudo o que foi sugerido como ideia.

## Antes de editar

1. Leia [[CONTEXTO PARA AGENTES]] e identifique a versão de partida.
2. Consulte [[06 - Arquitetura e arquivos]] e localize o dono do comportamento.
3. Reproduza o problema sem voz para separar reconhecimento e execução.
4. Preserve snapshot e binários imutáveis.
5. Defina o resultado esperado e os testes que o distinguem do comportamento atual.

## Escolher o menor ponto de extensão

| Mudança | Começar por |
| --- | --- |
| Nome/sinônimo | Léxico, mantendo o mesmo ID |
| Aparência | Modelo e materiais |
| Número de dano/custo/velocidade | Balance e política de custo |
| Outra combinação conhecida | Recipe ou macro, sem novo executor |
| Nova forma de casa | StructureGeometry e interpretação do plano |
| Nova ação de combate | ThingAction, registro e consumidores autoritativos |
| Novo modo | GameplayDirector, regras sanitizadas e replicação |
| Falha em obstáculos | Corpo/MoveChaseEnemy, com reprodução física |
| Interface | HUD/menu, sem mover regras para o cliente |

## Critérios de conclusão

Uma criação nova deve ser reconhecida, mostrada na prévia, cobrada corretamente, montada, usada, removida e replicada. Uma habilidade precisa expirar e limpar. Um modo precisa iniciar, terminar, reiniciar e trocar de mapa sem deixar entidades antigas. Um efeito precisa respeitar equipes, limites e autoridade.

Verifique também cancelamento, recurso insuficiente, fila cheia, inventário cheio, morte, saída do dono e limites de rede. A feature feliz sozinha não é o contrato completo.

## Próximos trabalhos possíveis

- Navegação global adaptada à destruição e à gravidade, além do desvio local atual.
- Melhor organização/iluminação de interiores e construção com edição mais granular.
- Salvamento de cenas/terreno, distinguindo snapshot diagnóstico de replay completo.
- Ensaios com seis máquinas em internet real e cenários de reconexão/latência.
- Matriz de teste de voz com ruído e sotaques mantendo o modelo simples.
- Modos Apocalipse, Rei da Colina e preparação dedicada de bases, se forem especificados.

Esses itens são propostas, não funcionalidades declaradas como prontas. Antes de implementar, defina regras, orçamento de entidades, autoridade, UI, custo e critérios de teste.

## Documentação de uma mudança

Anote problema, comportamento final, arquivos alterados, comandos de exemplo, formato novo, decisões e evidência de teste. Atualize o guia de implementação afetado e o histórico da release. Não copie fonte recuperada integral, dados privados, chave ou caminhos absolutos do computador para o cofre público.

O repositório de distribuição permanece voltado a documentação e pacotes. Uma evolução para publicar fontes completos exige avaliar separadamente os recursos disponíveis e as autorizações aplicáveis; não é consequência automática de escrever um guia.

---

[[00 - Comece aqui|Voltar ao índice]]
