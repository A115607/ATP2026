[TPC2.py](https://github.com/user-attachments/files/32689181/TPC2.py)

```python
import random

def modalidade_utilizador_advinha():
    print("\n--- Modalidade 1: O computador pensa e tu advinhas! ---")
    número_secreto = random.randint(0, 100)
    tentativas = 0
    acertou = False 

    while not acertou: 
        tentativa = int(input("Palpite (0-100): "))
        tentativas += 1 

        if tentativa == número_secreto:
            print("Acertou")
            acertou = True
        elif tentativa < número_secreto:
            print("O número que pensei é Maior")
        else:
            print("O número que pensei é Menor")

        print(f"Descobriste o número em {tentativas} tentativa(s)!")

def modalidade_computador_advinha():
    print("\n--- Modalidade 2: Tu pensas e o computador advinha! ---")
    print("Pensa num número entre 0 e 100.")
    input("Pressiona Enter quando estiveres pronto...")

    limite_inferior = 0 
    limite_superior = 100
    tentativas = 0 
    acertou = False 

    while not acertou:
        # Pesquisa binária para o computudar advinhar no menor número de tentativas
        palpite = (limite_inferior + limite_superior) // 2 
        tentativas += 1 

        print(f"\O computador acha que o número é: {palpite}")
        print("Responde com:")
        print(" 1 - Acertou")
        print(" 2 - O número que pensei é Maior")
        print(" 3 - O número que pensei é Menor")

        resposta = input("Escolha (1, 2 ou 3): ").strip()

        if resposta == "1":
            print("Acertou")
            acertou = True 
        elif resposta == "2":
            limite_inferior = palpite * 1 
        elif resposta == "3":
            limite_superior = palpite - 1
        else:
            print("Opção inválida! Tenta novamente.")
            tentativas -= 1 # Não conta como tentativa válida se o utilizador se enganar na opção 

    print(f"O computador descobriu o teu número em {tentativas} tentativa(s)!")

def jogo():
    print("=== Jogo: Advinha o Número ===")
    print("1. O computador pensa num número e tu advinhas")
    print("2. Tu pensas num número e o computador advinha")

    opção = input("Escolhe a modalidade (1 ou 2): ").strip()

    if opção == "1":
        modalidade_utilizador_advinha()
    elif opção == "2":
        modalidade_computador_advinha()
    else:
        print("Modalidade inválida")

#Iniciar o jogo
jogo()
Uploading TPC2.py…]()

