# Referência Protheus

Use esta referência quando a tarefa depender do conhecimento do framework Protheus em vez de apenas transformação de código.

## Áreas de Consulta de Alto Valor

- Funções nativas como `DbSelectArea`, `DbSeek`, `GetMV`, `FWExecView`, `FWLogMsg`, `MsExecAuto`.
- Tabelas de dicionário SX como `SX1`, `SX2`, `SX3`, `SX5`, `SX6`, `SX7`, `SX9`, `SIX`.
- Estilos de implementação REST: legado `WsRestFul` e padrões mais novos de framework/TLPP.
- Parâmetros MV e comportamento de configuração do `.ini`.

## Referência Rápida SX

| Tabela | Propósito |
|---|---|
| `SX1` | Perguntas e parametrização de rotinas |
| `SX2` | Cadastro de tabelas |
| `SX3` | Dicionário de campos |
| `SX5` | Tabelas genéricas |
| `SX6` | Parâmetros `MV_*` |
| `SX7` | Gatilhos |
| `SX9` | Relacionamentos |
| `SIX` | Índices |

## Disciplina de Consulta

- Prefira primeiro a verdade local do repositório: código existente, wrappers, nomes de campos, índices e includes.
- Se o contexto local for insuficiente, consulte a documentação oficial da TOTVS ou TDN.
- Não invente metadados SX, rotas REST ou semântica de parâmetros MV.

## Heurísticas de Busca

- Documentação de funções: busque pelo nome exato da função mais `ADVPL` ou `TDN`.
- Documentação de framework: busque pela classe de API exata ou nome da anotação.
- Questões de dicionário: confirme o alias e o contexto do módulo antes de responder.
