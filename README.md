# Case Técnico — Yandeh Business Solutions

## 1. Contexto

Este projeto foi desenvolvido a partir de um case técnico de ciência de dados com foco em análise logística e comercial.

O cenário apresentado indica que a Yandeh possui crescimento de receita, mas esse crescimento não está se refletindo proporcionalmente no lucro líquido. A hipótese central é que existem gargalos operacionais na logística e dúvidas sobre a eficiência da força de vendas.

## 2. Objetivo

O objetivo do projeto é analisar dados de entregas e vendas para identificar:

- quais frotas apresentam maior margem;
- quais frotas têm maior probabilidade de atraso;
- quais canais comerciais apresentam melhor conversão;
- qual canal gera maior faturamento estimado;
- onde a empresa deveria concentrar esforços e recursos no próximo semestre.

## 3. Bases utilizadas

O projeto utiliza duas bases em formato CSV:

- `entregas_logistica.csv`: base com 12.000 entregas, contendo informações sobre tipo de veículo, carga, distância, tempo estimado, tempo real, valor de frete e custo de combustível.
- `vendas_vendedores.csv`: base com 50 vendedores, contendo informações sobre canal comercial, leads contatados, vendas convertidas, ticket médio e anos de experiência.

## 4. Estrutura do projeto

```text
case-yandeh-business-solutions/
├── data/
│   ├── raw/
│   └── processed/
├── notebooks/
│   ├── 01_preparacao_dados.ipynb
│   ├── 02_analise_logistica.ipynb
│   ├── 03_analise_comercial.ipynb
│   └── 04_conclusao_recomendacoes.ipynb
├── outputs/
│   ├── figures/
│   └── tables/
├── presentation/
├── src/
├── requirements.txt
├── .gitignore
└── README.md
```

## 5. Metodologia

A análise foi desenvolvida em etapas:

1. carregamento dos dados;
2. análise de qualidade dos dados;
3. tratamento de inconsistências;
4. criação de métricas de negócio;
5. análise logística;
6. análise comercial;
7. consolidação dos achados e recomendações.

## 6. Métricas criadas

### Métricas logísticas

- `margem_bruta`: diferença entre valor do frete e custo de combustível.
- `margem_percentual`: margem bruta em relação ao valor do frete.
- `atraso_min`: diferença entre tempo real e tempo estimado.
- `atrasou`: indica se a entrega atrasou.
- `ocupacao_veiculo`: proporção da capacidade do veículo utilizada.
- `custo_por_km`: custo de combustível por quilômetro.
- `frete_por_km`: valor de frete por quilômetro.

### Métricas comerciais

- `taxa_conversao`: proporção de vendas convertidas em relação aos leads contatados.
- `faturamento_estimado`: vendas convertidas multiplicadas pelo ticket médio.
- `faturamento_por_lead`: faturamento estimado dividido pelo total de leads contatados.

## 7. Principais achados

### Logística

- `Carreta_Bau` e `Carreta_Sider` concentram aproximadamente 72% da margem bruta total da operação.
- Essas mesmas frotas apresentam as maiores probabilidades de atraso, acima de 64%.
- O VUC possui o maior volume de entregas, mas baixa participação na margem total.
- A ocupação média dos veículos ficou próxima entre as frotas, em torno de 57% a 59%.
- As carretas operam rotas mais longas e concentram maior risco operacional.

### Comercial

- `Field Sales` apresentou maior taxa de conversão ponderada: 16,10% contra 9,42% de `Inside Sales`.
- `Field Sales` também apresentou maior faturamento estimado total.
- O faturamento estimado por lead foi maior em `Field Sales`.
- A experiência dos vendedores não apresentou relação positiva clara com desempenho comercial.

## 8. Recomendação estratégica

Com base nos dados analisados, a Yandeh deveria priorizar a melhoria operacional das frotas `Carreta_Bau` e `Carreta_Sider`, pois elas concentram a maior parte da margem bruta total e também apresentam as maiores probabilidades e intensidades de atraso.

Na frente comercial, `Field Sales` apresentou melhor desempenho em conversão, faturamento estimado e faturamento por lead. Porém, para uma decisão completa de expansão do canal, seria necessário considerar também os custos operacionais de visitas e atendimento.

## 9. Limitações

A margem calculada considera apenas o custo de combustível. Portanto, ela deve ser interpretada como uma margem bruta simplificada, já que outros custos logísticos, como motorista, manutenção, pedágio, depreciação e seguro, não estão presentes na base.

Além disso, a análise comercial não possui dados de custo por canal, o que impede o cálculo completo de ROI.

## 10. Como executar o projeto

Crie um ambiente virtual:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

Instale as dependências:

```bash
pip install -r requirements.txt
```

Abra os notebooks na ordem:

```text
01_preparacao_dados.ipynb
02_analise_logistica.ipynb
03_analise_comercial.ipynb
04_conclusao_recomendacoes.ipynb
```
