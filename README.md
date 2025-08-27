import random

def valida_int(pergunta, min, max):
    x = int(input(pergunta))
    while (x < min or x > max):
        x = int(input(pergunta))

    return x

def vencedor(j1, j2):
    global v1, v2, empate
    if j1 == 1: #pedra
        if j2 == 1:
            empate += 1
        elif j2 == 2: #papel
            v2 += 1 
        elif j2 == 3: #tesoura
            v1 += 1
    
    elif j1 == 2:
        if j2 == 1:
            v1 += 1
        elif j2 == 2: #papel
            empate += 1
        elif j2 == 3: #tesoura
            v2 += 1
    elif j1 == 3:
        if j2 == 1:
            v2 += 1
        elif j2 == 2:
            v2 += 1
        elif j2 == 3: #
            empate += 1
    
    resultados =[v1, v2, empate]
    return resultados

#PROGRAMA PRINCIPAL
print('JOKENPO')
print('1 - Pedra')
print('2 - Papel')
print('3 - Tesoura')
print('0 - Sair')

jogadas = []
resultados = []
v1 = 0 
v2 = 0
empate = 0

while True:
    j1 = valida_int('Escolha sua jogada: ', 0, 3)
    if not j1:
        break
    j2 = random.randint(1,3)
    jogadas.append([j1, j2])
    resultados = vencedor(j1, j2)

for jogada in jogadas:
    for dado in jogada:
        print(dado, end=' ')
    print()

print(f'Núnero de vitórias do jogador 1: {resultados[0]}')
print(f'Núnero de vitórias do jogador 1: {resultados[1]}')
print(f'Núnero de empates: {resultados[2]}')
