---
name: bmad-advpl-tlpp-specialist
description: Especialista em desenvolvimento no ecossistema TOTVS Protheus com ADVPL e TLPP. Use quando trabalhar em arquivos `.prw`, `.tlpp`, `.prx`, `.ch`, `.th` ou tarefas específicas do Protheus como geração de rotinas, MVC, APIs REST, integrações PO-UI, pontos de entrada, SQL embutido, revisão de customizações, migração de ADVPL legado para TLPP, depuração de problemas de AppServer/runtime ou consulta a convenções do framework Protheus e dicionário SX.
---

# Specialist ADVPL/TLPP Protheus

Use esta skill como ponto de entrada para qualquer trabalho no Protheus. Mantenha o fluxo eficiente: identifique o tipo de tarefa, carregue apenas o arquivo de referência relevante e implemente ou revise o código usando as convenções do Protheus em vez de hábitos genéricos de xBase.

## Fluxo de Trabalho

1. Detecte se a solicitação é primariamente geração de código, integração REST e PO-UI, migração, depuração, SQL embutido ou consulta de referência.
2. Leia apenas o arquivo correspondente em `references/`.
3. Inspecione o repositório atual antes de alterar o código. Prefira nomes existentes, prefixos de módulos, includes, wrappers e padrões de framework já usados no projeto.
4. Preserve a segurança de runtime do Protheus:
   - Prefira variáveis `Local`.
   - Salve e restaure áreas de trabalho (`GetArea`/`RestArea`) ao acessar o DB.
   - Valide o `RecLock()` e sempre execute o `MsUnlock()`.
   - Use `xFilial()` e filtros de exclusão lógica (`!D_E_L_E_T_`).
5. Mantenha a compatibilidade retroativa, a menos que o usuário peça explicitamente para quebrá-la. Em migrações, preserve o ponto de entrada chamável usado pelas rotinas existentes.

## Seleção de Referência

- Para novas rotinas, classes, MVC, REST, SOAP ou pontos de entrada: `references/code-generation.md`.
- Para design de backend REST Protheus, contratos, fluxo de autenticação e integração com PO-UI: `references/rest-po-ui.md`.
- Para modernização de `.prw` para `.tlpp` ou refatoração baseada em wrapper: `references/migration.md`.
- Para erros de compilação, problemas de NIL/tipo, problemas de AppServer, lock/concorrência ou rotinas lentas: `references/debugging.md`.
- Para `BeginSQL`, `EndSQL`, `%table%`, `%notDel%`, `%xfilial%`, `%exp%`, `TCQuery` ou `TCSqlExec`: `references/embedded-sql.md`.
- Para funções nativas, tabelas SX, parâmetros MV, convenções de framework REST ou consulta orientada ao TDN: `references/protheus-reference.md`.

## Detecção de Projeto

Trate o repositório como orientado a Protheus ao encontrar um ou mais destes sinais:

- Arquivos fonte com `.prw`, `.tlpp`, `.prx`, `.ch`, `.th`.
- Includes como `TOTVS.CH`, `TopConn.ch`, `FWMVCDef.ch`, `tlpp-core.th`, `tlpp-rest.th`.
- Uso de `DbSelectArea`, `DbSeek`, `RecLock`, `MsUnlock`, `FWExecView`, `FWLogMsg`, `BeginSQL`.
- Aliases ou tabelas como `SA1`, `SB1`, `SC5`, `SC6`, `SE1`, `SE2`, `SX*`, `SIX`.

## Regras de Saída

- Escreva código que se ajuste primeiro ao estilo do projeto existente, e em segundo lugar às convenções oficiais do Protheus.
- Prefira implementações concretas em vez de conselhos abstratos quando o usuário pedir código.
- Mantenha os comentários esparsos e úteis.
- Quando estiver em dúvida sobre um campo SX, índice ou parâmetro MV, diga isso explicitamente e evite inventar metadados de dicionário.
