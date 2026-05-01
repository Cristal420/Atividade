# Classe Paciente
class Paciente:
    def __init__(self, nome, idade):
        self.__nome = nome
        self.set_idade(idade)

    def get_nome(self):
        return self.__nome

    def get_idade(self):
        return self.__idade

    def set_idade(self, idade):
        if idade >= 0:
            self.__idade = idade
        else:
            print("Idade inválida.")


# Classe Medico
class Medico:
    def __init__(self, nome, crm):
        self.__nome = nome
        self.set_crm(crm)

    def get_nome(self):
        return self.__nome

    def get_crm(self):
        return self.__crm

    def set_crm(self, crm):
        if crm.strip() != "":
            self.__crm = crm
        else:
            print("CRM inválido.")


# Classe Medicamento
class Medicamento:
    def __init__(self, nome, dosagem):
        self.__nome = nome
        self.set_dosagem(dosagem)

    def get_nome(self):
        return self.__nome

    def get_dosagem(self):
        return self.__dosagem

    def set_dosagem(self, dosagem):
        if dosagem > 0:
            self.__dosagem = dosagem
        else:
            print("Dosagem inválida.")


# Classe Consulta (Composição)
class Consulta:
    def __init__(self, paciente, medico):
        self.__paciente = paciente
        self.__medico = medico
        self.__medicamentos = []

    def adicionar_medicamento(self, medicamento):
        self.__medicamentos.append(medicamento)

    def gerar_resumo(self):
        print("=== RESUMO DA CONSULTA ===")
        print("Paciente:", self.__paciente.get_nome(),
              "| Idade:", self.__paciente.get_idade())

        print("Médico:", self.__medico.get_nome(),
              "| CRM:", self.__medico.get_crm())

        print("Medicamentos Prescritos:")
        for m in self.__medicamentos:
            print("-", m.get_nome(),
                  "| Dosagem:", m.get_dosagem(), "mg")


# Programa principal
paciente = Paciente("Carlos Silva", 35)
medico = Medico("Dra. Ana Souza", "CRM12345")

med1 = Medicamento("Paracetamol", 500)
med2 = Medicamento("Ibuprofeno", 400)

consulta = Consulta(paciente, medico)

consulta.adicionar_medicamento(med1)
consulta.adicionar_medicamento(med2)

consulta.gerar_resumo()
