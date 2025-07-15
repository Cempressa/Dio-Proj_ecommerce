# Projeto de Modelagem de Banco de Dados: Cenário de E-commerce

## Visão Geral do Projeto

Este projeto demonstra a modelagem e implementação de um banco de dados relacional para um cenário de e-commerce, focado em vendas, clientes, produtos, fornecedores e processos de entrega e pagamento. O objetivo foi criar um esquema de banco de dados robusto e funcional, aplicando conceitos de modelagem lógica e relacional, incluindo refinamentos específicos para atender a requisitos de negócio.

## Modelo Lógico Original (Ponto de Partida)

O projeto partiu de um modelo lógico inicial (conforme `E-commerce_v1.png`), que foi então refinado para incorporar funcionalidades adicionais.

![Modelo Lógico Original - E-commerce](E-commerce_v1.png)

## Refinamentos Implementados

O modelo lógico original foi refinado para abordar os seguintes requisitos específicos:

1.  **Cliente PJ e PF:** A tabela `cliente` foi projetada para lidar com clientes Pessoa Física (PF) e Pessoa Jurídica (PJ) na mesma entidade, utilizando um campo `TipoCliente` (`ENUM('PF', 'PJ')`). Regras de integridade garantem que apenas os campos de identificação (CPF ou CNPJ) relevantes para o tipo de cliente sejam preenchidos.
2.  **Múltiplas Formas de Pagamento por Pedido:** A relação entre `pedido` e `pagamento` foi ajustada para um relacionamento de **Um para Muitos (1:N)**. Isso permite que um único pedido seja associado a múltiplos registros de pagamento, viabilizando cenários onde um pedido é pago por diferentes métodos ou em parcelas.
3.  **Informações de Entrega:** A tabela `pedido` foi estendida para incluir um campo `CodigoRastreio`, além de já estar relacionada com `transportadora` e `status_entrega`, fornecendo uma visão completa sobre o processo de entrega de cada pedido.

## Estrutura do Banco de Dados (Esquema)

O esquema do banco de dados foi implementado usando o MySQL, contendo tabelas para clientes, produtos, pedidos, pagamentos, fornecedores, vendedores terceiros, estoque, transportadoras e status de entrega. As chaves primárias e estrangeiras foram definidas para garantir a integridade referencial dos dados.

O script SQL para a criação do esquema está disponível em: [`ecommerce_schema.sql`](ecommerce_schema.sql)

## Persistência de Dados (Dados de Teste)

Para facilitar os testes e a demonstração das consultas, um conjunto de dados de exemplo foi inserido no banco de dados.

O script SQL com os dados de teste está disponível em: [`ecommerce_test_data.sql`](ecommerce_test_data.sql)

## Consultas SQL (DML)

Foram elaboradas diversas consultas SQL (Data Manipulation Language) para extrair insights complexos dos dados, demonstrando o uso de:
* `SELECT` (Recuperações simples)
* `WHERE` (Filtros de dados)
* Expressões para gerar atributos derivados
* `ORDER BY` (Ordenação de resultados)
* `HAVING` (Filtros em grupos)
* `JOIN` (Junções entre múltiplas tabelas)

As perguntas que essas consultas respondem incluem:
* Quantos pedidos foram feitos por cada cliente, e qual o valor total gasto por cada um?
* Algum vendedor terceiro também é um fornecedor (com base no CNPJ)?
* Qual a relação de produtos, seus fornecedores e a quantidade em estoque?
* Relação de nomes dos fornecedores e nomes dos produtos que eles fornecem.
* Quais clientes (PF e PJ) fizeram pedidos com valor total superior à média de pedidos de seus respectivos tipos de cliente?
* Mostrar todos os detalhes de pedidos que foram entregues, incluindo informações da transportadora e o código de rastreio.
* Listar todos os pedidos e os métodos de pagamento utilizados, incluindo casos em que um pedido teve múltiplos pagamentos, e o total pago por cada método para cada pedido.

Todas as consultas SQL estão disponíveis em: [`ecommerce_queries.sql`](ecommerce_queries.sql)

## Ferramentas Utilizadas (Opcional)

* **MySQL Workbench:** Para gerenciamento do banco de dados, execução de scripts SQL e visualização do modelo.
* **Visual Studio Code (VS Code):** Para edição e organização dos scripts SQL.

---
**Desenvolvido como parte do Desafio de Projeto de Modelagem de Banco de Dados.**