# TPC4 : Manipulação de listas inteiras 

## Autor

- Mariana Santiago Machado Moreiras
- A115607
- <img width="4032" height="3024" alt="IMG_4705" src="https://github.com/user-attachments/assets/eceffe3c-7c3d-4bde-880a-c361f046e67f" />

## Resumo 

Criação de uma aplicação para a manipulação de listas inteiras em Python 


## Resultados 

## Solução do TPC4

```python 

import random

def mostrar_Menu():
    print("---Menu---")
    print("(1) Criar Lista")
    print("(2) Ler Lista")
    print("(3) Somar Lista")
    print("(4) Média Lista")
    print("(5) Maior Elemento Lista")
    print("(6) Menor Elemento Lista")
    print("(7) Lista ordenada por ordem crescente")
    print("(8) Lista ordenada por ordem decrescente")
    print("(9) Procura um elemento da Lista")
    print("(0) Sair")

def Menu():
    lista = []
    a_executar = True

    while True:
        mostrar_Menu()
        opção = input(" Introduza a opção pretendida: ")
        print(" Introduza a opção pretendida ")

        if opção == "1":
            n = int(input(" Quantos elementos quer que a lista tenha? "))
            lista = [random.randint(1,100) for _ in range(n)]
            print(f" Lista criada com sucesso: {lista} ")


        elif opção == "2":
            lista = []
            n = int(input(" Quantos elementos vai ter a lista? "))
            for i in range(n):
                elem = int(input(f" Introduza o elemento {i+1}: "))
                lista.append(elem)
                print(f" Lista lida com sucesso: {lista} ")


        elif opção == "3":
            if not lista:
                print("A lista está vazia.")
            else:
                print(f"A soma dos elementos é: {sum(lista)}")

            
        elif opção == "4":
            if not lita:
                print("A lista está vazia.")
            else:
                média = sum(lista) / len(lista)
                print(f" A média dos elemetos da lista é: {média}")


        elif opção == "5":
            maior = lista[0]
            for elem in lista:
                if elem > maior:
                    maior = elem
            if not lista:
                print(f" A lista está vazia ")
            else:
                print(f" O maior elemento da lista é: {maior(lista)} ")

        elif opção == "6":
            menor = lista[0]
            for elemento in lista:
                if elemento < menor:
                    menor = elemento
            if not lista:
                print(f" A lista está vazia ")
            else:
                print(f" O menor elemento da lista é: {menor(lista)} ")
        
        
        elif opção == "7":
            if not lista:
                print(f"A lista está vazia.")
            else:
                crescente = True
                i = 0
                while i < len(lista) - 1 and crescente:
                    if lista[i] > lista[i + 1]:
                        crescente = False
                    i += 1
                    if crescente:
                        print("Sim")
                    else:
                        print("Não")


        elif opção == "8":
            if not lista:
                print("A lista está vazia.")
            else:
                decrescente = True
                i = 0 
                while i < len(lista) - 1 and decrescente:
                    if lista[i] < lista [i + 1]:
                        decrescente = False 
                    i += 1
                if decrescente:
                    print("Sim")
                else:
                    print("Não")


        elif opção == "9":
            if not lista:
                print("A lista está vazia.")
            else:
                elem = int(input("Qual o elemento que deseja procurar?"))
                if elem in lista:
                    pos = lista.index(elem)
                    print(f"Posição do elemento: {pos}")
                else:
                    print("-1")


        elif opção == "0":
            print(f"Encerrar a aplicação. A lista guardada é: {lista}")

        else: print("Opção inválida! Escolha um número entre 0 e 9.")





  
                
            
        
        

                





            










 
