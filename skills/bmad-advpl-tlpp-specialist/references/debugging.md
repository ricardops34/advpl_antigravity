# Depuração em ADVPL e TLPP

Use esta referência ao diagnosticar problemas de compilação, runtime, locks ou performance.

## Ordem de Triagem

1. Capture o texto exato do erro, rotina falhando e caminho de reprodução.
2. Decida se o problema é de compilação, runtime, DB/lock ou performance.
3. Inspecione tipos de variáveis, aliases ativos, ordem de índice, filtro de filial e tratamento de lock próximo à linha falha.
4. Adicione logs temporários apenas onde eles estreitam o caminho de falha.
5. Valide a correção e remova diagnósticos ruidosos.

## Verificações Rápidas

| Sintoma | Primeira Verificação |
|---|---|
| `Variable does not exist` | Erro de digitação na declaração, escopo, branch não acessada |
| Incompatibilidade de tipo ou acesso NIL | `ValType()` e nulidade antes da operação |
| Alias inválido | Ordem do `DbSelectArea()` e se o alias está aberto |
| Timeout de lock | `RecLock(cAlias, .F.)`, caminho de unlock, editor concorrente |
| Rotina lenta | `DbSetOrder()` errado, table scan, queries em loop, crescimento de array |

## Logging

- Use `Conout()` para depuração local de curta duração.
- Prefira `FWLogMsg()` para diagnósticos estruturados da aplicação.
- Evite `MsgAlert()` para solução de problemas no lado do servidor.

## Padrão de Captura de Erro

```advpl
Local oError
Local bOldError := ErrorBlock({|e| oError := e, Break(e)})

Begin Sequence
    // código de risco
Recover Using oError
    Conout("Erro: " + oError:Description)
End Sequence

ErrorBlock(bOldError)
```

## Checklist de Lock

- Sempre teste o retorno do `RecLock()`.
- Sempre execute `MsUnlock()` após um lock bem-sucedido.
- Mantenha a janela de lock curta.
- Bloqueie registros em uma ordem consistente quando mais de um registro for tocado.

## Checklist de Performance

- Confirme se a chave de busca corresponde ao índice ativo.
- Prefira uma query SQL em vez de N buscas repetidas dentro de loops.
- Use SQL embutido para filtragem e agregação complexas.
- Feche aliases temporários prontamente.
