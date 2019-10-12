# RSA-crypto

#variaveis
'''numeros primos pré determinados coloque seus numeros primos '''
numeroP = 17
numeroQ = 41
'''mmultiplicaçao dos primos'''
n = numeroP * numeroQ
'''funcao de totiene de euler'''
phiN = (numeroP - 1) * (numeroQ - 1)
'''numero primo aleatório que seja menor que phin e maior que 1 e que seja primo entre si '''
e = 13
''' chave privada foi encontrada apartir do algoritmo d*e MOD phiN = 1'''
d = 197

#funções
'''func.criptografar'''
def criptografar (frase):
    
    frase = frase.lower()
    criptografado = ''
    index = 0

    while index < len(frase): 
        criptografado += str(((ord(frase[index]) ** e) % n))
        index += 1
    return criptografado 
    
'''func.descriptografar'''
def descriptografar (frase):
    
    descriptografado = ''
    index = 0
    indexFinal = index + 3
    
    while index != len(criptografado):
        indexFinal = index + 3
        descriptografado += (chr(((int(criptografado[index:indexFinal])) ** 197) % n))
        index = indexFinal
    
    return descriptografado 

if __name__ == "__main__":

    #inicio do programa

    opcao = (input('Escolha qual funcao você gostaria de executar :\n Para criptografar digite(0)\n Para descriptografar digite(1):\n'))
    # nesse ponto começa o processo de criptografia
    if opcao == '0':

        frase = input('Digite a frase que será criptografada: ')
        criptografado = (criptografar(frase))
        print(f'A frase {frase} Criptografada é igual a:')
        print(criptografado)

    # nesse ponto começa o processo de descriptografia
    elif opcao == '1':

        criptografado = input('Digite a hash que será descriptografada: ')
        descriptografado = (descriptografar(criptografado))
        print(f'A hash {criptografado} Descriptografada é igual a:')
        print(descriptografado)

    else:
        print('Reinicie o programa e digite uma opção valida')
    
