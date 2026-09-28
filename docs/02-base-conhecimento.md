# Base de Conhecimento

## Dados Utilizados

Descreva se usou os arquivos da pasta `data`, por exemplo:

| Arquivo | Formato | Utilização no Agente |
|---------|---------|---------------------|
| `empresa.json` | json | Providenciar insights e dados baseado na empresa |
| `perfil_empresario.json` | JSON | Personalizar recomendações |
| `funcionarios.csv` | CSV | contextualizar o tamanho e o desempenho da empresa |

---

## Adaptações nos Dados

> Você modificou ou expandiu os dados mockados? Descreva aqui.

Sim, foi transformei os dados para que pudessem ser aplicados a realidade do nosso público alvo.

---

## Estratégia de Integração

### Como os dados são carregados?
> Descreva como seu agente acessa a base de conhecimento.

Pode-se injetar os dados diretamente, ou carregar os arquivos via código:

```python
import pandas as pd
import json

empresa = json.load(open('./data/empresa.json'))
empresario = pd.read_csv('./data/perfil-empresario.csv')
funcionarios = pd.read_csv('./data/funcionarios.csv')
```

### Como os dados são usados no prompt?
> Os dados vão no system prompt? São consultados dinamicamente?

Os dados são "injetados" em na realização de prompts a fim de que o modelo possa ter o contexto de todo o problema
```text
DADOS DA EMPRESA (data/empresa.json)
[
  {
    "nome_empresa": "Inauro Velas",
    "idade_empresa": 1.2,
    "endereco":  "Av. Prof Maria Sales, 71"
    "bairro": "manaira"
    "categoria": "mei",
    "patrimonio_empresarial": 30000.00
    "numero_funcionarios": 3,
    "metas": [
    {
      "meta": "Sair do MEI para Empresa Médio Porte",
      "valor_necessario": 340000000.00,
      "prazo": "2028-06"
        }
    ]
  }
]

DADOS DO EMPRESARIO (data/perfil_empresario.json)
{
  "nome": "Inácio Silva",
  "idade": 42,
  "profissao": "Empresario",
  "renda_empresarial_mensal": 4000.00,
  "perfil_investidor": "moderado",
  "objetivo_principal": "Construir reserva de emergência",
  "patrimonio_total": 15000.00,
  "reserva_emergencia_atual": 4000.00,
  "aceita_risco": true,
}

DADOS FUNCIONARIOS (data/funcionarios.csv)
nome,função,idade,salario_mensal,cargo
Arthur do Egito Dutra,42,3.000,repositor
Alex Garcia,27,2.600,caixa
Beatriz Melo de Souza,51,4.000,supervisora
```
---

## Exemplo de Contexto Montado

> Mostre um exemplo de como os dados são formatados para o agente.

```
Dados da Empresa:
- Nome: Inauro Velas
- Endereço: Av. Prof Maria Sales, 71
- Bairro: Manaira
- Categoria: MEI
- patrimonio_empresarial: R$ 30.000

Informações de funcionários:
- Dados Funcionário 1: Nome = Arthur do Egito Dutra, Idade = 24, Salário = 3.000, Cargo = Repositor
- Dados Funcionário 2: Nome = Alex Garcia, Idade = 27, Salário = 2.600, Cargo = Atendente de Caixa
- Dados Funcionário 3: Nome = Beatriz Melo de Sousa, Idade = 51, Salário = 4.000, Cargo = Supervisora
...
```
