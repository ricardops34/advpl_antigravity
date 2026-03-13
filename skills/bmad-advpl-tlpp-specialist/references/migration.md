# Migração de ADVPL para TLPP

Use esta referência ao refatorar ADVPL procedural legado para TLPP.

## Estratégia de Migração

1. Leia o fonte `.prw` e liste pontos de entrada públicos, helpers estáticos, variáveis compartilhadas, includes, aliases e chamadas externas.
2. Proponha uma estrutura de classe antes de reescrever.
3. Mova os internos procedurais para uma classe TLPP.
4. Mantenha a `User Function` original como um wrapper de compatibilidade fino, a menos que o usuário queira substituição total.
5. Valide as assinaturas de chamada e efeitos colaterais.

## Mapeamento

| ADVPL | TLPP |
|---|---|
| `User Function X()` | Método público em uma classe, geralmente com wrapper preservado |
| `Static Function helper()` | Método privado |
| Estado compartilhado `Private` | `data` da classe ou estado do construtor |
| Globais `Public` | Remover; passar via parâmetros ou estado da classe |
| Múltiplos includes | Includes `.th` do TLPP correspondentes ao conjunto de funcionalidades |

## Orientações de Namespace

- Para customizações de clientes, use como padrão `custom.<agrupador>.<servico>`.
- Mantenha namespaces em letras minúsculas e separados por pontos.
- Mantenha classes em PascalCase e métodos em camelCase.

## Padrão de Wrapper de Compatibilidade

```advpl
#Include "TOTVS.CH"

User Function CalcPed(cPedido)
    Local oService := custom.faturamento.pedido.PedidoService():new()
Return oService:calcTotal(cPedido)
```

## Checklist de Revisão

- Preserve nomes chamáveis externos enquanto os chamadores ainda dependerem deles.
- Mantenha `GetArea()` e `RestArea()` em torno do acesso ao DB.
- Substitua o estado `Private` vazado por estado de classe explícito.
- Mantenha `xFilial()` e o comportamento de exclusão lógica intactos.
- Prefira o logging do framework em vez de prints ad hoc no novo código TLPP.

## Erros Comuns

- Remover o ponto de entrada antigo cedo demais.
- Criar uma classe TLPP gigante em vez de um serviço focado.
- Traduzir sintaxe sem redesenhar o estado compartilhado.
- Esquecer `::` no acesso a propriedades da classe.
