import textwrap

def entrar_no_sistema():
    menu = '''

      Bem Vindo, selecione à opção desajada.
    ==========================================
    [1]\tJá sou cliente. Entrar no sistema.
    [2]\tNão sou cliente. Abrir conta.
    [0]\tSair

    => '''
    return input(textwrap.dedent(menu))


def escolher_acesso():
    menu = '''

          Escolha a forma de acesso.
    ======================================
    Agncia: 0001

    [ct]\tConta.
    [cp]\tCPF.
    [q]\tSair

    => '''
    return input(textwrap.dedent(menu))


def consultar_contas():
    menu = """

                     MENU
    ======================================
    [d]\tDepositar
    [s]\tSacar
    [e]\tExtrato
    [nc]\tAbrir nova conta
    [lc]\tListar contas
    [q]\tSair
    => """
    return input(textwrap.dedent(menu))


def cadastrar_clientes():
    menu = """

                     MENU
    ======================================
    [cc]\tCadastrar cliente
    [ac]\tAbrir conta
    [lc]\tListar conta
    [q]\tSair
    => """
    return input(textwrap.dedent(menu))


def filtrar_conta(contas, numero_conta):
    contas_filtradas = [conta for conta in contas if conta['numero_conta'] == numero_conta]
    return contas_filtradas[0] if contas_filtradas else None


def filtrar_cliente(clientes, cpf):
    clientes_filtrados = [cliente for cliente in clientes if cliente['cpf'] == cpf]
    return clientes_filtrados[0] if clientes_filtrados else None


def filtrar_cpf(contas, cpf):
    cpf_filtrados = [conta for conta in contas if conta['cpf'] == cpf]
    return cpf_filtrados[0] if cpf_filtrados else None


def acessar_conta(contas, saldo, extrato, numero_saques, limite, LIMITE_SAQUES, AGENCIA, clientes):
    numero_conta = int(input('Digite o número da conta: '))
    filtro_conta = filtrar_conta(contas, numero_conta)
    
    if filtro_conta:
        senha = input('Digite a senha com 6 dígitos: ')
        
        if senha == filtro_conta['senha']:
            print('\n=== Acesso liberado. ===')
            seleciona_funcao_conta = selecionar_funcoes_conta(contas, saldo, extrato, numero_saques, limite, LIMITE_SAQUES, AGENCIA, clientes)
            
        else:
            print('\n=== Operação falhou! Senha inválida. ===')

    else:
        print('\n=== Operação falhou! Conta inválida. ===')


def acessar_cpf(contas, saldo, extrato, numero_saques, limite, LIMITE_SAQUES, AGENCIA, clientes):
    cpf = input('Informe o CPF (somente os números): ')
    cpf_filtrado = filtrar_cpf(contas, cpf)
    
    if cpf_filtrado:
        senha = input('Digite a senha com 6 dígitos: ')
        
        if senha == cpf_filtrado['senha']:
            print('\n=== Acesso liberado. ===')
            seleciona_funcao_conta = selecionar_funcoes_conta(contas, saldo, extrato, numero_saques, limite, LIMITE_SAQUES, AGENCIA, clientes)

        else:
            print('\n=== Operação falhou! Senha inválida. ===')
                        
    else:
        print('\n=== Operação falhou! CPF inválido. ===')


def depositar(saldo, valor_deposito, extrato, /):
    if valor_deposito > 0:
        saldo += valor_deposito
        extrato += f'   Depósito: R$ {valor_deposito:17.2f} (+)\n'
        print(f'\n=== Deposito de R$ {valor_deposito:.2f} realizado com sucesso! ===')
        
    else:
        print("\n=== Operação falhou! O valor informado é inválido. ===")
 
    return saldo, extrato


def sacar(saldo, valor_sacado, extrato, limite, numero_saques, limite_saques):
    excedeu_saldo = valor_sacado > saldo
    excedeu_limite = valor_sacado > limite
    excedeu_saques = numero_saques >= limite_saques

    if excedeu_saldo:
        print('\n=== Operação falhou! Saldo insuficiente para saque. ===')
        
    elif excedeu_limite:
        print('\n=== Operação falhou! Valor solicitado acima do limite de saque de R$ 500,00. ===')
        
    elif excedeu_saques:
        print(f'\n=== Operação falhou! Ultrapassado o limite de {limite_saques} saques diários. ===')
        
    elif valor_sacado > 0:
        saldo -= valor_sacado
        extrato += f"   Saque:    R$ {valor_sacado:17.2f} (-)\n"
        numero_saques += 1
        print(f'\n=== Saque de R$ {valor_sacado:.2f} realizado com sucesso! ===')
        
    else:
        print('\n=== Operação falhou! O valor informado é inválido. ===')
    
    return saldo, extrato, numero_saques


def exibir_extrato(saldo, numero_saques, /, *, extrato):
    print('\n            Extrato Bancário')
    print('=' * 40)
    print('   Não foram realizadas movimentações.' if not extrato else extrato)
    print(f'\n   Saldo:    R$ {saldo:17.2f}')
    print(f'\n   Numero de Saques:  {numero_saques:12}/3')
    print('=' * 40)


def criar_conta(agencia, numero_conta, clientes, cpf, senha):
    cpf = input("Informe o CPF do usuário: ")
    cliente_filtrado = filtrar_cliente(clientes, cpf)

    if cliente_filtrado:
        senha = input('Crie uma senha com 6 dígitos: ')
        nome = cliente_filtrado['nome']
        print('\n=== Conta criada com sucesso! ===')
        return {"agencia": agencia, "numero_conta": numero_conta, "cliente": nome, 'cpf': cpf, 'senha': senha}

    print('\n=== Usuário não encontrado, fluxo de criação de conta encerrado! ===')


def listar_contas(contas):
    cpf = input("Informe o CPF do usuário: ")
    for conta in contas:
        if cpf == conta['cpf']:
            linha = f'''\
                Agência:\t{conta['agencia']}
                C/C:\t\t{conta['numero_conta']}
                Titular:\t{conta['cliente']}
                CPF:\t\t{conta['cpf']}
            '''
            print('=' * 100)
            print(textwrap.dedent(linha))


def selecionar_funcoes_conta(contas, saldo, extrato, numero_saques, limite, LIMITE_SAQUES, AGENCIA, clientes):
    while True:
        consulta_conta = consultar_contas()

        if consulta_conta == 'd':
            valor_deposito = float(input('informe o valor a ser depositado: '))

            saldo, extrato = depositar(saldo, valor_deposito, extrato)

        elif consulta_conta == 's':
            valor_sacado = float(input('Informe o valor do saque: '))

            saldo, extrato, numero_saques = sacar(
                saldo,
                valor_sacado,
                extrato,
                limite,
                numero_saques,
                LIMITE_SAQUES,
            )

        elif consulta_conta == 'e':
            exibir_extrato(saldo, numero_saques, extrato = extrato)

        elif consulta_conta == 'nc':
            numero_conta = len(contas) + 1
            senha = 0
            cpf = ''
            conta = criar_conta(AGENCIA, numero_conta, clientes, cpf, senha)

            if conta:
                contas.append(conta)

        elif consulta_conta == 'lc':
            listar_contas(contas)

        elif consulta_conta == 'q':
            print('\n=== Obrigado por utilizar os nossos serviços! ===')
            break

        else:
            print('\n=== Opção selecionada incorreta, selecione a opção correta. ===')


def cadastrar_novo_cliente(clientes):
    cpf = input('Informe o CPF (somente número): ')
    cliente_filtrado = filtrar_cliente(clientes, cpf)

    if cliente_filtrado:
        print('\n=== Já existe cliente com esse CPF! ===')
        return

    nome = input('Informe o nome completo: ')
    data_nascimento = input('Informe a data de nascimento (dd-mm-aaaa): ')
    endereco = input('Informe o endereço (logradouro, nro - bairro - cidade/sigla estado): ')

    clientes.append({'nome': nome, 'data_nascimento': data_nascimento, 'cpf': cpf, 'endereco': endereco})

    print('=== Cliente cadastrado com sucesso! ===')


def selecionar_funcoes_cadastro(contas, AGENCIA, numero_conta, clientes, cpf, senha):
    while True:
        cadastro_cliente = cadastrar_clientes()

        if cadastro_cliente == 'cc':
            cadastrar_novo_cliente(clientes)

        elif cadastro_cliente == 'ac':
            numero_conta = len(contas) + 1
            conta = criar_conta(AGENCIA, numero_conta, clientes, cpf, senha)

            if conta:
                contas.append(conta)

        elif cadastro_cliente == 'lc':
            listar_contas(contas)
                
        elif cadastro_cliente == 'q':
            print('\n=== Obrigado por utilizar os nossos serviços! ===')
            break

        else:
            print('\n=== Opção selecionada incorreta, selecione a opção correta. ===')



def main():
    LIMITE_SAQUES = 3
    AGENCIA = '0001'

    saldo = 0
    limite = 500
    extrato = ''
    extrato_simplificado = ''
    numero_saques = 0
    numero_conta = 0
    senha = 0
    cpf = ''
    
    clientes = [
        {'nome': 'Gabriel Pereira', 'data_nascimento': '15-11-1980', 'cpf': '11111111111', 'endereco': 'Rua: Avila, 5 - Tijuca - Rio de Janeiro/RJ'},
        {'nome': 'Luisa Fonseca', 'data_nascimento': '02-08-1985', 'cpf': '22222222222', 'endereco': 'Rua: Humaita, 99 - Humaita - Rio de Janeiro/RJ'},
    ]

    contas = [
        {'agencia': '0001', 'numero_conta': 1, 'cliente': 'Gabriel Pereira', 'cpf': '11111111111', 'senha': '111111'},
        {'agencia': '0001', 'numero_conta': 2, 'cliente': 'Luisa Fonseca', 'cpf': '22222222222', 'senha': '222222'},
    ]


    while True:

        entra_sistema = entrar_no_sistema()

        if entra_sistema == '1':
            escolha_acesso = escolher_acesso()

            if escolha_acesso == 'ct':
                acessar_conta(contas, saldo, extrato, numero_saques, limite, LIMITE_SAQUES, AGENCIA, clientes)

            elif escolha_acesso == 'cp':
                acessar_cpf(contas, saldo, extrato, numero_saques, limite, LIMITE_SAQUES, AGENCIA, clientes)

            elif escolha_acesso == 'q':
                print('\n=== Obrigado por utilizar os nossos serviços! ===')
                break
            
            else:
                print('\n=== Opção selecionada incorreta, selecione a opção correta. ===')        

        elif entra_sistema == '2':
            selecionar_funcoes_cadastro(contas, AGENCIA, numero_conta, clientes, cpf, senha)

        elif entra_sistema == '0':
            print('\n=== Aguardamos o seu retorno! ===')
            break

        else:
            print('\n=== Opção selecionada incorreta, selecione a opção correta. ===')

main()
