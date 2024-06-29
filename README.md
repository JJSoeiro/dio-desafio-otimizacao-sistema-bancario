<h1>
    <a href="https://www.dio.me/">
     <img align="center" width="40px" src="https://hermes.dio.me/tracks/648ef080-6c4b-4e54-bf72-34f62030f350.png"></a>
    <span> Bootcamp Python AI Backend Developer - VIVO</span>
</h1>

##   Desafio de Projeto Otimizando o sistema bancário com Python

### Objetivo Geral

Separar as funções existentes de saque, depósito e extrato em funções. Criar duas novas funções: cadastrar usuário (cliente) e cadastrar conta bancária.

### Desafio

Precisamos deixar nosso Código mais modularizado, para isso vamos criar funções para as operações existentes: sacar, depositar e visualizar histórico. Além disso, para a versão 2 do nosso Sistema precisamos criar duas novas funções: criar usuário (cliente do banco) e criar conta corrente (vincular com usuário).

### Separação em funções

Devemos criar funções para todas as operações do Sistema. Para exercitar tudo o que aprendemos neste módulo, cada função vai ter uma regra na passagem de argumentos. O retorno e a forma como serão chamadas, pode ser definida por você da forma que achar melhor.

### Operação de saque

A função saque deve receber os argumentos apenas por nome (keyword only). Sugestão de argumentos: saldo, valor, extrato, limite, numero_saques, limite_saques. Sugestão de retorno: saldo, extrato.

### Operação de depósito

A função depósito deve receber os argumentos apenas por posição (positional only). Sugestão de argumentos: saldo, valor, extrato. Sugestão de retorno: saldo, extrato.

### Operação de extrato

A função extrato deve receber os argumentos por posição e nome (positional Only e keyword Only). Argumentos posicionais : saldo, argumentos nomeados: extrato.

### Novas funções

Precisamos criar duas novas funções: criar usuário e criar conta corrente. Fique à vontade para adicionar mais funções, exemplo: listar contas.

### Criar usuário (Cliente)

O programa deve armazenar os usuários em uma lista, um usuário é composto por: nome, data de nascimento, cpf e endereço. O endereço é uma string com o formato: logradouro, nro – bairro – cidade / sigla estado. Deve ser armazenado somente os números do CPF. Não podemos cadastrar 2 usuários com o mesmo CPF.

### Criar conta corrente

O programa deve armazenar contas em uma lista, uma conta é composta por: agência, número da conta e usuário. O número da conta é sequencial, iniciando em 1. O número da agência é fixo: “0001”. O usuário pode ter mais de uma conta, mas uma conta pertence a somente um usuário.

### Dica

Para vincular um usuário a uma conta, filtre a lista de usuários buscando o número do CPF informando para cada usuário da lista.

### Ferramentas

![Python](https://img.shields.io/badge/Python-000?style=for-the-badge&logo=python)
[![GitHub](https://img.shields.io/badge/GitHub-000?style=for-the-badge&logo=github&logoColor=30A3DC)](https://docs.github.com/)

### Utilitários

[![Badges](https://img.shields.io/badge/Badges-30A3DC?style=for-the-badge)](https://github.com/digitalinnovationone/dio-lab-open-source/blob/main/utils/badges/badges.md)
