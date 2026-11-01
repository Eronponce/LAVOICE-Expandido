---
title: "Build e publicação"
version: mod4-lab1
updated: 2026-11-01
tags:
  - lavoice
  - lavoice/build
---

# Build e publicação

A entrega foi construída preservando o executável e os recursos importados da distribuição original, com patches de dados e bytecode. O repositório público é de documentação e pacotes compilados; um clone não contém automaticamente todos os recursos necessários para refazer o jogo.

## Pré-requisitos locais

- Distribuição H4 original autorizada e cópia de segurança.
- Projeto recuperado que corresponde à versão em alteração.
- Godot **4.7.2** usado na verificação do projeto e engine original compatível.
- GDRETools/gdsdecomp da ferramenta local usada para compilar e aplicar patches.
- Chave PCK necessária ao fluxo local, mantida fora do Git, do cofre e dos pacotes de documentação.
- Manifesto de mudanças e diretório de saída novo.

> [!important] Segredo local
> Este cofre não contém nem ensina a publicar a chave. Não copie arquivos de descoberta de chave, logs com segredo ou argumentos expandidos para o GitHub. Nos exemplos, LAVOICE_PCK_KEY é apenas uma variável privada já configurada localmente.

## Fluxo de trabalho

1. Preserve a versão distribuída e faça snapshot dos fontes antes de editar.
2. Edite apenas os arquivos necessários e valide JSONs/classes no projeto.
3. Rode importação/verificações no Godot oficial compatível.
4. Compile scripts alterados em bytecode compatível.
5. Aplique patches ao pacote original/última versão, sempre em outro arquivo.
6. Inclua cenas, dados, remaps e cache de classes necessário.
7. Rode o EXE nativo resultante, inclusive rede quando aplicável.
8. Monte uma pasta completa de distribuição, com voz, DLLs, créditos/licenças.
9. Gere manifesto SHA-256, ZIP e confira os arquivos descompactados.
10. Publique notas que descrevem o resultado real e seus limites.

## Exemplo de compilação local

O caminho observado compila para um arquivo .gdc no diretório de trabalho, pelo basename do script. Evite basenames iguais em lotes diferentes sem mapear o resultado.

~~~powershell
# Exemplo: variáveis apontam para ferramentas e arquivos locais.
& $rtk proxy $gdre --headless --bytecode=4.7.2 "--compile=$source/scripts/dev/debug_lab.gd"
~~~

O texto do remap correspondente é:

~~~ini
[remap]

path="res://scripts/dev/debug_lab.gdc"
~~~

No patch, o .gdc vai para o caminho .gdc e o remap vai para **scripts/dev/debug_lab.gd.remap**. Uma cena que referencia o .gd usa esse remap no pacote compilado.

## Exemplo de patch

~~~powershell
& $rtk proxy $gdre --headless "--pck-patch=$baseExe" "--key=$env:LAVOICE_PCK_KEY" "--output=$newExe" "--patch-file=$compiled=res://scripts/dev/debug_lab.gdc" "--patch-file=$remap=res://scripts/dev/debug_lab.gd.remap" "--embed=$originalExe"
~~~

Trate esse comando como modelo para adaptar, não como um instalador pronto. Nunca use o mesmo arquivo como entrada e saída. Arquivos publicados que têm hardlinks locais também devem permanecer imutáveis. Muitos argumentos de patch podem exceder o limite de linha do Windows: use lotes e intermediários controlados.

## Cenas e classes de teste

Para um executável de teste, foi gerado project.binary com outra application/run/main_scene e diretório de usuário próprio. Novas classes globais podem exigir a atualização de **.godot/global_script_class_cache.cfg** no pacote, além do bytecode. Uma classe nova compilar isoladamente não prova que o EXE conseguirá resolvê-la.

Não reexporte indiscriminadamente GLBs recuperados: a recuperação pode ser imperfeita e alterar modelos/imports/checksums do robô. Preserve os recursos importados originais e aplique patches pontuais. Isso também evita quebrar a compatibilidade online.

## Argumentos e ambiente

As flags da engine vêm antes de **--**. Os argumentos do jogo lidos por MobileDev vêm depois: --sem-voz, --auditar e --saida são exemplos de argumentos da ferramenta, não do editor. Preserve um caminho absoluto válido para os resultados dos fixtures.

Para testes gráficos finais, use o ambiente Windows normal por PowerShell/RTK. Certas execuções por Node no ambiente de desenvolvimento ficaram sem APPDATA e provocaram erros de pasta de usuário/cache de shader que não eram falhas de gameplay. Não apague configuração do jogador para mascarar esse problema de lançamento.

Estados de retomada locais: **work/MOD4-STATE.json**, **work/DEBUG-LAB-STATE.json** e **work/patch-plan-mod4.json**. A fonte recuperada não é um repo Git; o repo público docs-only fica em work/github-release. O snapshot anterior ao laboratório é work/mod4-source.

## Releases

Inclua o jogo completo Mod 4, laboratório separado, documentação e checksums. Diferencie o ZIP original de referência do pacote recomendado para jogar. Todos precisam usar a mesma versão Mod 4 na partida. Não distribua os arquivos experimentais de teste como se fossem o executável normal.

O protocolo só deve ser alterado com consciência dos formatos/semântica em [[17 - Multiplayer e autoridade]]. Não faça um bump para esconder erro de manifesto ou de recurso corrompido.

---

[[00 - Comece aqui|Voltar ao índice]]
