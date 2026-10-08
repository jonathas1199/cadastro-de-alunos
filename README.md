NOME DOS INTEGRANTES Cauã Pedro Fagundes da Silva - 01884138
Jonathas Ferreira Alves de Mendonça Barbosa - 01910039
Pedro Henrique Ismael de Souza - 01867006
# ==========================================
# SISTEMA DE CADASTRO DE ALUNOS
# ==========================================

# Lista que armazenará todos os alunos
alunos = []


# ------------------------------------------
# 1. ADICIONAR ALUNO
# ------------------------------------------
def adicionar_aluno():
    print("\n===== ADICIONAR ALUNO =====")

    nome = input("Digite o nome do aluno: ").strip()

    # Validação da idade
    while True:
        try:
            idade = int(input("Digite a idade do aluno: "))

            if idade > 0:
                break
            else:
                print("A idade deve ser maior que zero.")

        except ValueError:
            print("Digite uma idade válida.")


    # Validação da nota
    while True:
        try:
            nota = float(input("Digite a nota (0 a 10): "))

            if 0 <= nota <= 10:
                break
            else:
                print("A nota deve estar entre 0 e 10.")

        except ValueError:
            print("Digite uma nota válida.")


    # Dicionário com os dados do aluno
    aluno = {
        "nome": nome,
        "idade": idade,
        "nota": nota
    }

    # Adiciona o dicionário à lista
    alunos.append(aluno)

    print("\nAluno cadastrado com sucesso!")


# ------------------------------------------
# 2. LISTAR TODOS OS ALUNOS
# ------------------------------------------
def listar_alunos():
    print("\n===== LISTA DE ALUNOS =====")

    if len(alunos) == 0:
        print("Não há nenhum aluno cadastrado.")
        return

    for i, aluno in enumerate(alunos, start=1):
        print(f"\nAluno {i}")
        print(f"Nome: {aluno['nome']}")
        print(f"Idade: {aluno['idade']} anos")
        print(f"Nota: {aluno['nota']:.1f}")


# ------------------------------------------
# 3. BUSCAR ALUNO PELO NOME
# ------------------------------------------
def buscar_aluno():
    print("\n===== BUSCAR ALUNO =====")

    nome_busca = input("Digite o nome do aluno: ").strip()

    encontrado = False

    for aluno in alunos:
        if aluno["nome"].lower() == nome_busca.lower():
            print("\nAluno encontrado!")
            print(f"Nome: {aluno['nome']}")
            print(f"Idade: {aluno['idade']} anos")
            print(f"Nota: {aluno['nota']:.1f}")

            encontrado = True
            break

    if not encontrado:
        print("\nAluno não encontrado.")


# ------------------------------------------
# 4. REMOVER ALUNO
# ------------------------------------------
def remover_aluno():
    print("\n===== REMOVER ALUNO =====")

    nome_remover = input("Digite o nome do aluno: ").strip()

    for aluno in alunos:
        if aluno["nome"].lower() == nome_remover.lower():
            alunos.remove(aluno)
            print("\nAluno removido com sucesso!")
            return

    print("\nAluno não encontrado.")


# ------------------------------------------
# 5. MOSTRAR MÉDIA GERAL
# ------------------------------------------
def mostrar_media():
    print("\n===== MÉDIA GERAL =====")

    if len(alunos) == 0:
        print("Não há alunos cadastrados para calcular a média.")
        return

    soma = 0

    for aluno in alunos:
        soma += aluno["nota"]

    media = soma / len(alunos)

    print(f"Média geral das notas: {media:.2f}")


# ------------------------------------------
# MENU PRINCIPAL
# ------------------------------------------
while True:

    print("\n================================")
    print("   SISTEMA DE CADASTRO DE ALUNOS")
    print("================================")
    print("1. Adicionar aluno")
    print("2. Listar todos os alunos")
    print("3. Buscar aluno pelo nome")
    print("4. Remover aluno")
    print("5. Mostrar média geral das notas")
    print("6. Sair")
    print("================================")

    opcao = input("Escolha uma opção: ")

    if opcao == "1":
        adicionar_aluno()

    elif opcao == "2":
        listar_alunos()

    elif opcao == "3":
        buscar_aluno()

    elif opcao == "4":
        remover_aluno()

    elif opcao == "5":
        mostrar_media()

    elif opcao == "6":
        print("\nPrograma encerrado. Até mais!")
        break

    else:
        print("\nOpção inválida! Escolha uma opção de 1 a 6.")
