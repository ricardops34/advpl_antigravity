# Geração de Código ADVPL e TLPP

Use esta referência ao gerar novo código Protheus.

## Regras Principais

- Use os includes Protheus já adotados na base de código.
- Para rotinas ADVPL, use por padrão `#Include "TOTVS.CH"` e adicione `TopConn.ch` apenas quando recursos de DB ou SQL exigirem.
- Prefira variáveis `Local` e prefixos de estilo húngaro (`c`, `n`, `d`, `l`, `a`, `o`, `b`, `x`).
- Envolva o trabalho de DB com `GetArea()` e `RestArea()`.
- Adicione tratamento de erro defensivo em rotinas que tocam DB, serviços externos, E/S de arquivos ou pontos de entrada do framework.

## Nomenclatura

- User Function: prefixo do módulo seguido do identificador de negócio, ex: `FATA050`, `MATA030`, `FINA460`.
- Helper estático: PascalCase ou camelCase descritivo.
- Classe TLPP: PascalCase com um sufixo claro como `Service`, `Repository`, `Controller`, `Dto`.
- Método TLPP: camelCase.

## Esqueleto de User Function ADVPL

```advpl
#Include "TOTVS.CH"

User Function FATA001(cCodCli)
    Local lOk     := .T.
    Local aArea   := GetArea()

    Begin Sequence
        // Implementar lógica de negócio
    Recover Using oError
        lOk := .F.
        FWLogMsg("INFO",, "ERRO", "FATA001", "", "01", oError:Description, 0, 0, {})
    End Sequence

    RestArea(aArea)
Return lOk
```

## Esqueleto de Classe TLPP

```tlpp
#Include "tlpp-core.th"

namespace custom.faturamento.pedido

class PedidoService
    public method new() as object
    public method process(cPedido as character) as logical
endclass

method new() class PedidoService
return self

method process(cPedido as character) class PedidoService
    local lOk := .T.
return lOk
```

## Orientações MVC

- Mantenha `MenuDef`, `ModelDef` e `ViewDef` alinhados com o padrão MVC existente no projeto.
- Reutilize aliases existentes, metadados SX3 e convenções de browse do mesmo módulo sempre que possível.
- Evite inventar estruturas de campo sem verificar o uso atual no projeto.

## Orientações REST

- Prefira o estilo REST já usado no projeto: TLPP baseado em anotações ou legado `WsRestFul`.
- Valide os payloads explicitamente.
- Normalize as respostas e o tratamento de erros em vez de retornar exceções internas brutas.
- Se a API for destinada a um frontend PO-UI, leia também `references/rest-po-ui.md`.

## Orientações para Pontos de Entrada

- Mantenha a assinatura exatamente compatível com a invocação esperada pelo framework.
- Preserve ou documente os efeitos colaterais necessários em arrays, parâmetros e valores de retorno.

## Erros Comuns

- Esquecer `RestArea(aArea)` após acesso ao DB.
- Usar `Private` ou `Public` em novo código.
- Chumbas a filial em vez de usar `xFilial()`.
- Omitir filtros de exclusão lógica ao consultar tabelas.
