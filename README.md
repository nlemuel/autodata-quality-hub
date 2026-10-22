# AutoData Quality | Qualidade de Dados Automotivos

## O projeto

Imagine receber uma lista de peças de um fornecedor e precisar descobrir **a quais veículos cada peça está associada**. Antes de publicar o catálogo, é necessário responder: os cadastros estão completos, os códigos são únicos e os relacionamentos fazem sentido?

Foi para simular esse desafio que criei o **AutoData Quality**, um projeto pessoal de **Data Quality e gestão de dados mestres**, usando Excel.

## Como funciona

O fluxo parte de duas origens: **dados públicos de frota da SENATRAN da cidade de São José dos Campos** como referência de veículos e **dados simulados de fornecedor** para produtos e aplicações. Os dados originais são preservados para permitir auditoria.

Em seguida, o processo:

1. **Organiza** cadastros de veículos, produtos e aplicações (relações produto × veículo).
2. **Padroniza e valida** campos com regras de completude, unicidade, validade, consistência, integridade e atualidade.
3. **Registra inconsistências** em um log para revisão e correção.
4. **Compara remessas** do fornecedor para identificar novos registros, alterações, duplicidades e conflitos.
5. **Classifica aplicações** para apoiar a decisão de aprovar, corrigir, deixar pendente ou rejeitar registros.

**Fluxo resumido:** dados brutos → padronização → validação → registro de problemas → revisão do catálogo.

## Resultados dos testes

O processo foi conferido com um conjunto de testes de erros **inseridos intencionalmente em dados simulados**:

| Indicador | Resultado |
| --- | ---: |
| Registros comparados | 493 |
| Registros com status correto | 493/493 |
| Falhas esperadas identificadas | 118/118 (100%) |
| Falsos positivos | 0 |
| Correções do fornecedor sem falha indevida | 12/12 |

**Importante:** esses números validam as regras para os cenários simulados. Não representam uma taxa de detecção de 100% em dados reais de fornecedores.

## Ferramentas

- **Excel:** tabelas, fórmulas, conferências e rastreabilidade.
- **Dados abertos:** referência pública da frota de veículos da SENATRAN.
- **Data Quality / Master Data:** regras de qualidade, integridade entre cadastros e controle de atualizações.
- **Power Query:** consultas para agregar e padronizar a base de veículos, montar o cadastro de produtos e gerar o log de qualidade.
**Qualidade de dados não é apenas encontrar erros**: é conseguir explicar cada regra, localizar a origem do problema e tornar a correção verificável.

## Dados reais: o que apareceu
**Fonte:** Registro Nacional de Veículos Automotores (SENATRAN/Ministério dos Transportes), dados abertos, referência jul/2026; licença exibida no portal: Other (Public Domain). Recorte: São José dos Campos/SP, 30.671 linhas (523.100 veículos), das quais os 250 modelos mais frequentes formam o cadastro de veículos (47% da frota do recorte). O arquivo original, de 22,7 milhões de linhas, não está no repositório.
Problemas encontrados na fonte: campo de ano com o texto "Sem Informação" (543 linhas); registros sem modelo, só com a marca (199 linhas); prefixos de origem antes da marca (I, IMP, JTA, REB, SR); a mesma marca escrita de três formas (GM, CHEV, CHEVROLET); quantidades gravadas com ponto decimal, que o Excel em português lê como 10 vezes o valor.

## Escopo e próximos passos

Este é um **MVP de estudo**, não um catálogo automotivo comercial. As aplicações e compatibilidades são simuladas e **não devem ser usadas para determinar se uma peça serve em um veículo real**. A faixa de anos de cada modelo foi derivada dos anos de fabricação observados na frota do recorte. Não é o período oficial de produção do modelo. Os nomes das marcas de peças são fictícios e não têm relação com empresas ou produtos reais.

Como evolução, o projeto prevê consolidar um painel de indicadores e concluir a documentação técnica.

## Fonte de Dados

Os dados utilizados neste projeto são provenientes do portal oficial de dados abertos do Ministério dos Transportes.

    RENAVAM — Registro Nacional de Veículos Automotores: 
    
[Acessar dataset do RENAVAM](https://dados.transportes.gov.br/dataset/registro-nacional-de-veiculos-automotores-renavam)

Acesse o link para consultar e obter os dados originais utilizados nas análises de qualidade de dados.
dados. 

Data do download: 03/10/2026

---

**English summary:** Personal Excel-based MVP for automotive master data and data quality. It combines public vehicle fleet reference data with simulated supplier records to test standardization, validation, relationship integrity and update tracking. In controlled synthetic tests, all 118 expected failures were detected across 493 checked records, with no false positives. These results do not measure real-world supplier data accuracy.
