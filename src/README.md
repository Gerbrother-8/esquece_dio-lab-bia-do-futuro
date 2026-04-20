# Código da Aplicação

Esta pasta contém o código do **GIGA (Gestor Inteligente de Gastos e Ativos)**.

## Estrutura

```
Chatbot GIGA/
├── data/                           # Base de dados local (contexto do agente)
│   ├── perfil_investidor.json      # Perfil do cliente.
│   ├── produtos_financeiros.json   # Catálogo de produtos.
│   ├── transacoes.csv              # Transações financeiras.
│   └── historico_atendimento.csv   # Dúvidas anteriores.
├── src/                            # Scripts de execução
    ├── app.py                      # Aplicação principal (Streamlit)
    └── requirements.txt            # Bibliotecas necessárias
    └── README.md                   # Estrutura do código e como rodar
```

## Como Rodar

```bash
# Instalar dependências
pip install -r requirements.txt

# Rodar a aplicação
streamlit run app.py
```
