# Seção 07: Evolução de Schema, Compactação de Dados e Uso de Metadados 🧊

Nesta seção, o foco está em práticas essenciais de manutenção e governança em tabelas Apache Iceberg com Spark.
Você vai aprender a evoluir o schema com segurança, otimizar arquivos com compactação e explorar metadados para auditoria e observabilidade. 🚀

## Objetivos da seção 🎯
- Entender como evoluir o schema de tabelas Iceberg sem perder compatibilidade.
- Aplicar estratégias de compactação para melhorar a performance de leitura.
- Consultar metadados para auditoria, rastreabilidade e troubleshooting.
- Consolidar boas práticas de operação de tabelas analíticas no dia a dia.

## Arquivos da seção 📁
- `01_Evolucao_Schema.ipynb`
- `02_Compactacao_Dados.ipynb`
- `03_Uso_Metadados_Catalgo.ipynb`

## Notebook 01 - Evolução de schema
No notebook `01_Evolucao_Schema.ipynb`, o foco é a evolução da estrutura da tabela sem perder os dados já existentes.

### Aprendizados principais
- Como adicionar novas colunas ao schema.
- Como manter compatibilidade com dados históricos.
- Como validar a estrutura depois das alterações.

## Notebook 02 - Compactação de dados
No notebook `02_Compactacao_Dados.ipynb`, o foco é reduzir fragmentação e melhorar a organização física dos arquivos.

### Aprendizados principais
- Quando a compactação é útil.
- Como reorganizar arquivos pequenos em estruturas mais eficientes.
- Como avaliar o impacto da manutenção da tabela.

## Notebook 03 - Uso de metadados do catálogo
No notebook `03_Uso_Metadados_Catalgo.ipynb`, o foco é explorar informações do catálogo e dos metadados do Iceberg.

### Aprendizados principais
- Como consultar informações de tabelas e metadados.
- Como entender melhor o estado da tabela no catálogo.
- Como apoiar auditoria e governança com metadados.

## Boas práticas para estudo 🛠️
- Execute os notebooks na ordem (`01` -> `03`).
- Sempre valide os dados após cada etapa (`SELECT`, `COUNT`, snapshots).
- Documente alterações de schema para facilitar a manutenção.

## Resultado esperado da seção ✅
Ao final, você terá uma visão prática de como evoluir, otimizar e auditar tabelas Iceberg em cenários reais de engenharia de dados.

