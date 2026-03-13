# API REST e PO-UI para Protheus

Use esta referência ao construir um backend Protheus em ADVPL ou TLPP que será consumido por um frontend PO-UI.

## Escopo

- Endpoints REST em ADVPL ou TLPP para Protheus.
- Contratos de integração entre Protheus e telas PO-UI.
- Endpoints de CRUD, busca, paginação e detalhe.
- Fluxo de autenticação e autorização entre frontend e backend.
- Modelagem de resposta para tabelas, formulários e notificações PO-UI.

## Arquitetura

- Mantenha as regras de negócio nas rotinas de serviço do Protheus, não no frontend PO-UI.
- Use a camada REST como o limite do contrato.
- Normalize os payloads JSON para que o frontend não precise de regras de parsing específicas do Protheus.
- Reutilize a validação e lógica de transação existentes no Protheus sempre que possível.

## Orientações de Backend

- Prefira o estilo REST já usado no projeto: `WsRestFul` em ADVPL ou TLPP baseado em anotações onde disponível.
- Separe as responsabilidades em:
  - Endpoint/Controller
  - Service/Lógica de Negócio
  - Repository ou camada de Query
- Valide a entrada no limite da API.
- Retorne semântica HTTP clara onde o framework suportar.
- Padronize payloads de erro com mensagem, código e detalhes opcionais.

## Formatos de Endpoint Sugeridos

- `GET /api/clientes`
  - Suporte a filtros, page, pageSize, search.
- `GET /api/clientes/{id}`
  - Retorna o recurso com campos derivados já formatados para uso na UI quando apropriado.
- `POST /api/clientes`
- `PUT /api/clientes/{id}`
- `DELETE /api/clientes/{id}`

## Design de Resposta para PO-UI

Prefira contratos JSON estáveis como:

```json
{
  "items": [],
  "hasNext": false,
  "page": 1,
  "pageSize": 20,
  "total": 0
}
```

Para formulários:

```json
{
  "id": "000001",
  "nome": "Cliente Exemplo",
  "loja": "01",
  "ativo": true
}
```

Para erros:

```json
{
  "error": true,
  "code": "CLIENTE_NAO_ENCONTRADO",
  "message": "Cliente não encontrado"
}
```

## Orientações de Frontend PO-UI

- Use componentes PO-UI para produtividade, não para esconder contratos de backend fracos.
- Mapeie coleções de backend para `po-table`.
- Mapeie fluxos de criação e atualização para `po-dynamic-form` ou formulários Angular tipados, dependendo dos padrões do projeto.
- Mantenha os serviços de API isolados em classes de serviço Angular.
- Centralize o tratamento de URL de ambiente e tokens.
- Trate identificadores específicos do Protheus como filial, código, loja e recno como campos de domínio com nomes explícitos.

## Checklist de Integração

- Confirmar CORS, headers de autenticação e URL base do ambiente.
- Confirmar formatos de data e decimais JSON esperados pelo frontend.
- Confirmar contrato de paginação antes de implementar a tela de tabela.
- Confirmar se o backend retorna erros de domínio ou erros genéricos do framework.
- Confirmar se as telas PO-UI precisam de endpoints de lookup para combos e autocomplete.

## Erros Comuns

- Retornar aliases brutos ou nomes de campos SX diretamente para o frontend sem um contrato estável.
- Embutir regras de negócio apenas no Angular e ignorar a validação do Protheus.
- Misturar lógica de paginação entre frontend e backend.
- Retornar formatos de erro inconsistentes entre endpoints.
