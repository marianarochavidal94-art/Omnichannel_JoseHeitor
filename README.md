Sistema de Gestão OmniChannel — Desafio Final

SENAI

Identificação do Estudante
- Aluno: José Heitor Cordeiro de Lima Xavier
- Turma: Desenvolvimento de Sistemas
- Unidade Curricular: Banco de Dados
- Docente: Ryan

1. Descrição do Projeto
Este projeto apresenta a infraestrutura de dados do ecossistema de e-commerce da VarejoOmni S.A., integrando MySQL para transações relacionais e MongoDB Atlas para armazenamento de logs não relacionais de navegação dos clientes.

2. Objetivos
- Modelar e implementar o banco de dados relacional.
- Criar tabelas com chaves primárias e estrangeiras.
- Inserir dados de teste consistentes.
- Automatizar o processamento de vendas e a atualização do estoque.
- Registrar alterações de preços por meio de uma trigger de auditoria.
- Configurar permissões de acesso ao banco de dados.
- Implementar uma prova de conceito de logs de navegação no MongoDB Atlas.
- Gerar o backup do banco de dados e publicar os arquivos no GitHub.

3. Tecnologias e Ferramentas Utilizadas

- Modelagem: brModelo.
- SGBD Relacional: MySQL Server 8.0 e MySQL Workbench.
- SGBD NoSQL: MongoDB Atlas (Cloud).
- Editor/IDE: Visual Studio Code.
- Controle de Versão: Git e GitHub.

4. Estrutura do Repositório

omnichannel/
├── docs/
│   └── der_omnichannel.png
├── scripts/
│   ├── 01_ddl_estrutura_e_seguranca.sql
│   ├── 02_dml_povoamento.sql
│   ├── 03_automacao_plsql.sql
│   ├── 04_nosql_poc.js
│   └── backup_omnichannel.sql
└── README.md

5. Modelagem do Banco de Dados

O banco relacional contempla seis tabelas principais:
- clientes: armazena os dados cadastrais dos clientes.
- lojas: registra as unidades físicas e o canal de e-commerce.
- produtos:armazena o catálogo, os preços e o estoque.
- pedidos: registra as vendas realizadas.
- itens_pedido: registra os produtos, as quantidades e os preços praticados em cada pedido.
- auditoria_preco: mantém o histórico das alterações de preços.
Os relacionamentos são definidos por chaves primárias e estrangeiras para garantir a integridade referencial.

6. Como Executar os Scripts

6.1. Banco Relacional — MySQL
1. Abra o MySQL Workbench e conecte-se ao servidor MySQL.
2. Execute os scripts na seguinte ordem:
- `01_ddl_estrutura_e_seguranca.sql`
- `02_dml_povoamento.sql`
- `03_automacao_plsql.sql`
3. Verifique se as tabelas foram criadas e se os dados foram inseridos corretamente.
4. Execute a Stored Procedure `sp_registrar_venda` para testar o processamento de uma venda e a baixa de estoque.
5. Execute um comando `UPDATE` no preço de um produto para validar a trigger `trg_auditoria_preco`.
6. Confira se a alteração foi registrada na tabela `auditoria_preco`.

6.2. Banco Não Relacional — MongoDB Atlas
1. Configure um cluster no MongoDB Atlas.
2. Configure o usuário do banco e as permissões de acesso à rede.
3. Conecte-se ao cluster utilizando a extensão MongoDB do Visual Studio Code.
4. Abra o arquivo `04_nosql_poc.js` no MongoDB Playground.
5. Execute os comandos de inserção e consulta.
6. Verifique os documentos na coleção `logs_navegacao`, dentro do banco `omnichannel_nosql`.

7. Segurança e Controle de Acesso

O usuário `atendente_omni` deve possuir permissão exclusiva de consulta (`SELECT`) nas tabelas `clientes` e `produtos`, sem privilégios de alteração dos dados ou da estrutura do banco.
As credenciais de acesso ao MongoDB Atlas não devem ser publicadas no repositório.

8. Evidências de Funcionamento

As capturas de tela que comprovam o funcionamento do projeto estão disponíveis na pasta `docs`, neste repositório.
Nessa pasta estão organizados os prints dos testes realizados, demonstrando a execução dos scripts SQL, o funcionamento da procedure de registro de vendas, a trigger de auditoria de preços, as permissões de acesso e os registros no MongoDB Atlas.

9. Backup do Banco de Dados

O arquivo `backup_omnichannel.sql`, localizado na pasta `scripts`, deverá conter a exportação do banco relacional gerada pelo recurso **Data Export** do MySQL Workbench.
O backup deverá corresponder à versão final do banco implementado.

