# 🛠️ Sistema de Gerenciamento de Loja de Ferragens – Projeto em PostgreSQL

Este repositório contém o desenvolvimento de um sistema de banco de dados relacional voltado à gestão de uma **loja de ferragens**, utilizando **PostgreSQL** como SGBD.

## 📌 Objetivo

Criar um sistema capaz de:
- Gerenciar compras de mercadorias feitas por fornecedores.
- Controlar vendas realizadas para clientes.
- Acompanhar o estoque da loja.
- Gerar relatórios de desempenho, como lucros/prejuízos e produtos mais/menos vendidos.

## 🧱 Estrutura do Banco de Dados

O modelo contempla as seguintes entidades:

- **Loja**
- **Fornecedor**
- **Cliente**
- **Vendedor**
- **Mercadorias_Compradas**
- **Mercadoria_Vendida**
- **Venda**
- **Loja_Fornecedor** (tabela de relacionamento N:M)

Além disso, foram definidos relacionamentos com cardinalidades 1:1, 1:N e N:M, e chaves estrangeiras garantindo a integridade referencial.

## 🔄 Funcionalidades Simuladas

- Inserção de dados de fornecedores, clientes, vendedores e lojas.
- Simulação de compras de mercadorias por lojas.
- Simulação de vendas com atualização de estoque.
- Exclusão de mercadorias esgotadas do banco.
- Atualização de atributos.
- Criação de views para relatórios automatizados.

## 📊 Relatórios Gerados

- **Mercadorias mais vendidas**
- **Mercadorias menos vendidas**
- **Lucro ou prejuízo por mercadoria**
- **Estoque atual (com nome em ordem crescente)**
- **Mercadorias esgotadas que foram vendidas**
