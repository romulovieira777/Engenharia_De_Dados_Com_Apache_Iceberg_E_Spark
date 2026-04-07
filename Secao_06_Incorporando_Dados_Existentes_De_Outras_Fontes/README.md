# Secao 06: Incorporando Dados Existentes de Outras Fontes

Nesta secao, o foco e trazer dados que ja existem fora do Iceberg para dentro de uma tabela gerenciada com Spark + Apache Iceberg.

## Objetivos da secao
- Incorporar dados existentes em formato Parquet para uma tabela Iceberg.
- Entender como validar dados carregados e historico de snapshots.
- Realizar integracao incremental com banco relacional (PostgreSQL) usando `MERGE`.
- Simular um fluxo mais proximo de producao com controle de `last_run_timestamp`.

## Arquivos da secao
- `01_Incorporando_Dados_Existentes.ipynb`
- `02_Fazendo_Merge_Banco_Relacional.ipynb`

## Notebook 01 - Incorporando dados existentes
No notebook `01_Incorporando_Dados_Existentes.ipynb`, o fluxo principal e:

1. Preparar ambiente (Java/Spark) e estrutura de diretories.
2. Descompactar dados de exemplo (`vendas_iceberg.zip`) para o warehouse local.
3. Criar (ou recriar) a tabela Iceberg no catalogo Hadoop.
4. Ler dados Parquet e validar conteudo com consultas SQL.
5. Consultar metadados de snapshots para verificar versionamento da tabela.

### Aprendizados principais
- Como aproveitar arquivos Parquet existentes sem recriar pipeline do zero.
- Como inspecionar dados no Iceberg via Spark SQL.
- Como usar a tabela de metadados `snapshots` para auditoria e rastreabilidade.

## Notebook 02 - Fazendo merge com banco relacional
No notebook `02_Fazendo_Merge_Banco_Relacional.ipynb`, o fluxo principal e:

1. Preparar ambiente e importar bibliotecas auxiliares de data/hora.
2. Criar base inicial da tabela `vendas_iceberg` no Iceberg.
3. Configurar conexao JDBC para PostgreSQL.
4. Ler dados do banco de forma incremental com base em `last_run_timestamp`.
5. Criar visao temporaria (`vendas_updates`) e aplicar `MERGE` na tabela Iceberg.
6. Validar total de registros e atualizar timestamp da ultima execucao.

### Aprendizados principais
- Estrategia de carga incremental a partir de banco relacional.
- Uso do comando `MERGE` para `upsert` (insert/update) em tabelas Iceberg.
- Importancia de persistir o timestamp de controle entre execucoes.

## Boas praticas para estudo
- Execute os notebooks na ordem (`01` -> `02`).
- Sempre valide os dados apos cada etapa (`SELECT`, `COUNT`, snapshots).
- Em cenarios reais, mova credenciais para variaveis de ambiente/secret manager.
- Persista o `last_run_timestamp` em armazenamento externo (arquivo, tabela de controle ou banco).

## Resultado esperado da secao
Ao final, voce tera uma visao pratica de como:
- Incorporar dados historicos ja existentes.
- Integrar atualizacoes incrementais vindas de sistemas relacionais.
- Manter governanca e rastreabilidade com recursos nativos do Apache Iceberg.

