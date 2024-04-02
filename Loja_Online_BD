-- Criar o banco de dados
CREATE DATABASE IF NOT EXISTS loja_online;

-- Usar o banco de dados
USE loja_online;

-- Tabela de clientes
CREATE TABLE IF NOT EXISTS clientes (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100),
    email VARCHAR(100),
    telefone VARCHAR(20)
);

-- Tabela de produtos
CREATE TABLE IF NOT EXISTS produtos (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100),
    preco DECIMAL(10, 2),
    estoque INT
);

-- Tabela de pedidos
CREATE TABLE IF NOT EXISTS pedidos (
    id INT AUTO_INCREMENT PRIMARY KEY,
    cliente_id INT,
    data_pedido TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    status ENUM('pendente', 'processando', 'enviado', 'entregue'),
    desconto DECIMAL(10, 2),
    total DECIMAL(10, 2),
    FOREIGN KEY (cliente_id) REFERENCES clientes(id)
);

-- Tabela de itens do pedido
CREATE TABLE IF NOT EXISTS itens_pedido (
    id INT AUTO_INCREMENT PRIMARY KEY,
    pedido_id INT,
    produto_id INT,
    quantidade INT,
    preco_unitario DECIMAL(10, 2),
    FOREIGN KEY (pedido_id) REFERENCES pedidos(id),
    FOREIGN KEY (produto_id) REFERENCES produtos(id)
);

-- Tabela de pagamentos
CREATE TABLE IF NOT EXISTS pagamentos (
    id INT AUTO_INCREMENT PRIMARY KEY,
    pedido_id INT,
    valor DECIMAL(10, 2),
    data_pagamento TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (pedido_id) REFERENCES pedidos(id)
);

-- Tabela de funcionários
CREATE TABLE IF NOT EXISTS funcionarios (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100),
    cargo VARCHAR(100),
    salario DECIMAL(10, 2)
);

-- Inserir dados de exemplo na tabela de clientes
INSERT INTO clientes (nome, email, telefone) VALUES
('João', 'joao@example.com', '123456789'),
('Maria', 'maria@example.com', '987654321');

-- Inserir dados de exemplo na tabela de produtos
INSERT INTO produtos (nome, preco, estoque) VALUES
('Camisa', 29.99, 50),
('Calça', 39.99, 30),
('Tênis', 59.99, 20);

-- Inserir um pedido de exemplo na tabela de pedidos
INSERT INTO pedidos (cliente_id, status, desconto, total) VALUES
(1, 'pendente', 5.00, 0.00);

-- Inserir itens de pedido de exemplo na tabela de itens do pedido
INSERT INTO itens_pedido (pedido_id, produto_id, quantidade, preco_unitario) VALUES
(1, 1, 2, 29.99),
(1, 3, 1, 59.99);

-- Inserir um pagamento de exemplo na tabela de pagamentos
INSERT INTO pagamentos (pedido_id, valor) VALUES
(1, 84.97);

-- Inserir dados de exemplo na tabela de funcionários
INSERT INTO funcionarios (nome, cargo, salario) VALUES
('Carlos', 'Gerente', 3000.00),
('Ana', 'Vendedora', 2000.00);

-- Consulta para obter informações detalhadas de um pedido específico
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
LEFT JOIN pagamentos ON pedidos.id = pagamentos.pedido_id
WHERE pedidos.id = 1;
