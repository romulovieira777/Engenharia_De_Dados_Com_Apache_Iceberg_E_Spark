# Seção 06: Incorporando Dados Existentes de Outras Fontes

Nesta seção, o foco é trazer dados que já existem fora do Iceberg para dentro de uma tabela gerenciada com Spark + Apache Iceberg.

## Objetivos da seção
- Incorporar dados existentes em formato Parquet para uma tabela Iceberg.
- Entender como validar dados carregados e o histórico de snapshots.
- Realizar integração incremental com banco relacional (PostgreSQL) usando `MERGE`.
- Simular um fluxo mais próximo de produção com controle de `last_run_timestamp`.

## Arquivos da seção
- `01_Incorporando_Dados_Existentes.ipynb`
- `02_Fazendo_Merge_Banco_Relacional.ipynb`

## Notebook 01 - Incorporando dados existentes
No notebook `01_Incorporando_Dados_Existentes.ipynb`, o fluxo principal é:

1. Preparar ambiente (Java/Spark) e estrutura de diretórios.
2. Descompactar dados de exemplo (`vendas_iceberg.zip`) para o warehouse local.
3. Criar (ou recriar) a tabela Iceberg no catálogo Hadoop.
4. Ler dados Parquet e validar conteúdo com consultas SQL.
5. Consultar metadados de snapshots para verificar o versionamento da tabela.

### Aprendizados principais
- Como aproveitar arquivos Parquet existentes sem recriar pipeline do zero.
- Como inspecionar dados no Iceberg via Spark SQL.
- Como usar a tabela de metadados `snapshots` para auditoria e rastreabilidade.

## Notebook 02 - Fazendo merge com banco relacional
No notebook `02_Fazendo_Merge_Banco_Relacional.ipynb`, o fluxo principal é:

1. Preparar ambiente e importar bibliotecas auxiliares de data/hora.
2. Criar base inicial da tabela `vendas_iceberg` no Iceberg.
3. Configurar conexão JDBC para PostgreSQL.
4. Ler dados do banco de forma incremental com base em `last_run_timestamp`.
5. Criar visão temporária (`vendas_updates`) e aplicar `MERGE` na tabela Iceberg.
6. Validar total de registros e atualizar timestamp da última execução.

### Aprendizados principais
- Estratégia de carga incremental a partir de banco relacional.
- Uso do comando `MERGE` para `upsert` (`insert`/`update`) em tabelas Iceberg.
- Importância de persistir o timestamp de controle entre execuções.

## Boas práticas para estudo
- Execute os notebooks na ordem (`01` -> `02`).
- Sempre valide os dados após cada etapa (`SELECT`, `COUNT`, snapshots).
- Em cenários reais, mova credenciais para variáveis de ambiente/secret manager.
- Persista o `last_run_timestamp` em armazenamento externo (arquivo, tabela de controle ou banco).

## Resultado esperado da seção
Ao final, você terá uma visão prática de como:
- Incorporar dados históricos já existentes.
- Integrar atualizações incrementais vindas de sistemas relacionais.
- Manter governança e rastreabilidade com recursos nativos do Apache Iceberg.
