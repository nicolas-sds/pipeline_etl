
## Visão Geral

Esta transformação do Pentaho Data Integration (PDI) é responsável por ler um arquivo CSV, processar os dados e carregar em um modelo dimensional.
O fluxo é dividido em duas frentes principais: carga de tabelas de dimensão e carga de tabelas de fato.

**Fonte de Dados:**
* **Tipo:** `CSV file input`
* **Arquivo:** `dataset_teste_de.csv`
* **Descrição:** Arquivo de entrada principal contendo todos os dados brutos.

#### Fluxo 1: Dimensão Calendário (`dim_calendario`)

#### Fluxo 2: Dimensão Ponto de Venda (`dim_pdv`)

#### Fluxo 3: Dimensão Linha de Produto (`dim_linha_produto`)

#### Fluxo 4: Fato Disponibilidade (`ft_disponibilidade`)

#### Fluxo 5: Fato Disponibilidade Agregada (`ft_disponibilidade_agregada`)

#### Fluxo 6: Fato Ponto Extra (`ft_ponto_extra`)

#### Fluxo 7: Fato Ponto Extra Agregada (`ft_ponto_extra_agregada`)

```mermaid
graph LR
A[dataset_teste_de.csv]

A --> B(Sort rows data)
B --> C(Unique rows data)
C --> D(Calculator data)
D --> E(dim_calendario output)

A --> F(Sort rows id_pdv)
F --> G(Unique rows id_pdv)
G --> H(dim_pdv output)

A --> F2(Sort rows id_linha_produto)
F2 --> G2(Unique rows id_linha_produto)
G2 --> H2(dim_linha_produto output)

A --> L(Filter rows data set-2020)
L --> M(Filter disponibilidade)
M --> N(Group by disponibilidade)
N --> O(ft_disponibilidade output)

M --> P(Group by disponibilidade_agregada)
P --> Q(ft_disponibilidade_agregada output)

L --> R(Filter ponto extra)
R --> S(Group by ponto_extra)
S --> T(ft_ponto_extra output)

R --> U(Group by ponto_extra_agregada)
U --> V(ft_ponto_extra_agregada output)
```
