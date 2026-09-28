# 🧌 Gigante - O ombro das pequenas empresas

Assistente virtual para pequenos empresários brasileiros.

## 💡 O Que é o Gigante?

O Gigante é um assistente virtual que providencia dados valiosos e insights para donos de pequenas empresas que se estabeleceram recentemente no mercado de trabalho, ajudando-os a tomarem melhores decisões que os ajudam a aumentar a sua produtividade.

**As funçoes do Gigante**
-Providenciar dados e insights que afetam na tomada de decisão
-Buscar e divulgar pesquisas de mercado recentes
-Analisar e verificar os ajustes que poderão ser realizados dentro das empresas
-Apoia as decisões tomadas, sempre informando os pros e os contras de cada oportunidade de negócio.

## 🏗️ Arquitetura

```mermaid
flowchart TD
    A[Empresário] --> B["Streamlit (Interface Visual)"]
    B --> C[LLM]
    C --> D[Base de Conhecimento]
    D --> C
    C --> E[Validação]
    E --> F[Dados e insights]
```

**Stack:**
- Interface: Streamlit
- LLM: Claude Opus
- Dados: Arquivos JSON

## 📁 Estrutura do Projeto

```
├── data/                          # Base de conhecimento
│   ├── empresa.json          # Ambiente e contexto do usuário final
│   ├── perfil_empresario.csv # Perfil do usuário final
│   └──  funcionarios.csv      # Funcionarios da empresa
│ 
│
├── docs/                          # Documentação completa
│   ├── 01-documentacao-agente.md  # Caso de uso e persona
│   ├── 02-base-conhecimento.md    # Dados e de como são processados
│   ├── 03-prompts.md              # System prompt e casos de teste
│   ├── 04-metricas.md             # Avaliação de qualidade
│   └── 05-pitch.md                # Apresentação do projeto
│
└── src/
    └── app.py                     # Aplicação Streamlit
```

## ▶️ Instalações e executar

### 1. Instalar Dependências

```bash
pip install streamlit pandas requets anthropic
```

### 2. Rodar o Gigante

```bash
streamlit run src/app.py
```

## 🎯 Casos de Uso

**Usuário:**
```
"Quais são as melhores épocas do ano para elevarmos o nosso marketing de velas artesanais?"
```
**Gigante:**
```
"De acordo com a sua área de negócio e com os dados estatísticos, é recomendado que haja uma maior divulgação de velas artesanais nos meses de Novembro e Dezembro, estima-se que cerca de 30% a 35% de todas as vendas anuais desse setor aconteçam especificamente nesse período de fim de ano, em celebração ao dia de Finados e a Véspera de Natal."
```

**Usuário:**
```
"Quais são os produtos e serviços mais vendidos no bairro de Tambaú?"
```
**Gigante:**
```
"Os principais serviços oferecidos no bairro Tambaú seriam os serviços de turismo e gastronomia, devido ao grande número de quiosques e viagens que são ofertados na praia de Tambaú. 
```

## 📊 Métricas de Avaliação

| Métrica | Objetivo |
|---------|----------|
| **Assertividade** | O agente responde o que foi perguntado? |
| **Segurança** | Evita inventar informações (anti-alucinação)? |
| **Coerência** | A resposta é adequada ao perfil do cliente? |
