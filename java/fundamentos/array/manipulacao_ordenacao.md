# Manipulação de Arrays

## Exemplo de ordenação de um array numérico utilizando o algorítmo BubbleSort

```java
public class BubbleSortExample {
    public static void main(String[] args) {
        // Inicializa o array com 10 números (5 negativos e 5 positivos)
        int[] numeros = {10, -5, 32, -18, 25, -3, 45, -12, 8, -7};

        // Algoritmo de ordenação Bubble Sort
        for (int i = 0; i < numeros.length - 1; i++) {  // Percorre o array até o penúltimo elemento
            for (int j = 0; j < numeros.length - 1 - i; j++) {  // Percorre os elementos não ordenados
                if (numeros[j] > numeros[j + 1]) {  // Compara dois elementos adjacentes
                    // Troca os valores se o atual for maior que o próximo
                    int temp = numeros[j];  // Armazena o valor atual temporariamente
                    numeros[j] = numeros[j + 1];  // Coloca o menor valor na posição atual
                    numeros[j + 1] = temp;  // Coloca o valor maior na próxima posição
                }
            }
        }

        // Exibe os números ordenados
        System.out.println("Array ordenado:");
        for (int numero : numeros) {  // Loop para exibir cada número do array
            System.out.print(numero + " ");  // Imprime cada número do array
        }
    }
}

```

### Explicação do código:

#### Array inicial:
O array numeros é inicializado diretamente com os valores {10, -5, 32, -18, 25, -3, 45, -12, 8, -7}. Ele contém 5 números negativos e 5 números positivos.

#### Bubble Sort:

O algoritmo de Bubble Sort percorre o array comparando cada elemento com o próximo. Se o valor atual for maior que o próximo, eles trocam de lugar.
Esse processo é repetido até que o array esteja completamente ordenado em ordem crescente.

#### Exibição:

O loop for-each percorre o array e imprime os números ordenados.


### Exemplo de ordenação de um array de String utilizando o algorítmo BubbleSort

```java
public class BubbleSortCidades {
    public static void main(String[] args) {
        // Inicializa o array com 10 nomes de cidades brasileiras
        String[] cidades = {"São Paulo", "Rio de Janeiro", "Salvador", "Fortaleza", "Brasília", 
                            "Curitiba", "Manaus", "Recife", "Porto Alegre", "Belém"};
        
        // Algoritmo de ordenação Bubble Sort para strings
        for (int i = 0; i < cidades.length - 1; i++) {  // Percorre o array até o penúltimo elemento
            for (int j = 0; j < cidades.length - 1 - i; j++) {  // Percorre os elementos não ordenados
                // Compara duas cidades usando compareTo() para ordem lexicográfica (crescente)
                if (cidades[j].compareTo(cidades[j + 1]) > 0) {
                    // Se a cidade na posição j vem depois (alfabeticamente) da cidade j+1, faz a troca
                    String temp = cidades[j];  // Armazena temporariamente a cidade na posição j
                    cidades[j] = cidades[j + 1];  // Coloca a cidade j+1 na posição j
                    cidades[j + 1] = temp;  // Coloca a cidade armazenada temporariamente na posição j+1
                }
            }
        }

        // Exibe os nomes das cidades em ordem alfabética crescente
        System.out.println("Cidades ordenadas:");
        for (String cidade : cidades) {  // Loop para exibir cada cidade do array
            System.out.println(cidade);  // Imprime o nome de cada cidade
        }
    }
}


```

### Explicação do código:

#### Array inicial:

String[] cidades: O array é inicializado com 10 nomes de cidades brasileiras. Esses nomes são fornecidos diretamente no código.

#### Bubble Sort:

* O laço externo (for (int i = 0; i < cidades.length - 1; i++)) percorre o array até o penúltimo elemento. Isso acontece porque, após cada iteração, o maior (ou último) valor da sublista já estará na sua posição final.
* O laço interno (for (int j = 0; j < cidades.length - 1 - i; j++)) faz comparações entre as cidades adjacentes, utilizando o método compareTo() para determinar a ordem alfabética.
* cidades[j].compareTo(cidades[j + 1]) > 0: Essa linha compara duas strings e, se o resultado for maior que 0, significa que a string na posição j vem depois (alfabeticamente) da string na posição j+1. Assim, é feita uma troca de valores.

#### Troca de elementos:

Se for necessário realizar uma troca, um valor temporário (temp) armazena o valor atual, para então os valores serem trocados entre as posições j e j+1.

#### Exibição dos resultados:

Após a ordenação, o array de cidades é exibido com um loop for-each, imprimindo cada cidade em ordem crescente (alfabética).