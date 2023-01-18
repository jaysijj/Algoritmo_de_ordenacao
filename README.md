

<div  align=center >
    
Autor | Jaime Jaysi
------ | :----------------
Github | [github.com/jaysijj](https://github.com/jaysijj)
    
</div>
<div align=center><h1>Ordenação de dados em Python</h1></div>


Ordenação é um dos algoritmos mais  estudados pela ciência da computação. Existem diferentes métodos de ordenação que você pode utilizar no seu código para torná-lo mais eficiênte e efetivo.
Você pode usar métodos de ordenação para solucionar ou auxiliar na resolução dos seguintes problemas:

* Procurar itens de uma lista mais facilmente;
* Selecionar itens de uma lista baseado no relacionamento com o resto dos items;
* Procurar valores duplicados em uma lista, pode ser feito de maneira mais rápida;
* Analizar a frequência de distribuição dos itens em uma lista de maneira mais rápida.

## Quais métodos serão apresentados aqui:
- Sorted;
- Sort;
- Bubble sort;
- Insertion sort;
- Merge sort;


## Método "sorted"

Devido Python ser uma linguagem de programação de alto nível, já existe um método pronta capaz de realizar a ordenação dos dados dentro de uma lista, este método é o "sorted()". Aqui temos um exemplo de como usar o método "sorted()":

```
    >>> sorted([9, 1, 5, 2, 7, 0])
    [0, 1, 2, 5, 7, 9]
```

## Método "sort"


Você também pode usar o método "x.sort()", onde x indica a lista que irá ser ordenada. A diferente entre o "sort()" e o "sorted()" é que no "sorted()" não altera a lista original, já o "sort()" altera a lista original.

```
    >>> lista = [9, 1, 5, 2, 7, 0]
    >>> lista.sort()
    [0, 1, 2, 5, 7, 9]
```

## Algoritmo "Bubble Sort"


"Bubble Sort" é um dos mais integros algoritmos de ordenação. O nome se deve ao método de trabalho do algoritmo, a cada nova etapa, o maior elemento da lista "borbulha" até sua posição correta.

O método consiste em fazer multiplas movimentações dentro de uma lista, comparando elemento um por um, e trocando os elementos adjacentes que estão fora de ordem.

```
    def bubble_sort(array):
        n = len(array)

        for i in range(n):
            # Cria um ponto de ignição que irá permitir que a função termine antecipadamente se não houver mais nada para ordenar.
            already_sorted = True

            # Comece verificando cada item dentro da lista, um por um, comparando com o seu valor adjacente. A cada iteração, a porção do array que você verificar diminui, porque os itens restantes já foram ordenados.
            for j in range(n - i - 1):
                if array[j] > array[j + 1]:
                    # Se o item que você estiver verificando for maior que o seu valor adjacente então troque-os.
                    array[j], array[j + 1] = array[j + 1], array[j]

                    # Se você trocar dois elementos, precisar alterar a variável "already_sorted" como "False".
                    already_sorted = False

            # Se não houveram trocas durante a última iteração, o array já está ordenado e você já pode finalizar.
            if already_sorted:
                break

        return array
```
<div align='center'>
<img src='https://lh5.googleusercontent.com/_oLwPF5ZvaZZ4pGD-HvSUSw6nTwwHjUwcLpNigUvb24-PKNwjMUwXcWYWf2wp4HopzHkh9JVmZd_AFYP4HjSYelidbw4FRo1fHrWV3KxbFM13xlRLALb-y-EbLhEmln11lhwEZPV' alt='bouble na prática' style='width:500px; text-align:center;'/>
<p>Passo a passo do Bouble Sort</p>
</div>

## Algoritmo de Inserção "Insertion Sort"

Assim como o "bubble sort", o algoritmo de inserção é simples de implementar e compreender. Mas diferente do "bubble sort" ele cria uma lista classificando um elemento de cada vez comparando cada item com o resto da lista e inserindo na posição correta. 


```
    def insertion_sort(array):
        # loop do segundo elemento do array até o último elemento
        for i in range(1, len(array)):
            # Esse é o elemento que queremos posicionar no local correto
            key_item = array[i]

            # Inicializar a variável que vamos usar para encontrar a posição correta do elemento de referência pelo "key-item".
            j = i - 1

            # Percorra a lista de itens (a porção esquerda do array) e encontre a posição correta do elemento de referência "key_item". Faça isso apenas se "key_item" é menor que os valores adjacentes.
            while j >= 0 and array[j] > key_item:
                # Desloque o valor uma posição a esquerda e reposicione j para o próximo elemento (da direita para esquerda).
                array[j + 1] = array[j]
                j -= 1

            # Quando você terminar o deslocamento dos elementos, você pode posicionar "key_item" na localização correta.
            array[j + 1] = key_item

        return array
```


<div align='center'>
<img src='https://upload.wikimedia.org/wikipedia/commons/0/0f/Insertion-sort-example-300px.gif' alt='Algoritmo de inserção na prática' style='width:300px; text-align:center;'/>
<p>Algoritmo de inserção na prática</p>
</div>

## Algoritmo de Ordenação por junção "Merge Sort"


"Merge Sort" é um algoritmo de ordenação muito eficiente. É baseado na abordagem de dividir e conquistar, uma poderosa técnica usada para solucionar problemas complexos.
Para entender apropriadamente a abordagem de "dividir e conquistar", você tem que entender primeiro o conceito de recursividade. Recursividade envolve na quebra de um problema gerando subproblemas menores até eles ficarem pequenos o suficiente para serem trabalhados. Na programação, recursividade é usualmente expresso como uma função chamando a sí mesma.

A abordagem de "Dividir e conquistar" tipicamente segue uma mesma estrutura:
1. O valor original inputado é quebrado em várias partes, cada um repreentando um subproblema similar ao original;
2. Cada subproblema é resolvido por recursividade;
3. A solução para todos os problemas são combinadas em uma única solução.

No caso do "Merge Sort", a abordagem de "Dividir e conquistar" divide um conjunto de valores de entrada em duas partes iguais, classifica cada metade de forma recursiva e finaliza mesclando essas duas partes em uma única lista organizada.

Para implementar o "Merge Sort" vamos precisar definir duas funções.

- A Primeira é para divir o array em duas metades iguais:

```
        def merge_sort(array):
            # Se o array de entrada conter menos de dois elementos, então retorna como o resultado da função
            if len(array) < 2:
                return array

            midpoint = len(array) // 2

            # Classifica o array dividindo recursivamente os valores de entrada em duas metades iguais, organizando cada metade e mesclando para chegar em um resultado final.
            return merge(
                left=merge_sort(array[:midpoint]),
                right=merge_sort(array[midpoint:]))
```

- A segunda é para ordenar cada metade de forma recursiva: 

```
        def merge(left, right):
            # Se o primeiro array estiver vazio, não vai precisar ser feito o "merged" e você pode retornar o segundo array como resultado.
            if len(left) == 0:
                return right

            # Se o segundo array estiver vazio, então não precisa ser feito o "merged" e você pode retornar o primeiro array como resultado.
            if len(right) == 0:
                return left

            result = []
            index_left = index_right = 0

            # Agora percorra dentro de ambos os arrays atá que todos os elementos criem um array resultante.
            while len(result) < len(left) + len(right):
                # Os elementos precisam ser classificados para adicioná-los para o array resultante, você precisa decidir se pega o elemento mais próximo do primeiro ou do segundo array.
                if left[index_left] <= right[index_right]:
                    result.append(left[index_left])
                    index_left += 1
                else:
                    result.append(right[index_right])
                    index_right += 1

                # Se você chegar ao final de qualquer array, então você pode adicionar os elementos restantes de outro array ao resultado e interromper o loop.
                if index_right == len(right):
                    result += left[index_left:]
                    break

                if index_left == len(left):
                    result += right[index_right:]
                    break

            return result
```
  
  
<div align='center'>
<img src='https://www.simplilearn.com/ice9/free_resources_article_thumb/mergesort/merge_sort-what-img1.png' alt='Algoritmo de Merge Sort na prática' style='width:500px; text-align:center;'/>
<p>Algoritmo de Merge Sort na prática</p>
</div>
