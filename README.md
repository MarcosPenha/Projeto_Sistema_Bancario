# Projeto_Sistema_Bancario

### Fomos contratados por um grande banco para desenvolver o seu novo sistema. Esse banco deseja modernizar suas operações e para isso escolheu a linguagem Python. Para a primeira versão do sistema devemos implementar apenas 3 operações: depósito, saque e extrato. Deve ser possível depositar valores positivos para a minha conta bancária. A v1 do projeto trabalha apenas com 1 usuário, dessa forma não precisamos nos preocupar em identificar qual é o número da agência e conta bancária. Todos os depósitos devem ser armazenados em uma variável e exibidos na operação de extrato. O sistema deve permitir realizar 3 saques diários com limite máximo de R$500,00 por saque. Caso o usuário não tenha saldo em conta, o sistema deve exibir uma mensagem informando que não será possível sacar o dinheiro por falta de saldo. Todos os saques devem ser armazenados em uma variável e exibidos na operação de extrato. Essa operação deve listar todos os depósitos e saques realizados na conta. No fim da listagem deve ser exibido o saldo atual da conta. Se o extrato estiver em branco, exibira mensagem: Não foram realizadas movimentações. ###

menu = """ 

-------------- MRP CENTER BANK -----------------

[1] Depositar

[2] Sacar

[3] Consultar Extrato

[4] Sair

Selecione uma operação para iniciar """

-----------------------------------------------
saldo = 0

limite = 500

extrato = ""

numero_saques = 0

LIMITE_SAQUES = 3

while True:

    opcao = input(menu)

    if opcao == "1":
        valor = float(input("Entre com o valor do depósito: "))

        if valor > 0:
            saldo += valor
            extrato += f"Depósito: R$ {valor:.2f}\n"
                        
    elif opcao == "2":
      valor = float(input("Informe o valor do saque: "))
      
      excedeu_saldo = valor > saldo
      
      excedeu_limite = valor > limite
      
      excedeu_saques = numero_saques >= LIMITE_SAQUES
      
      if excedeu_saldo:
          print("Você não tem saldo suficiente, seu saldo é: ", saldo)
          
      elif excedeu_limite:
          print("O valor do saque excedeu o limite.\nSeu limite é: ", limite)
      
      elif excedeu_saques:
          print("Número máximo de saques excedido.\nSeu limite saque é: ", LIMITE_SAQUES)
      
      elif valor > 0:
          saldo -= valor
          extrato += f"Saque: R$ {valor:.2f}\n"
          numero_saques += 1
          
      else:
          print("O valor informado é inválido.")

    elif opcao == "3":
        print("\n----------- SEU EXTRATO BANCÁRIO É! ------------")
        print("Não foram realizadas movimentações." if not extrato else extrato)
        print(f"\nSaldo: R$ {saldo:.2f}")
        print("------------------------------------------------")

    elif opcao == "4":
         print('MRP CENTER BANK AGRADEÇE A PREFERÊNCIA!')
         print()
              
         break

    else:
        print("Por favor selecione novamente a operação desejada.")
