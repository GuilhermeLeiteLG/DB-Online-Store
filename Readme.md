## Loja Online MySQL Database

Este repositório contém um conjunto de comandos SQL para criar e popular um banco de dados MySQL para uma loja online, incluindo tabelas para clientes, produtos, pedidos, itens de pedido, pagamentos e funcionários. Este é um projeto de estudo, criado com o objetivo de praticar e aprimorar habilidades em bancos de dados MySQL.

## Funcionalidades

- **Clientes:** Registra informações sobre os clientes, incluindo nome, e-mail e telefone.
- **Produtos:** Armazena dados dos produtos disponíveis, como nome, preço e quantidade em estoque.
- **Pedidos:** Gerencia pedidos realizados pelos clientes, com informações sobre o cliente, data do pedido, status do pedido, desconto aplicado e total do pedido.
- **Itens do Pedido:** Mantém os detalhes dos produtos incluídos em cada pedido, como quantidade e preço unitário.
- **Pagamentos:** Registra os pagamentos realizados pelos clientes em relação aos pedidos.
- **Funcionários:** Armazena informações sobre os funcionários da loja, incluindo nome, cargo e salário.

## Como Usar

1. Copie e cole os comandos SQL em um cliente MySQL para criar o banco de dados e suas tabelas.
2. Execute as inserções de dados de exemplo para preencher as tabelas com informações fictícias.
3. Utilize a consulta SQL fornecida para obter informações detalhadas de um pedido específico.

## Exemplo de Consulta Detalhada

A seguinte consulta SQL pode ser usada para obter informações detalhadas de um pedido específico:

```sql
SELECT 
    pedidos.id AS id_pedido, 
    clientes.nome AS nome_cliente, 
    produtos.nome AS nome_produto, 
    itens_pedido.quantidade, 
    itens_pedido.preco_unitario,
    pedidos.desconto,
    pedidos.total,
    pagamentos.valor AS valor_pago
FROM pedidos
JOIN clientes ON pedidos.cliente_id = clientes.id
JOIN itens_pedido ON pedidos.id = itens_pedido.pedido_id
JOIN produtos ON itens_pedido.produto_id = produtos.id
LEFT JOIN pagamentos ON pedidos.id = pagamentos.pedido_i
WHERE pedidos.id = 1;

