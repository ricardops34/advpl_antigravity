# 🌌 ADVPL Antigravity: Especialista Protheus

> **Release 1.0.0** - O upgrade definitivo para o seu desenvolvimento TOTVS Protheus com IA.

Repositório oficial da **Skill Especialista** em ADVPL, TLPP e APIs REST para o ecossistema Antigravity/BMAD. Este agente ensina à sua IA as nuances, padrões e "pulos do gato" do ecossistema Protheus que modelos genéricos desconhecem.

---

## 🏗️ O que é esta Skill?

AI Agents (como Claude Code, Cursor ou Gemini) são inteligentes, mas não conhecem os dicionários SX, as regras de `RecLock` ou as particularidades do `BeginSQL` do Protheus. 
Esta **Skill** fornece o contexto técnico necessário para que a IA atue como um Desenvolvedor Protheus Sênior, garantindo código limpo, performático e moderno.

---

## ⚡ Início Rápido (1 minuto)

1. **Instale**:
   ```powershell
   # No Windows (Antigravity Global)
   mkdir "$HOME\.gemini\antigravity\skills\bmad-advpl-tlpp-specialist"
   # Clone ou copie os arquivos para esta pasta
   ```

2. **Verifique**:
   Certifique-se de que o arquivo `SKILL.md` está no caminho correto.

3. **Use agora**:
   > "Use a skill **@bmad-advpl-tlpp-specialist** para criar um CRUD em TLPP."

---

## 🧠 Como Usar

Uma vez instalada, basta invocar o agente naturalmente durante o seu desenvolvimento:

> "Use **@bmad-advpl-tlpp-specialist** para revisar as travas de banco (locks) deste fonte."
> "Como migrar este `.prw` para namespaces do TLPP?"

---

## ⚙️ Compatibilidade e Invocação

Esta skill segue o formato universal **SKILL.md** e funciona com os principais assistentes do mercado.

| Ferramenta      | Tipo | Exemplo de Invocação            | Caminho de Instalação                                                 |
| :-------------- | :--- | :------------------------------ | :-------------------------------------------------------------------- |
| **Antigravity** | IDE  | `(Modo Agente) Use skill...`    | `%USERPROFILE%\.gemini\antigravity\skills\`                           |
| **Claude Code** | CLI  | `>> /skill-name help me...`     | `.claude/skills/`                                                     |
| **Gemini CLI**  | CLI  | `Use o especialista-advpl...`   | `.gemini/skills/`                                                     |
| **Cursor**      | IDE  | `@bmad-advpl-tlpp-specialist`   | `.cursor/skills/`                                                     |

---

## 📦 Estrutura do Projeto

Aqui está como o conhecimento está organizado para a sua IA:

| Caminho | Propósito |
| :--- | :--- |
| `SKILL.md` | O cérebro principal: regras de ativação e fluxo de trabalho. |
| `references/code-generation.md` | Padrões de escrita, prefixos e esqueletos de código. |
| `references/rest-po-ui.md` | Design de APIs e integração com o framework PO-UI. |
| `references/migration.md` | Guia passo a passo para modernização (ADVPL -> TLPP). |
| `references/debugging.md` | Estratégias de diagnóstico de erros e performance. |
| `references/embedded-sql.md` | O guia definitivo para uso do `BeginSQL`. |
| `references/protheus-reference.md` | Consulta rápida aos dicionários SX e funções nativas. |

---

## 🚀 Exemplos Reais

### 1. Modernização de Código
> "Converta esta função que usa Private para uma classe TLPP com atributos protegidos."

### 2. Integração Frontend
> "Desenhe o contrato JSON para uma tabela de 'Pedidos de Venda' que será consumida por um `po-table`."

### 3. Performance SQL
> "Analise esta query e adicione os filtros de filial e exclusão lógica usando as macros corretas."

---

## 🛠️ Solução de Problemas (Windows)

> [!WARNING]
> **Permissões de Symlink**: Se você encontrar erros de "Acesso Negado" ao mover os arquivos, certifique-se de estar executando o terminal como Administrador ou ative o **Modo de Desenvolvedor** no Windows.

---

## 📄 Licença e Créditos

Este projeto é uma adaptação baseada no repositório `adpvl_codex`.
Distribuído sob a licença **MIT**.

---
*Criado com ❤️ por Ricardo para a comunidade Protheus.*
