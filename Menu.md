def menu():
    hotel = Hotel()
    while True:
        print("\n1. Cadastrar Quarto")
        print("2. Cadastrar Reserva")
        print("3. Check-in")
        print("4. Check-out")
        print("5. Relatório de Ocupação")
        print("6. Histórico de Reservas")
        print("7. Sair")

        escolha = input("Escolha uma opção: ")

        if escolha == "1":
            numero = input("Número do quarto: ")
            tipo = input("Tipo do quarto (solteiro, casal, suite): ")
            preco = float(input("Preço diário: "))
            hotel.cadastrar_quarto(numero, tipo, preco)
        else if escolha == "2":
            nome_hospede = input("Nome do hóspede: ")
            check_in = input("Data de check-in: ")
            check_out = input("Data de check-out: ")
            numero_quarto = input("Número do quarto reservado: ")
            tipo_quarto = input("Tipo de quarto reservado: ")
            hotel.cadastrar_reserva(nome_hospede, check_in, check_out, numero_quarto, tipo_quarto)
        else if escolha == "3":
            numero_quarto = input("Número do quarto para check-in: ")
            hotel.check_in(numero_quarto)
        else if escolha == "4":
            numero_quarto = input("Número do quarto para check-out: ")
            hotel.check_out(numero_quarto)
        else if escolha == "5":
            hotel.gerar_relatorio_ocupacao()
        else if escolha == "6":
            hotel.gerar_historico_reservas()
        else if escolha == "7":
            break
        else:
            print("Opção inválida.")
