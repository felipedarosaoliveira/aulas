# Uso de Arrays em Java

## Introdução aos Arrays
O que são Arrays?
Arrays são estruturas de dados que armazenam múltiplos valores do mesmo tipo em uma única variável.
Os arrays são utilizados para armazenar coleções de dados de forma ordenada e eficiente.
Cada elemento em um array é identificado por um índice.

## Características dos Arrays
Características principais:
Tipo Fixo: Todos os elementos de um array devem ser do mesmo tipo (por exemplo, int, String, double).
Tamanho Fixo: O tamanho de um array é definido no momento de sua criação e não pode ser alterado.
Índices: O primeiro índice de um array é 0, e o último índice é tamanho - 1.
Contíguo na Memória: Os arrays são armazenados em blocos contíguos de memória.

## Declaração e Criação de Arrays
Sintaxe para declarar e criar um array:
```java
tipo[] nomeDoArray = new tipo[tamanho];
```
Exemplo de Criação de um Array de Inteiros:

```java
int[] numeros = new int[5]; // Cria um array de inteiros com 5 elementos
```
Explicação:
tipo é o tipo de dados que o array irá armazenar.
nomeDoArray é o nome que você dá ao array.
tamanho especifica o número de elementos que o array pode armazenar.

## Inicialização de Arrays
Inicialização durante a criação:
```java

int[] numeros = {1, 2, 3, 4, 5}; // Cria e inicializa o array com valores
```

Inicialização Padrão:

Quando um array é criado usando new, todos os elementos são inicializados para o valor padrão do tipo:
0 para tipos numéricos (int, double, etc.).
false para tipos boolean.
null para tipos de referência (String, objetos, etc.).
Exemplo de Array de Strings:

```java
String[] nomes = new String[3]; // Cria um array de Strings com 3 elementos
nomes[0] = "Alice";
nomes[1] = "Bob";
nomes[2] = "Carol";
```

## Acessando e Modificando Elementos do Array
Acessar elementos:
```java

int primeiroNumero = numeros[0]; // Acessa o primeiro elemento do array
```

Modificar elementos:
```java
numeros[1] = 10; // Modifica o segundo elemento do array para 10
```
Explicação:
Utiliza-se o índice do elemento entre colchetes [] para acessar ou modificar elementos.


## Exemplo Prático: Populando um Array
```java
import java.util.Scanner;

public class ExemploArray {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int[] numeros = new int[5];

        // Populando o array com entradas do usuário
        for (int i = 0; i < numeros.length; i++) {
            System.out.println("Digite um número:");
            numeros[i] = scanner.nextInt();
        }

        // Exibindo os elementos do array
        System.out.println("Os números digitados foram:");
        for (int numero : numeros) {
            System.out.println(numero);
        }
    }
}
```
Explicação:
Um for loop é usado para iterar sobre os índices do array, preenchendo cada elemento com entrada do usuário.
Um for-each loop é usado para exibir os elementos do array.

## Arrays Multidimensionais
O que são Arrays Multidimensionais?

Arrays que possuem mais de uma dimensão, como uma matriz (linhas e colunas).
Exemplo: Um array bidimensional (int[][]) pode ser visto como uma tabela de valores.
Sintaxe para Criar um Array Bidimensional:

```java
int[][] matriz = new int[3][3]; // Cria uma matriz de 3x3
Inicialização de um Array Bidimensional:
java
Copiar código
int[][] matriz = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};
```
Acessando Elementos de um Array Bidimensional:
```java
int valor = matriz[1][2]; // Acessa o elemento da segunda linha, terceira coluna
```

## Boas Práticas com Arrays
Sempre verificar os limites do array:
Evite acessar índices fora dos limites (IndexOutOfBoundsException).
Inicializar todos os elementos:
Certifique-se de inicializar todos os elementos, especialmente se o array for de objetos.
Use for-each para percorrer arrays quando não for necessário acessar o índice.