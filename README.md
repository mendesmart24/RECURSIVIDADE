# RECURSIVIDADE
RELATÓRIO DO TRABALHO –DISCIPLINA FUNADAMENTOS MATEMATICOS
Introdução
A recursão é uma das técnicas mais elegantes e poderosas da programação. Ela permite que uma função chame a si mesma para resolver problemas complexos de maneira gradual, dividindo uma tarefa maior em partes menores e mais simples. Cada função recursiva possui dois elementos fundamentais: o caso base, que interrompe as chamadas, e o passo recursivo, que reduz o problema até chegar ao caso base. Neste trabalho, serão apresentadas três implementações clássicas: o cálculo fatorial, a busca binária e o problema das Torres de Hanói. Além do código em Python, o relatório explica a lógica de cada algoritmo e mostra exemplos práticos que facilitam sua compreensão.
1. Cálculo Fatorial Recursivo
O fatorial de um número é o resultado da multiplicação de todos os inteiros positivos menores ou iguais a ele. Matematicamente, é definido como 0! = 1 e n! = n × (n−1)! para n ≥ 1. A função recursiva segue exatamente essa definição.
Exemplo real: imagine que você quer saber quantas maneiras diferentes há de organizar 4 pessoas em uma fila. Cada pessoa pode ocupar uma posição diferente, então há 24 possibilidades. Isso é o fatorial de 4.
Código em Python
def fatorial(n):
    if n == 0 or n == 1:
        return 1  # Caso base
    return n * fatorial(n - 1)  # Passo recursivo

print(fatorial(4))  # Saída: 24

Caso Base
O caso base ocorre quando n é igual a 0 ou 1. Nessa situação, a função retorna 1 e a recursão é interrompida. Sem o caso base, o programa chamaria a si mesmo indefinidamente, resultando em erro.
Passo Recursivo
O passo recursivo acontece quando a função chama a si mesma com um valor menor, ou seja, fatorial(n - 1). Dessa forma, o problema grande (calcular n!) é reduzido a um problema menor (calcular (n−1)!), até chegar ao caso base.
Rastreio Manual (n = 4)
fatorial(4)
→ 4 × fatorial(3)
  → 3 × fatorial(2)
    → 2 × fatorial(1)
      → fatorial(1) = 1 (caso base)
Resultado final: 4 × 3 × 2 × 1 = 24

2. Busca Binária Recursiva
A busca binária é um algoritmo eficiente usado para encontrar um valor dentro de uma lista ordenada. A ideia é dividir o espaço de busca ao meio a cada chamada, descartando metade dos elementos até localizar o valor ou concluir que ele não está presente.
Exemplo real: imagine uma lista de números ordenados: [2, 4, 6, 8, 10, 12, 14]. Queremos saber se o número 10 está nela.
Código em Python
def busca_binaria(lista, valor, inicio, fim):
    if inicio > fim:
        return -1  # Caso base de falha
    meio = (inicio + fim) // 2
    if lista[meio] == valor:
        return meio  # Caso base de sucesso
    elif valor < lista[meio]:
        return busca_binaria(lista, valor, inicio, meio - 1)  # Passo recursivo (esquerda)
    else:
        return busca_binaria(lista, valor, meio + 1, fim)  # Passo recursivo (direita)

nums = [2, 4, 6, 8, 10, 12, 14]
print(busca_binaria(nums, 10, 0, len(nums)-1))  # Saída: 4

Por que o Array Deve Estar Ordenado
O algoritmo da busca binária depende da lista estar ordenada, pois as decisões sobre procurar à esquerda ou à direita só são válidas se os elementos estiverem em ordem crescente. Caso contrário, a comparação com o elemento do meio não faria sentido.
Caso Recursivo e Casos Base
O caso recursivo ocorre quando o valor ainda não foi encontrado. A função então se chama novamente, reduzindo o tamanho da lista pela metade.
O caso base de sucesso é quando o elemento do meio é igual ao valor procurado.
O caso base de falha é quando o início ultrapassa o fim, indicando que o valor não está presente.
Rastreio Manual (buscando 10)
busca_binaria([2,4,6,8,10,12,14], 10, 0, 6)
→ meio = 3 → lista[3] = 8 → 10 > 8 → busca à direita
→ meio = 5 → lista[5] = 12 → 10 < 12 → busca à esquerda
→ meio = 4 → lista[4] = 10 → encontrado!

3. Torres de Hanói
O problema das Torres de Hanói é um clássico da recursão. Ele consiste em mover uma pilha de discos de um pino de origem para outro de destino, usando um terceiro pino auxiliar, respeitando duas regras: mover um disco por vez e nunca colocar um disco maior sobre um menor.
Exemplo real: imagine três pratos empilhados (1 pequeno, 2 médio e 3 grande). Eles estão na torre A e precisam ser movidos para a torre C, usando a torre B como apoio.
Código em Python
def hanoi(n, origem, destino, auxiliar):
    if n == 1:
        print(f"Mover disco 1 de {origem} para {destino}")  # Caso base
    else:
        hanoi(n-1, origem, auxiliar, destino)  # Passo 1
        print(f"Mover disco {n} de {origem} para {destino}")  # Passo 2
        hanoi(n-1, auxiliar, destino, origem)  # Passo 3

hanoi(3, 'A', 'C', 'B')

Lógica dos Três Passos
1. Mover os n−1 discos superiores de A (origem) para B (auxiliar).
2. Mover o maior disco de A para C (destino).
3. Mover os n−1 discos de B para C, usando A como apoio.
Caso Base
O caso base acontece quando há apenas um disco (n = 1). Nesse caso, basta mover o disco diretamente de A para C. Esse é o ponto onde a recursão começa a se desenrolar.
Rastreio Manual (n = 3)
1. Mover disco 1 de A para C
2. Mover disco 2 de A para B
3. Mover disco 1 de C para B
4. Mover disco 3 de A para C
5. Mover disco 1 de B para A
6. Mover disco 2 de B para C
7. Mover disco 1 de A para C

Conclusão
Os três exercícios mostraram como a recursão pode simplificar problemas que envolvem repetição ou divisão em partes menores. Compreender o caso base e o passo recursivo é essencial para garantir que o algoritmo funcione corretamente e não entre em loop infinito. Por meio de exemplos simples e práticos, como organizar pessoas, procurar um número em uma lista e mover pratos entre pinos, ficou mais fácil visualizar como a recursão trabalha internamente e como ela se torna uma ferramenta poderosa na lógica de programação.
