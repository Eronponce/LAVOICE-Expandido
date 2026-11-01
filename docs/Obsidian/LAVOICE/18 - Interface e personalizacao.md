---
title: "Interface e personalização"
version: mod4-lab1
updated: 2026-11-01
tags:
  - lavoice
  - lavoice/interface
---

# Interface e personalização

A interface deve apresentar o estado do jogo e recolher intenções, sem se tornar outra autoridade de criação. Os componentes principais são **scripts/gameplay/creative_hud.gd**, **creative_menu.gd** e **creation_review.gd**, integrados por **scenes/main.gd**.

## Prévia e confirmação

**scenes/player/shaper.gd** representa a receita e as dimensões. **CreationReview** mostra o que foi entendido, preço, saldo, restrições e os botões. Ela consome o clique de confirmação para impedir que ele também dispare a arma que já estava na mão.

O painel aparece para a prévia local ativa e segue input_enabled. Uma falha de visibilidade pode ser causada pelo jogador congelado, menu aberto ou mudança de modo, não apenas por estilo ou posição.

Uma opção nova precisa funcionar em resoluções diferentes e com texto maior. Confira altura, escala, sobreposição com minimapa e dicas, foco de teclado, cancelamento e uso com inventário cheio.

## Perfil

O nick individual é exibido e sincronizado. F2 abre a edição, com limite de 20 caracteres. Cores e pinturas usam os sistemas existentes; a expansão acrescenta acessórios visuais como coroa, antena, halo e cartola. F3 reúne perfil e regras.

O minimapa está em **scripts/ui_minimap.gd**; as etiquetas de jogadores ficam em **scripts/player_nametag.gd**. As cores também identificam invocações. Não use apenas cor para comunicar uma condição importante se ela puder receber texto ou ícone junto.

## Dicas e histórico

**data/creative_tips.json** contém 291 exemplos/orientações na entrega Mod 4. CreativeHud alterna as dicas no canto superior direito. Uma dica precisa refletir um comando real e as regras atuais: por exemplo, criação exige confirmação e a fila tem uma posição.

Histórico, favoritos e desfazer ajudam a repetir criações. Favoritos do anfitrião/local podem persistir no caminho existente; os de clientes remotos têm limitações de sessão. Não prometa que desfazer restaura dano em personagens ou todo o mapa.

## Conversa e reconhecimento

VoiceReplication controla conversa entre jogadores e inicia silenciada por padrão. O reconhecimento que transforma voz em pedido usa outro caminho, em **scripts/voice/voice_input.gd**. Uma caixa de “silenciar aliados” não deve desligar o reconhecimento do próprio comando.

## Alterar a oficina

1. Acrescente a regra/valor sanitizado no diretor se for regra de partida.
2. Crie o controle na CreativeMenu e mantenha restrições de anfitrião.
3. Exiba o estado autoritativo no HUD.
4. Preserve opções locais, como preferência de conversa, separadas das regras globais.
5. Teste troca de modo, perda/retorno de foco e prévia aberta.

O laboratório usa outro painel, em scripts/dev/debug_lab.gd. Mudar o painel diagnóstico não altera automaticamente o menu normal.

---

[[00 - Comece aqui|Voltar ao índice]]
