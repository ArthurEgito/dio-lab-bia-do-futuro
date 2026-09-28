# Base de Conhecimento

## Dados Utilizados

Descreva se usou os arquivos da pasta `data`, por exemplo:

| Arquivo | Formato | Utilização no Agente |
|---------|---------|---------------------|
| `empresa.json` | json | Providenciar insights e dados baseado na empresa |
| `perfil_empresario.json` | JSON | Personalizar recomendações |
| `funcionarios.json` | JSON | contextualizar o tamanho e o desempenho da empresa |

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
empresario = pd.read_csv('./data/perfil-empresario.json')
funcionarios = pd.read_csv('./data/funcionarios.json')
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
    "endereco":  "Av. Prof Maria Sales, 71",
    "bairro": "manaira",
    "categoria": "MEI",
    "patrimonio_empresarial": 30000.00,
    "numero_funcionarios": 3,
    "metas": [
    {
      "meta": "Sair do MEI para Empresa Médio Porte",
      "valor_necessario": 340000000.00,
      "prazo": "2028-06"
        }
    ]
  }

DADOS DO EMPRESARIO (data/perfil_empresario.json)
{
  "nome": "Inácio Silva",
  "idade": 42,
  "renda_mensal": 4000.00,
  "perfil_investidor": "moderado",
  "patrimonio_total": 15000.00,
  "reserva_emergencia_atual": 4000.00,
  "aceita_risco": true,
}

DADOS FUNCIONARIOS (data/funcionarios.json)
[
    {
  "nome": "Arthur do Egito Dutra",
  "idade": 42,
  "renda_mensal": 3000.00,
  "cargo": "Repositor"
    },
    {
  "nome": "Alex Garcia",
  "idade": 26,
  "renda_mensal": 2600.00,
  "cargo": "Atendente de Caixa"
    },
    {
  "nome": "Beatriz Melo",
  "idade": 51,
  "renda_mensal": 3500.00,
  "cargo": "Supervisora"
    }
]
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

```
