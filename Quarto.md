class Quarto:
    def __init__(self, numero, tipo, preco_diario):
        self.numero = numero
        self.tipo = tipo
        self.preco_diario = preco_diario
        self.disponivel = True

class Reserva:
    def __init__(self, nome_hospede, check_in, check_out, numero_quarto, tipo_quarto):
        self.nome_hospede = nome_hospede
        self.check_in = check_in
        self.check_out = check_out
        self.numero_quarto = numero_quarto
        self.tipo_quarto = tipo_quarto

class Hotel:
    def __init__(self):
        self.quartos = []
        self.reservas = []

    def cadastrar_quarto(self, numero, tipo, preco_diario):
        quarto = Quarto(numero, tipo, preco_diario)
        self.quartos.append(quarto)

    def cadastrar_reserva(self, nome_hospede, check_in, check_out, numero_quarto, tipo_quarto):
        reserva = Reserva(nome_hospede, check_in, check_out, numero_quarto, tipo_quarto)
        self.reservas.append(reserva)

    def check_in(self, numero_quarto):
        for quarto in self.quartos:
            if quarto.numero == numero_quarto and quarto.disponivel:
                quarto.disponivel = False
                print(f"Check-in realizado no quarto {numero_quarto}.")
                return
        print(f"Quarto {numero_quarto} não está disponível.")

    def check_out(self, numero_quarto):
        for quarto in self.quartos:
            if quarto.numero == numero_quarto and not quarto.disponivel:
                quarto.disponivel = True
                print(f"Check-out realizado no quarto {numero_quarto}.")
                return
        print(f"Quarto {numero_quarto} já está disponível.")

    def gerar_relatorio_ocupacao(self):
        print("Relatório de Ocupação de Quartos:")
        for quarto in self.quartos:
            status = "Ocupado" if not quarto.disponivel else "Disponível"
            print(f"Quarto {quarto.numero} ({quarto.tipo}) - {status}")

    def gerar_historico_reservas(self):
        print("Histórico de Reservas:")
        for reserva in self.reservas:
            print(f"Hóspede: {reserva.nome_hospede}, Quarto: {reserva.numero_quarto}, Check-in: {reserva.check_in}, Check-out: {reserva.check_out}")