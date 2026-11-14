# Agentes de Design para o Claude Code

Três subagentes do [Claude Code](https://claude.com/claude-code) para o dia a dia de Product Design: revisão de acessibilidade, crítica de design e pesquisa de UX.

Cada agente é um arquivo de texto com instruções. O Claude Code lê o arquivo e passa a tarefa para o agente certo quando você pede.

## Os agentes

| Agente | Para que serve | O que entrega |
|---|---|---|
| `revisor-acessibilidade` | Revisar telas, fluxos, links do Figma, imagens ou código front-end com base na WCAG 2.2 nível AA | Tabela com problema, critério WCAG, gravidade e sugestão de correção |
| `critico-design` | Criticar uma tela ou fluxo com as 10 heurísticas de Nielsen, com foco em produtos B2B complexos | Lista de problemas com heurística, impacto e sugestão, mais as 3 melhorias de maior impacto e menor esforço |
| `pesquisa-ux` | Planejar pesquisa, montar roteiro de entrevista, sintetizar entrevistas e analisar dados quantitativos | Plano de pesquisa, roteiro, síntese por temas com citações reais ou leitura cautelosa dos números |

## Princípios

- **Sem invenção.** O revisor de acessibilidade só cita critérios que existem na WCAG 2.2. O pesquisador nunca cria dados nem citações.
- **Evidência separada de hipótese.** O que veio do material e o que é interpretação aparecem marcados.
- **Limites declarados.** Cada agente diz o que não conseguiu verificar com o material recebido.
- **Só leitura na revisão.** Os agentes de acessibilidade e de crítica não alteram arquivos.

## Como instalar

1. Baixe este repositório.
2. Copie os três arquivos da pasta `.claude/agents/` para um destes lugares:
   - **Um projeto só:** a pasta `.claude/agents/` dentro do projeto.
   - **Todos os seus projetos:** a pasta `.claude/agents/` do seu usuário. No Windows, `C:\Users\SEU_USUARIO\.claude\agents\`. No Mac e no Linux, `~/.claude/agents/`.
3. Feche e abra o Claude Code.

## Como usar

Descreva a tarefa e o Claude Code escolhe o agente. Para garantir, cite o nome do agente.

**Acessibilidade**

```
Use o agente revisor-acessibilidade para revisar a tela de login em src/pages/Login.tsx
```

**Crítica de design**

```
Use o agente critico-design para criticar a tela em telas/dashboard.png
```

**Pesquisa de UX**

```
Use o agente pesquisa-ux para sintetizar as entrevistas da pasta pesquisa/entrevistas
```

Também dá para chamar com `@`: digite `@agent-` e escolha o agente na lista.

Para revisar uma imagem, salve o arquivo em uma pasta e informe o caminho.

## Estrutura

```
.claude/
  agents/
    revisor-acessibilidade.md
    critico-design.md
    pesquisa-ux.md
README.md
```

## Como adaptar

Abra o arquivo do agente em qualquer editor de texto. O cabeçalho, entre as linhas `---`, define o nome, quando o agente é usado e quais ferramentas ele tem. O texto abaixo são as instruções. Mude o que quiser e salve.

Formato dos arquivos: [documentação de subagentes do Claude Code](https://code.claude.com/docs/en/sub-agents).
