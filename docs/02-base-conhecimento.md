# Base de Conhecimento

## Dados Utilizados

O FinMatcher utiliza os dados mockados fornecidos para garantir que as sugestões sejam fundamentadas em informações reais do cliente e no catálogo oficial do banco.

| Arquivo | Formato | Utilização no Agente |
|---------|---------|---------------------|
| `perfil_investidor.json` | JSON | **Fonte Primária**: Define o perfil de investidor (nível de risco e objetivos) do usuário. |
| `produtos_financeiros.json` | JSON | **Fonte Primária**: Catálogo oficial de produtos financeiros para cruzamento de dados. |
| `historico_atendimento.csv` | CSV | **Fonte Secundária**: Fornece contexto sobre interações passadas. |
| `transacoes.csv` | CSV | **Fonte Secundária**: Permite validar a disponibilidade de saldo para aportes. |

---

## Estratégia de Integração

### Como os dados são carregados?
Os arquivos são carregados em memória no início da execução da aplicação Streamlit utilizando as bibliotecas `json` e `pandas`. Os dados são convertidos para strings formatadas para que a LLM possa processá-los facilmente.

### Como os dados são usados no prompt?
Os dados são injetados diretamente no **Contexto do Agente**. Sempre que o usuário faz uma pergunta, o FinMatcher recupera as informações do perfil e o catálogo de produtos e os envia como parte da instrução do sistema (System Message), garantindo que a resposta seja baseada estritamente nesses dados (técnica de Grounding).

---

## Exemplo de Contexto Montado

> Mostre um exemplo de como os dados são formatados para o agente.

```
[CONTEXTO DE PERFIL]
- Nome: João Silva
- Perfil: Moderado
- Objetivos: Aposentadoria, Reserva de Emergência

[CATÁLOGO DE PRODUTOS DISPONÍVEIS]
- Produto A: CDB Pós-Fixado (Risco: Baixo)
- Produto B: Fundo de Ações (Risco: Alto)
- Produto C: Tesouro Direto (Risco: Baixo)

[PERGUNTA DO USUÁRIO]
"Quais produtos você me sugere para minha reserva de emergência?"
```
