# Verificação de desempenho — Mod 4

A análise focou perseguição, criação de malhas e limites das hordas. A alteração foi feita no projeto recuperado, que não é um repositório Git; o repositório de publicação existente não foi alterado.

- **Alto — busca de alvos repetida:** antes ocorria a cada passo de cada perseguidor. Agora cada animal atualiza seu alvo a 5 Hz, e consultas próximas no tempo usam uma lista comum de candidatos por passo de física. No teste determinístico de 120 passos foram 10 atualizações, contra 120 no caminho antigo.
- **Médio — malhas repetidas:** modificadores de vida e rota deixaram de produzir novas entradas de geometria. O teste confirmou que dois animais com vidas e rotas diferentes usam a mesma malha.
- **Médio — composição de Caos:** resultados por receita e catálogo ficam em cache com limite de 256 entradas.
- **Médio — acúmulo de entidades:** limite de 32 animais ativos, espera por capacidade de rede e remoção de projéteis antigos antes de construções. O teste de carga confirmou o limite.
- **Médio — áudio silenciado:** o caminho silenciado não cria tocadores de áudio nem decodifica e enfileira PCM para reprodução local. A validação e o encaminhamento do host continuam funcionando.

Verificação: testes nativos passaram; rede cooperativa passou com seis processos. Não foi realizado benchmark de FPS com renderização ou computadores diferentes. Os números acima medem consultas de alvo, não FPS.

◆ Análise e verificação
- Gargalos identificados: passou.
- Alterações autorizadas pelo pedido de implementação e desempenho: passou.
- Testes de regressão e recursos novos: passou.
- Limites e reaproveitamento de malhas: passou.
- Resultado: PASS para as verificações automatizadas; desempenho visual em partida real ainda precisa de teste.
