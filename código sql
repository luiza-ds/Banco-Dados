-- ===================================================
-- 1. Criação de Tabelas
-- ===================================================

CREATE TABLE Loja 
(CNPJ character varying(14), 
gerente_geral character varying(100), 
nome character varying(100), 
endereco character varying(255), 
PRIMARY KEY(CNPJ));

CREATE TABLE Fornecedores 
(CNPJ character varying(14), 
nome character varying(100), 
endereco character varying(255), 
ramo_atividade character varying(50), 
tel integer, 
PRIMARY KEY(CNPJ));

CREATE TABLE Vendedor 
(cod_identificacao character varying(10), 
nome character varying(100), 
CPF character varying(11) UNIQUE, 
endereco character varying(255), 
data_admissao date, 
data_desligamento date, 
cnpj_loja character varying(14), 
PRIMARY KEY(cod_identificacao), 
FOREIGN KEY (cnpj_loja) REFERENCES Loja(cnpj));

CREATE TABLE Mercadorias_Compradas 
(codigo character varying(20), 
id_fornecedor character varying(14), 
id_loja character varying(14),
nome character varying(100), 
data_compra date, 
quantidade integer, 
unidade character varying(20), 
preco_unitario numeric(10,2), 
PRIMARY KEY (codigo), 
FOREIGN KEY (id_fornecedor) REFERENCES Fornecedores(CNPJ), 
FOREIGN KEY (id_loja) REFERENCES Loja(CNPJ));

CREATE TABLE Cliente 
(CPF character varying(11),
nome character varying(100), 
endereco character varying(255), 
data_nascimento date, 
data_cadastro date, 
profissao character varying(50), 
tel integer, 
PRIMARY KEY(CPF));

CREATE TABLE Venda 
(id_venda character varying(20), 
CPF_cliente character varying(11), 
codigo_vendedor character varying(10), 
quantidade_vendida integer, 
data_venda date, 
PRIMARY KEY(id_venda), 
FOREIGN KEY (CPF_cliente) REFERENCES Cliente(CPF), 
FOREIGN KEY (codigo_vendedor) REFERENCES Vendedor(cod_identificacao));

CREATE TABLE Mercadoria_Vendida 
(codigo character varying(20), 
codigo_comprada character varying(20), 
cod_venda character varying(20), 
nome character varying(100), 
quantidade integer, 
data_venda date, 
unidade character varying(20), 
preco_unitario numeric(10,2), 
PRIMARY KEY(codigo), 
FOREIGN KEY (codigo_comprada)REFERENCES Mercadorias_Compradas(codigo), 
FOREIGN KEY (cod_venda) REFERENCES Venda(id_venda));

CREATE TABLE Loja_Fornecedor
(cnpj_loja character varying(14), 
cnpj_fornecedor character varying(14), 
PRIMARY KEY(cnpj_loja, cnpj_fornecedor), 
FOREIGN KEY(cnpj_loja) REFERENCES Loja(cnpj), 
FOREIGN KEY(cnpj_fornecedor) REFERENCES Fornecedores(CNPJ));


-- ===================================================
-- 2. Inserção de Dados
-- ===================================================

INSERT INTO Loja (CNPJ, gerente_geral, nome, endereco) VALUES 
('00625701425612', 'Paulo Junqueira', 'Oliveira Ferragens', 'Rua São Francisco, Bairro Av Getúlio Vargas, 205, Riberao preto, SP'), 
('12345678901234', 'Carla Mendes', 'Constrular', 'Av Brasil, 1001, Centro, Uberaba, MG'), 
('98765432109876', 'Roberto Lima', 'Casa & Obra', 'Rua das Palmeiras, 88, Bairro Industrial, Uberlândia, MG');

INSERT INTO Fornecedores (CNPJ, nome, endereco, ramo_atividade, tel) VALUES 
('00014825978452', 'Metais Ferragens', 'Rua Indaia, 53, Copacabana, Catalao, GO', 'atacadista de ferragens', 32334455), 
('00782415696453', 'Giro', 'Av Deodoro da Fonseca, 4000, Liberdade, Araxa, MG', 'atacadista de ferragens', 98887766), 
('00552876149524', 'KFH', 'Av Presidente Prudente, 874, Jardim Versailles, Araguari, MG', 'atacadista e varejista de ferragens', 91234557);

INSERT INTO Vendedor (cod_identificacao, nome, CPF, endereco, data_admissao, data_desligamento, cnpj_loja) VALUES 
('A0122', 'Anderson Almeida', '01139645217', 'rua americano, brasil, Uberlandia, MG', '2007-09-25', NULL, '00625701425612'), 
('M7821', 'Mauricio Lima', '75163428491', 'rua da crista, guarani, Uberaba, MG', '2021-04-07', NULL, '12345678901234'), 
('J6513', 'Joao Victor', '03912874186', 'rua antonio gazeta, Imperio, Riberao Preto, SP', '2018-03-16', NULL, '98765432109876');

INSERT INTO Mercadorias_Compradas (codigo, id_fornecedor, nome, data_compra, quantidade, unidade, preco_unitario, id_loja) VALUES 
('PM0102', '00014825978452', 'porca', '2024-01-13', 100, 'CX', 0.50, '00625701425612'), 
('PM0103', '00014825978452', 'parafuso', '2024-04-27', 200, 'CX', 0.90, '00625701425612'), 
('CG7485', '00782415696453', 'chave de fenda', '2024-02-14', 60, 'DZ', 10.00, '12345678901234'), 
('AG7182', '00782415696453', 'alicate', '2024-08-06', 48, 'DZ', 12.00, '12345678901234'), 
('MK4516', '00552876149524', 'martelo', '2025-02-25', 72, 'DZ', 15.00, '98765432109876'), 
('PK4156', '00552876149524', 'prego', '2025-01-18', 200, 'CX', 0.60, '98765432109876');

INSERT INTO Cliente (CPF, nome, endereco, data_nascimento, data_cadastro, profissao, tel) VALUES 
('01425878941', 'Antonio Fagundes', 'rua dos amentes, 104, Divinópolis, MG', '1965-04-15', '2017-06-26', 'carpinteiro', 98414652), 
('32178974126', 'Americo da Silva', 'rua flamingo, 14, Uberlândia, MG', '1975-10-07', '2023-07-12', 'analista de crédito', 9914263), 
('98415675324', 'Maria Rocha', 'rua 13 de março, centro, Catalão, GO', '1999-12-28', '2024-05-19', 'faturista', 99153247);

INSERT INTO Venda (id_venda, CPF_cliente, codigo_vendedor, quantidade_vendida, data_venda) VALUES 
('AF001', '01425878941', 'A0122', 10, '2025-04-04'), 
('AS4123', '32178974126', 'M7821', 5, '2024-12-23'), 
('MR2634', '98415675324', 'J6513', 8, '2024-09-25'), 
('AF7485', '01425878941', 'M7821', 5, '2025-01-05'), 
('MR3614', '98415675324', 'A0122', 15, '2024-08-31');

INSERT INTO mercadoria_vendida (codigo, codigo_comprada, cod_venda, nome, quantidade, data_venda, unidade, preco_unitario) VALUES ('AQ12', 'PM0102', 'AF001', 'porca', 5, '2025-04-04', 'UN', 0.80), ('AZ78', 'CG7485', 'AF001', 'chave de fenda', 5, '2025-04-04', 'UN', 15.00), ('QW36', 'PK4156', 'AS4123', 'prego', 5, '2024-12-23', 'UN', 0.90), ('JH1328', 'PM0103', 'MR2634', 'parafuso', 8, '2024-09-25', 'UN', 1.20), ('UG67', 'PK4156', 'AF7485', 'prego', 5, '2025-01-05', 'UN', 0.90), ('LP56', 'PK4156', 'MR3614', 'prego', 5, '2024-08-31', 'UN', 0.90), ('LP18', 'MK4516', 'MR3614', 'martelo', 1, '2024-08-31', 'UN', 23.00), ('SD87', 'PM0103', 'MR3614', 'parafuso', 9, '2024-08-31', 'UN', 1.20);

INSERT INTO loja_fornecedor(cnpj_loja, cnpj_fornecedor) VALUES ('00625701425612', '00014825978452'), ('00625701425612', '00782415696453'), ('12345678901234', '00552876149524'), ('98765432109876', '00782415696453');

-- ===================================================
-- 3. Junção de tabelas
-- ===================================================

SELECT Loja.cnpj, Loja.nome AS nome_loja, Fornecedores.cnpj AS cnpj_fornecedor, Fornecedores.nome AS nome_fornecedor FROM Loja JOIN Loja_Fornecedor ON Loja.cnpj = Loja_Fornecedor.cnpj_loja JOIN Fornecedores ON Loja_Fornecedor.cnpj_fornecedor = Fornecedores.cnpj;

SELECT Vendedor.cod_identificacao, Vendedor.nome AS nome_vendedor, Loja.nome AS nome_loja FROM Vendedor JOIN Loja ON Vendedor.cnpj_loja = Loja.cnpj;

SELECT Mercadorias_Compradas.codigo, Mercadorias_Compradas.nome AS nome_mercadoria, Mercadorias_Compradas.data_compra, Mercadorias_Compradas.quantidade, Mercadorias_Compradas.unidade, Mercadorias_Compradas.preco_unitario, Fornecedores.cnpj, Fornecedores.nome AS nome_fornecedores FROM Mercadorias_Compradas JOIN Fornecedores ON Mercadorias_Compradas.id_fornecedor = Fornecedores.cnpj;

SELECT Loja.CNPJ AS cnpj_loja, Loja.nome AS nome_loja, Mercadorias_Compradas.codigo AS codigo_mercadoria, Mercadorias_Compradas.nome AS nome_mercadoria, Mercadorias_Compradas.data_compra, Mercadorias_Compradas.quantidade, Mercadorias_Compradas.unidade, Mercadorias_Compradas.preco_unitario FROM Loja JOIN Mercadorias_Compradas ON Loja.CNPJ = Mercadorias_Compradas.id_loja;

SELECT Mercadorias_Compradas.codigo AS codigo_mercadoria_comprada, Mercadorias_Compradas.nome AS nome_mercadoria_comprada, Mercadorias_Compradas.data_compra, Mercadorias_Compradas.quantidade AS quantidade_comprada, Mercadorias_Compradas.preco_unitario AS preco_unitario_compra, Mercadoria_vendida.codigo AS codigo_mercadoria_vendida, Mercadoria_vendida.data_venda, Mercadoria_vendida.quantidade AS quantidade_vendida, Mercadoria_vendida.preco_unitario AS preco_unitario_venda FROM Mercadorias_Compradas JOIN Mercadoria_vendida ON Mercadorias_Compradas.codigo = Mercadoria_vendida.codigo_comprada;

SELECT Vendedor.cod_identificacao AS codigo_vendedor, Vendedor.nome AS nome_vendedor, Vendedor.CPF AS cpf_vendedor, Vendedor.endereco AS endereco_vendedor, Vendedor.data_admissao, Vendedor.data_desligamento, Venda.id_venda, Venda.CPF_cliente, Venda.quantidade_vendida, Venda.data_venda FROM Vendedor JOIN Venda ON Vendedor.cod_identificacao = Venda.codigo_vendedor;

SELECT Cliente.CPF AS cpf_cliente, Cliente.nome AS nome_cliente, Cliente.endereco AS endereco_cliente, Cliente.data_nascimento, Cliente.data_cadastro, Cliente.profissao, Cliente.tel, Venda.id_venda, Venda.codigo_vendedor, Venda.quantidade_vendida, Venda.data_venda FROM Cliente JOIN Venda ON Cliente.CPF = Venda.CPF_cliente;

SELECT Mercadoria_Vendida.codigo AS codigo_mercadoria_vendida, Mercadoria_vendida.nome AS nome_mercadoria_vendida, Mercadoria_vendida.quantidade AS quantidade_vendida, Mercadoria_vendida.preco_unitario AS preco_unitario_vendido, Venda.id_venda, Venda.data_venda, Cliente.nome AS nome_cliente FROM Mercadoria_vendida JOIN Venda ON Mercadoria_vendida.cod_venda = Venda.id_venda JOIN Cliente ON Venda.CPF_cliente = Cliente.CPF;

-- ===================================================
-- 4. Simulação de mercadoria comprada de fornecedores
-- ===================================================

INSERT INTO Mercadorias_Compradas (codigo, id_fornecedor, nome, data_compra, quantidade, unidade, preco_unitario, id_loja) VALUES 
('PD9001', '00014825978452', 'arruela', '2025-04-01', 300, 'CX', 0.30, '00625701425612'), 
('CH2010', '00782415696453', 'chave inglesa', '2025-04-03', 50, 'UN', 22.00, '12345678901234'), 
('AL4550', '00552876149524', 'alavanca', '2025-04-05', 40, 'UN', 35.00, '98765432109876'), 
('TR7894', '00552876149524', 'trena 5m', '2025-04-06', 80, 'UN', 9.50, '98765432109876');

-- ===================================================
-- 5. Simularemos vendas, diminuindo em nosso estoque.
-- ===================================================

INSERT INTO Venda (id_venda, CPF_cliente, codigo_vendedor, quantidade_vendida, data_venda) VALUES 
('V005', '01425878941', 'A0122', 150, '2025-04-20'), 
('V006', '32178974126', 'M7821', 40, '2025-04-25'), 
('V007', '98415675324', 'J6513', 40, '2025-05-01'),
('V008', '01425878941', 'A0122', 80, '2025-04-01'); 

INSERT INTO Mercadoria_Vendida (codigo, codigo_comprada, cod_venda, nome, quantidade, data_venda, unidade, preco_unitario) VALUES 
('PD9001-1', 'PD9001', 'V005', 'arruela', 150, '2025-04-20', 'CX', 0.30), 
('CH2010-1', 'CH2010', 'V006', 'chave inglesa', 40, '2025-04-25', 'UN', 22.00), 
('AL4550-1', 'AL4550', 'V007', 'alavanca', 40, '2025-05-01', 'UN', 35.00), 
('TR7894-1', 'TR7894', 'V008', 'trena 5m', 80, '2025-04-01', 'UN', 9.50);

UPDATE Mercadorias_Compradas SET quantidade = quantidade - 150 WHERE codigo = 'PD9001';

UPDATE Mercadorias_Compradas SET quantidade = quantidade - 40 WHERE codigo = 'CH2010';

UPDATE Mercadorias_Compradas SET quantidade = quantidade - 40 WHERE codigo = 'AL4550';

UPDATE Mercadorias_Compradas SET quantidade = quantidade - 80 WHERE codigo = 'TR7894';

-- ===================================================
-- 6. Faremos a exclusão das mercadorias zeradas no estoque
-- ===================================================

DELETE FROM mercadoria_vendida WHERE codigo_comprada = 'TR7894';
DELETE FROM mercadoria_vendida WHERE codigo_comprada = 'AL4550';

DELETE FROM Mercadorias_Compradas WHERE codigo = 'TR7894';
DELETE FROM Mercadorias_Compradas WHERE codigo = 'AL4550';

-- ===================================================
-- 7. Alteração nos dados
-- ===================================================

UPDATE Mercadorias_Compradas
SET nome = 'arruelas', preco_unitario = 0.40
WHERE codigo = 'PD9001'; 

UPDATE Mercadorias_Compradas
SET nome = 'martelos', preco_unitario = 14.99
WHERE codigo = 'MK4516';

UPDATE Mercadorias_Compradas
SET data_compra = '2025-05-05', preco_unitario = 11.99
WHERE codigo = 'AG7182';

-- ===================================================
-- 8. Relatório das mercadorias mais e menos vendidas
-- ===================================================

CREATE VIEW Relatorio_Mais_Vendidas AS 
SELECT Mercadoria_vendida.nome AS nome_mercadoria,
	SUM(Mercadoria_vendida.quantidade) AS total_vendido
FROM 
    Mercadoria_vendida
JOIN 
    Venda ON Mercadoria_vendida.cod_venda = Venda.id_venda
GROUP BY 
    Mercadoria_vendida.nome
ORDER BY 
    total_vendido DESC;

select * from Relatorio_Mais_Vendidas;


CREATE VIEW R_Menos_Vendidas AS
SELECT 
    Mercadoria_vendida.nome AS nome_mercadoria,
    SUM(Mercadoria_vendida.quantidade) AS total_vendido
FROM 
    Mercadoria_vendida
JOIN 
    Venda ON Mercadoria_vendida.cod_venda = Venda.id_venda
GROUP BY 
    Mercadoria_vendida.nome
ORDER BY 
    total_vendido ASC;

-- ===================================================
-- 9. Relatório Lucro e Prejuízo
-- ===================================================

CREATE VIEW Relatorio_LucroPreju AS
SELECT 
    Mercadorias_Compradas.codigo AS codigo_mercadoria,
    Mercadorias_Compradas.nome AS nome_mercadoria,
    SUM(Mercadoria_Vendida.quantidade) AS total_vendido,
    Mercadorias_Compradas.preco_unitario AS preco_compra,
    Mercadoria_Vendida.preco_unitario AS preco_venda,
    SUM(Mercadoria_Vendida.quantidade) * Mercadoria_Vendida.preco_unitario AS total_venda,
    SUM(Mercadoria_Vendida.quantidade) * Mercadorias_Compradas.preco_unitario AS total_compra,
    (SUM(Mercadoria_Vendida.quantidade) * Mercadoria_Vendida.preco_unitario) - (SUM(Mercadoria_Vendida.quantidade) * Mercadorias_Compradas.preco_unitario) AS lucro_prejuizo
FROM 
    Mercadorias_Compradas 
JOIN 
    Mercadoria_vendida  ON Mercadorias_Compradas.codigo = Mercadoria_Vendida.codigo_comprada
GROUP BY 
    Mercadorias_Compradas.codigo, Mercadorias_Compradas.nome, Mercadorias_Compradas.preco_unitario, Mercadoria_Vendida.preco_unitario

-- ===================================================
-- 10. Relatório das mercadorias em estoque
-- ===================================================

CREATE VIEW Relatorio_Estoque AS 
SELECT codigo, nome, quantidade
FROM Mercadorias_Compradas 
ORDER BY 
quantidade ASC;	
