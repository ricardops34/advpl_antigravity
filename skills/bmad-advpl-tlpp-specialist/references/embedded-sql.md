# SQL Embutido (Embedded SQL)

Use esta referência ao escrever ou revisar SQL dentro de ADVPL ou TLPP.

## Preferência Padrão

Prefira `BeginSQL ... EndSQL` em vez de concatenação manual de strings `TCQuery` para novas consultas `SELECT`.

## Padrões Obrigatórios

- Use `%table:ALIAS%` para resolução de tabela física.
- Use `%xfilial:ALIAS%` para filtragem de filial.
- Use `%notDel%` para filtragem de exclusão lógica.
- Use `%exp:...%` para valores vinculados (bound values) e expressões.
- Use `GetNextAlias()` e feche o alias quando terminar.

## Padrão Base

```advpl
Local cAlias := GetNextAlias()

BeginSQL Alias cAlias
    SELECT SA1.A1_COD, SA1.A1_NOME
    FROM %table:SA1% SA1
    WHERE SA1.%notDel%
    AND SA1.A1_FILIAL = %xfilial:SA1%
    AND SA1.A1_COD = %exp:cCodCli%
EndSQL

(cAlias)->(DbCloseArea())
```

## Regras

- Não use `SELECT *`.
- Converta datas com `DtoS()` quando exigido pela expressão de consulta.
- Declare tipos de `column` quando tipos de campos de resultado importarem.
- Use sintaxe de `JOIN` explícita.
- Use `TCSqlExec` para `INSERT`, `UPDATE` e `DELETE`; reserve `BeginSQL` para `SELECT`.

## Erros Comuns

- Esquecer o `%notDel%`.
- Esquecer o filtro de filial em tabelas multi-filiais.
- Abrir aliases sem fechá-los.
- Construir SQL dinâmico concatenando valores de usuário em vez de usar `%exp:%`.
