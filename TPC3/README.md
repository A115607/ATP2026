# TPC3: Corrida para o 100

## Autor

- Mariana Santiago Machado Moreiras
- A115607
- <img width="4032" height="3024" alt="IMG_4705" src="https://github.com/user-attachments/assets/5bc6db05-79e1-47a9-bd8c-2b3798d23b8c" />

## Resumo 

Desenvolvimento do jogo corrida para o 100, onde começando no zero, o jogador e computador alternam somando um número de 1 a 10 ao total, e quem chegar ao 100 primeiro ganha. 
O jogo apresenta duas modalidades: o computador joga primeiro (ganha), ou o jogador joga primeiro ( computador poderá ganhar ou não ).

## Resultados 

```python

numeros_chave = [1, 12, 23, 34, 45, 56, 67, 78, 89, 100]
jogadas_validas = ["1", "2", "3", "4", "5", "6", "7", "8", "9", "10"]

total = 0 

print("=== JOGO DOS 100 ===")

quem_comeca = input("Quem joga primeiro? (1 = Computador, 2 = Tu): ").strip()
while quem_comeca not in ["1", "2"]:
    print("Opção inválida! Digite 1 ou 2.")

turno = "computador" if quem_comeca == "1" else "humano"

while total < 100:
    print(f"\n--- TOTAL ATUAL: {total} ---")

    if turno == "computador":
        jogada = 1 
        for alvo in numeros_chave:
            diferenca = alvo - total
            if 1 <= diferenca <= 10:
                jogada = diferenca
                break

        total = total + jogada
        print(f"O computador jogou: {jogada}")

        if total == 100:
            print("\nFim de jogo! O Computador venceu!")
            break

        turno = "humano"

    else: 
        entrada = input("Escolhe um número de 1 a 10: ").strip()
        while entrada not in jogadas_validas or (total + int(entrada)) > 100:
            print("Jogada inválida ou ultrapassa 100! Tente novamente. ")
            entrada = input("Escolhe um número de 1 a 10: ").strip()

        jogada = int(entrada)
        total = total + jogada
        print(f"Tu jogas: {jogada}")

        if total == 100:
            print("\nParabéns! Tu venceste o computador!")
            break

        turno = "computador"


