#  -------- ETAPA 1--------------

# -- Etapa 1: Criação da tabela Produtos SCRIPT
CREATE TABLE Produtos (
  id_produto INT PRIMARY KEY,
  nome VARCHAR(255) NOT NULL,
  preço DECIMAL(10, 2) NOT NULL,
  estoque INT NOT NULL,
  perecível BOOLEAN NOT NULL,
  marca VARCHAR(100),
  nacionalidade VARCHAR(100)
);

-- Etapa 1: Inserção de cinco produtos
INSERT INTO Produtos (id_produto, nome, preço, estoque, perecível, marca, nacionalidade)
VALUES (1, 'Produto A', 19.99, 100, TRUE, 'Marca A', 'Nacionalidade A');

INSERT INTO Produtos (id_produto, nome, preço, estoque, perecível, marca, nacionalidade)
VALUES (2, 'Produto B', 29.99, 50, FALSE, 'Marca B', 'Nacionalidade B');

INSERT INTO Produtos (id_produto, nome, preço, estoque, perecível, marca, nacionalidade)
VALUES (3, 'Produto C', 9.99, 200, TRUE, 'Marca C', 'Nacionalidade C');

INSERT INTO Produtos (id_produto, nome, preço, estoque, perecível, marca, nacionalidade)
VALUES (4, 'Produto D', 14.99, 75, FALSE, 'Marca D', 'Nacionalidade D');

INSERT INTO Produtos (id_produto, nome, preço, estoque, perecível, marca, nacionalidade)
VALUES (5, 'Produto E', 24.99, 120, TRUE, 'Marca E', 'Nacionalidade E');

-- Etapa 1: Verificação dos dados inseridos
SELECT * FROM Produtos;

![TABELA](https://github.com/CplGustavo/SQL/assets/144744164/0b0004f5-1e86-4523-9097-6473fe7bba5c)


# ESTAPA 2 ---------------------
Gere um relatório informando quantos produtos estão cadastrados;

SELECT COUNT(*) AS "Quantidade de Produtos Cadastrados" FROM Produtos;

![PRODUTOS CADASTRADOS](https://github.com/CplGustavo/SQL/assets/144744164/232c2473-cd8a-4191-8617-bd157341c46d)



Gere um relatório informando o preço médio dos produtos;


SELECT AVG(preço) AS "Preço Médio dos Produtos" FROM Produtos;

![PREÇO MEDIO PRODUTOS](https://github.com/CplGustavo/SQL/assets/144744164/d4cbf9b5-c1ea-4706-b96d-4160dfec0ad3)



---- 1 Selecione a média dos preços dos produtos em 2 grupos: perecíveis e não perecíveis;

SELECT perecível, AVG(preço) AS "Média de Preço" FROM Produtos GROUP BY perecível;




----  2 Selecione a média dos preços dos produtos agrupados pelo nome do produto;


SELECT nome, AVG(preço) AS "Média de Preço" FROM Produtos GROUP BY nome;





---- 3 Selecione a média dos preços e total em estoque dos produtos;

SELECT AVG(preço) AS "Média de Preço", SUM(estoque) AS "Total em Estoque" FROM Produtos;





---- 4 Selecione o nome, marca e quantidade em estoque do produto mais caro;

SELECT nome, marca, estoque FROM Produtos WHERE preço = (SELECT MAX(preço) FROM Produtos);



----- 5 Selecione os produtos com preço acima da média;

SELECT * FROM Produtos WHERE preço > (SELECT AVG(preço) FROM Produtos);




----- 6 Selecione a quantidade de produtos de cada nacionalidade.

SELECT nacionalidade, COUNT(*) AS "Quantidade" FROM Produtos GROUP BY nacionalidade;












