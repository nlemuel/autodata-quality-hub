# AutoData Quality | Qualidade de Dados Automotivos

## O projeto

Imagine receber uma lista de peças de um fornecedor e precisar descobrir **a quais veículos cada peça está associada**. Antes de publicar o catálogo, é necessário responder: os cadastros estão completos, os códigos são únicos e os relacionamentos fazem sentido?

Foi para simular esse desafio que criei o **AutoData Quality**, um projeto pessoal de **Data Quality e gestão de dados mestres**, usando Excel.

## Como funciona

O fluxo parte de duas origens: **dados públicos de frota da SENATRAN** como referência de veículos e **dados simulados de fornecedor** para produtos e aplicações. Os dados originais são preservados para permitir auditoria.

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

## Ferramentas e aprendizado

- **Excel:** tabelas, fórmulas, conferências e rastreabilidade.
- **Dados abertos:** referência pública da frota de veículos da SENATRAN.
- **Data Quality / Master Data:** regras de qualidade, integridade entre cadastros e controle de atualizações.

O principal aprendizado foi que **qualidade de dados não é apenas encontrar erros**: é conseguir explicar cada regra, localizar a origem do problema e tornar a correção verificável.

## Escopo e próximos passos

Este é um **MVP de estudo**, não um catálogo automotivo comercial. As aplicações e compatibilidades são simuladas e **não devem ser usadas para determinar se uma peça serve em um veículo real**. Os anos observados na frota não representam necessariamente os anos de fabricação de um modelo.

Como evolução, o projeto prevê consolidar um painel de indicadores, concluir a documentação técnica e considerar o uso de Power Query para repetir as transformações com menos etapas manuais.

---

**English summary:** Personal Excel-based MVP for automotive master data and data quality. It combines public vehicle fleet reference data with simulated supplier records to test standardization, validation, relationship integrity and update tracking. In controlled synthetic tests, all 118 expected failures were detected across 493 checked records, with no false positives. These results do not measure real-world supplier data accuracy.
