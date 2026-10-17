# TPC5: Aplicação para gestão de alunos 

## Autor

-Mariana Santiago Machado Moreiras 

-A115607

<img width="4032" height="3024" alt="IMG_4705" src="https://github.com/user-attachments/assets/fd849ae9-f832-4535-a136-5ea5da8f9484" />


## Resumo 

Desenvolvimento de uma aplicação para a gestão de alunos, através da criação de listas constituídas por vários alunos.


## Resultados

```python

# TPC5 : Aplicação para a gestão de alunos 

# aluno = (nome, id, [notaTPC, notaProj, notaTeste])
# turma = [aluno]

def mostraMenu():
    print("""
===== Gestão de Alunos =====
1: Criar uma turma 
2: Inserir um aluno na turma 
3: Listar a turma 
4: Consultar um aluno por id
8: Guardar a turma em ficheiro 
9: Carregar uma turma dum ficheiro 
0: Sair da aplicação 
""")

def criarTurma():
    return[]


def lerNota(texto):
    """Pede uma nota ao utlizador até ele escrever um número entre 0 e 20."""
    nota = -1
    while not (0 <= nota <= 20):
        try:
            nota = float(input(texto))
            if not (0 <= nota <= 20):
                print("A nota tem de ser entre 0 e 20.")
        except ValueError:
            print("Valor inválido. Escreve um número.")
    return nota

def consultarAluno(turma, idAluno):
    """Devolve o aluno com esse id, ou None, se não existir"""
    for aluno in turma:
        if aluno[1] == idAluno:
            return aluno
    return None

def inserirAluno(turma):
    nome = input("Nome: ")
    idAluno = input("ID: ")
    if consultarAluno(turma, idAluno) is not None:
        print("Já existe um aluno com esse ID.")
        return
    notaTPC = lerNota("Nota do TPC: ")
    notaProj = lerNota("Nota do projeto: ")
    notaTeste = lerNota("Nota do teste: ")
    turma.append((nome, idAluno, [notaTPC, notaProj, notaTeste]))
    print("Aluno inserido.")


def listarTurma(turma):
    if len(turma) == 0:
        print("A turma está vazia.")
        return
    for nome, idAluno, notas in turma:
        print(f"{nome} - {idAluno}: TPC={notas[0]}, Projetos={notas[1]}, Teste={notas[2]}")


def consultarPorId(turma):
    idAluno = input("ID a consultar: ")
    aluno = consultarAluno(turma, idAluno)
    if aluno is None:
        print("Aluno não encontrado.")
    else:
        nome, idAluno, notas = aluno 
        print(f"Nome: {nome}")
        print(f"ID: {idAluno}")
        print(f"Notas: TPC={notas[0]}, Projeto={notas[1]}, Teste={notas[2]}")


def guardarTurma(turma):
    nomeFicheiro = input("Nome do ficheiro: ")
    with open(nomeFicheiro, "w") as f:
        for nome, idAluno, notas in turma:
            f.write(f"{nome};{idAluno};{notas[0]};{notas[1]};{notas[2]}\n")
    print(f"{len(turma)} alunos guardados em {nomeFicheiro}.")

def carregarTurma():
    nomeFicheiro = input("Nome do ficheiro: ")
    turma = []
    try:
        f = open(nomeFicheiro)
    except FileNotFoundError:
        print("Ficheiro não encontrado.")
        return None
    for linha in f:
        linha = linha.strip()
        if linha == "":
            continue
        campos = linha.split(";")
        turma.append((campos[0], campos[1],
                      [float(campos[2]), float(campos[3]), float(campos[4])]))

    f.close()
    print(f"{len(turma)} alunos carregados.")
    return turma 

def main():
    turma = criarTurma()
    opcao = -1
    while opcao != 0:
        mostraMenu()
        try:
            opcao = int(input("Opção: "))
        except ValueError:
            print("Opção inválida.")
            opcao = -1
            continue


        if opcao == 1:
            turma = criarTurma()
            print("Turma criada (vazia).")
        elif opcao == 2:
            inserirAluno(turma)
        elif opcao == 3:
            listarTurma(turma)
        elif opcao == 4:
            consultarPorId(turma)
        elif opcao == 8:
            guardarTurma(turma)
        elif opcao == 9:
            nova = carregarTurma()
            if nova is not None:
                turma = nova
        elif opcao == 0:
            print("Até á próxima!")
        else:
            print("Opção inválida.")


main()
