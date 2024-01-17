def adicao_manual(num1, num2):
    resultado = num1
    for _ in range(num2):
        resultado += 1
    return resultado


def subtracao_manual(num1, num2):
    resultado = num1
    for _ in range(num2):
        resultado -= 1
    return resultado


def multiplicacao_manual(num1, num2):
    resultado = 0
    for _ in range(num2):
        resultado = adicao_manual(resultado, num1)
    return resultado


def divisao_manual(num1, num2):
    if num2 == 0:
        return "Divisão por zero não é possível"

    resultado = 0
    while num1 >= num2:
        num1 = subtracao_manual(num1, num2)
        resultado = adicao_manual(resultado, 1)

    return resultado


def eh_par(numero):
    return numero % 2 == 0


def eh_positivo(numero):
    return numero > 0


def eh_impar(numero):
    return numero % 2 != 0


# Função para realizar as operações com base na escolha do usuário
def calcular_operacao(num1, num2, operacao):
    if operacao == '1':
        return adicao_manual(num1, num2)
    elif operacao == '2':
        return subtracao_manual(num1, num2)
    elif operacao == '3':
        return multiplicacao_manual(num1, num2)
    elif operacao == '4':
        return divisao_manual(num1, num2)
    else:
        return "Operação inválida"


# Exemplo de uso
numero1 = int(input("Digite o primeiro número: "))
numero2 = int(input("Digite o segundo número: "))
operacao = input("Escolha a operação:\n1 - Adição\n2 - Subtração\n3 - Multiplicação\n4 - Divisão\n")

resultado = calcular_operacao(numero1, numero2, operacao)

# Verificar paridade, positividade, e negatividade da soma
par = eh_par(resultado)
positivo = eh_positivo(resultado)
impar = eh_impar(resultado)

# Subtrair números positivos e pares da soma
resultado_final = subtracao_manual(resultado, positivo) - (numero1 if eh_par(numero1) else 0) - (
    numero2 if eh_par(numero2) else 0)

# Exibir resultados
print("\nResultados:")
print(f"Resultado da Operação: {resultado}")
print(f"Par: {par}")
print(f"Ímpar: {impar}")
print(f"Resultado Final: {resultado_final}")

