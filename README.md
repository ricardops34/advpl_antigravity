# ADVPL Antigravity - Especialista Protheus

Repositório oficial da skill especializada em desenvolvimento TOTVS Protheus (ADVPL/TLPP) para o ecossistema Antigravity.

## 🚀 Visão Geral

Este agente foi projetado para elevar a produtividade de desenvolvedores Protheus, fornecendo suporte inteligente para geração de código, migração de legado, APIs REST modernas e integração com PO-UI. Baseado nos padrões de excelência do repositório `adpvl_codex`.

## 🛠️ Pré-requisitos

- **Ambiente Antigravity**: Este agente é uma "Skill" para ser utilizada com assistentes baseados no framework Antigravity/BMAD.
- **Visual Studio Code**: Recomendado para edição e interação com o agente.
- **Acesso ao Git**: Necessário para clonar este repositório e manter as referências atualizadas.

## 📦 Instalação

### Instalação Manual

1. Localize a pasta de skills do seu ambiente Antigravity:
   - **Windows**: `%USERPROFILE%\.gemini\antigravity\skills\`
2. Crie uma pasta chamada `bmad-advpl-tlpp-specialist`.
3. Copie o conteúdo da pasta `skills/bmad-advpl-tlpp-specialist` deste repositório para a pasta criada no passo anterior.

### Estrutura de Pastas Esperada

```text
skills/
└── bmad-advpl-tlpp-specialist/
    ├── SKILL.md
    └── references/
        ├── code-generation.md
        ├── rest-po-ui.md
        ├── migration.md
        ├── debugging.md
        ├── embedded-sql.md
        └── protheus-reference.md
```

## 💡 Exemplo de Uso

Uma vez instalado, o agente é ativado automaticamente ao abrir arquivos `.prw` ou `.tlpp`. Você pode solicitar:

### 1. Criar um novo serviço REST
> "Crie uma classe TLPP para um serviço de consulta de pedidos (SC5/SC6) seguindo os padrões REST e compatível com PO-UI."

### 2. Migrar código antigo
> "Refatore esta User Function legada para uma classe TLPP usando Namespaces e métodos camelCase."

### 3. Otimizar Consultas
> "Analise este DbSeek e transforme em um BeginSQL otimizado com filtro de filial e exclusão lógica."

## 📚 Referências Incluídas

- **Geração de Código**: Padrões de variáveis e esqueletos.
- **REST & PO-UI**: Contratos JSON estáveis e integração Angular.
- **Migração**: Estratégias de Modernização ADVPL -> TLPP.
- **Depuração**: Checklist de erros comuns e logs.
- **SQL Embutido**: Melhores práticas de `BeginSQL`.
- **Dicionário Protheus**: Referência rápida de tabelas SX.

## 📄 Licença

Este projeto está sob a licença MIT. Sinta-se à vontade para contribuir!

---
*Desenvolvido por Ricardo e Antigravity AI.*
