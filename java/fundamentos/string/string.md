# Classe String em Java

Vamos explorar a classe String em Java, que é amplamente utilizada para representar cadeias de caracteres (textos). A String é uma classe imutável, o que significa que uma vez que um objeto String é criado, ele não pode ser alterado. Para operações como encontrar um caractere específico, verificar o conteúdo ou modificar uma string, podemos utilizar diversos métodos que essa classe oferece.


## O que significa uma classe ser imutável?

Quando dizemos que uma classe é imutável, significa que, uma vez que um objeto dessa classe é criado, o seu conteúdo não pode ser alterado. No caso de String, isso quer dizer que, após criarmos uma String, não podemos modificar diretamente seus caracteres ou mudar seu valor. Qualquer operação que pareça "modificar" uma String na verdade cria uma nova instância de String com o resultado da operação.

## Por que String é imutável?

A imutabilidade da String tem vários benefícios práticos:

1. Segurança: Em muitos sistemas, as Strings são usadas para armazenar informações sensíveis, como senhas e tokens de segurança. Se as Strings fossem mutáveis, seria mais fácil alterar esses dados acidentalmente ou maliciosamente.

2. Compartilhamento de memória: Em Java, o uso de objetos imutáveis permite que o compilador e a JVM façam otimizações, como o interning de strings. Isso significa que se várias variáveis armazenam o mesmo texto, elas podem compartilhar a mesma instância de String, economizando memória.

3. Facilidade no uso em estruturas de dados: Objetos imutáveis são ideais para serem usados em coleções, como chaves em mapas (HashMap), pois garantem que o valor não mudará enquanto estão sendo usadas na estrutura de dados.

## Exemplo prático de imutabilidade
```java
String saudacao = "Olá";
```
Agora, vamos tentar modificar o valor dessa String concatenando outra palavra:

```java
saudacao = saudacao.concat(", Mundo!");
System.out.println(saudacao);  // Saída: "Olá, Mundo!"
```

Aparentemente, parece que modificamos a string original, mas o que realmente aconteceu foi:

O método concat() criou uma nova String com o valor "Olá, Mundo!".
A variável saudacao foi atualizada para referenciar essa nova instância.
A String original "Olá" continua existindo na memória, inalterada, até ser removida pelo garbage collector.

## Vantagens da Imutabilidade

* Thread-safe: Como uma String nunca pode ser alterada após sua criação, ela é automaticamente segura para ser compartilhada entre várias threads sem o risco de interferência ou corrupção de dados.
* Previsibilidade: Como não podemos modificar o conteúdo de uma String, o comportamento das variáveis String é mais previsível, o que torna o código mais fácil de entender e menos propenso a bugs.

Abaixo estão os métodos mais comuns da classe `String` em Java, juntamente com exemplos de uso, explicações e comentários para cada linha de código.

## Métodos da Classe String em Java

### 1. `length()`
Retorna o número de caracteres presentes na string.

```java
String texto = "Java é incrível!";  // Declara uma string com o texto "Java é incrível!"
int tamanho = texto.length();        // Calcula o comprimento da string
System.out.println(tamanho);         // Exibe o comprimento da string (15)
```

### 2. `charAt()`
Retorna o caractere localizado no índice especificado.

```java
String texto = "Java";               // Declara uma string com o texto "Java"
char caractere = texto.charAt(1);     // Pega o caractere no índice 1 (segundo caractere, 'a')
System.out.println(caractere);       // Exibe o caractere 'a'
```

### 3. `contains()`
Verifica se a string contém a sequência especificada.

```java
String texto = "Aprender Java é divertido!";  // Declara uma string com o texto "Aprender Java é divertido!"
boolean contem = texto.contains("Java");      // Verifica se a string contém a palavra "Java"
System.out.println(contem);                   // Exibe `true` porque "Java" está presente
```

### 4. `equals()`
Compara se duas strings são exatamente iguais (sensível a maiúsculas e minúsculas).

```java
String a = "Java";              // Declara uma string com o texto "Java"
String b = "java";              // Declara outra string com o texto "java"
boolean saoIguais = a.equals(b); // Compara as duas strings (diferencia maiúsculas e minúsculas)
System.out.println(saoIguais);   // Exibe `false` porque "Java" e "java" são diferentes
```

### 5. `equalsIgnoreCase()`
Compara duas strings ignorando maiúsculas e minúsculas.

```java
String a = "Java";                   // Declara uma string com o texto "Java"
String b = "java";                   // Declara outra string com o texto "java"
boolean saoIguais = a.equalsIgnoreCase(b);  // Compara as strings ignorando maiúsculas e minúsculas
System.out.println(saoIguais);       // Exibe `true` porque "Java" e "java" são equivalentes ignorando o caso
```

### 6. `indexOf()`
Retorna o índice da primeira ocorrência da string especificada.

```java
String texto = "Programar em Java é ótimo!";  // Declara uma string
int indice = texto.indexOf("Java");           // Encontra o índice de início da palavra "Java"
System.out.println(indice);                   // Exibe 14 (a posição de "Java")
```

### 7. `isEmpty()`
Verifica se a string está vazia (comprimento igual a 0).

```java
String texto = "";                    // Declara uma string vazia
boolean estaVazia = texto.isEmpty();   // Verifica se a string está vazia
System.out.println(estaVazia);         // Exibe `true` porque a string está vazia
```

### 8. `replace()`
Substitui todas as ocorrências de uma sequência por outra.

```java
String texto = "Olá, mundo!";                     // Declara uma string com o texto "Olá, mundo!"
String novoTexto = texto.replace("mundo", "Java"); // Substitui "mundo" por "Java"
System.out.println(novoTexto);                    // Exibe "Olá, Java!"
```

### 9. `replaceAll()`
Substitui todas as ocorrências que correspondem a uma expressão regular.

```java
String texto = "123 Java 456";                    // Declara uma string com dígitos e texto
String novoTexto = texto.replaceAll("\d", "#");  // Substitui todos os dígitos por "#"
System.out.println(novoTexto);                    // Exibe "### Java ###"
```

### 10. `split()`
Divide a string em um array com base em um delimitador.

```java
String texto = "Java,Python,C++";             // Declara uma string com linguagens separadas por vírgula
String[] linguagens = texto.split(",");       // Divide a string nas vírgulas, criando um array
for (String linguagem : linguagens) {         // Itera sobre o array e exibe cada linguagem
    System.out.println(linguagem);            // Exibe cada linguagem separadamente
}
// Saída:
// Java
// Python
// C++
```

### 11. `startsWith()`
Verifica se a string começa com o prefixo especificado.

```java
String texto = "Java é legal";                  // Declara uma string
boolean comecaCom = texto.startsWith("Java");   // Verifica se a string começa com "Java"
System.out.println(comecaCom);                  // Exibe `true` porque a string começa com "Java"
```

### 12. `endsWith()`
Verifica se a string termina com o sufixo especificado.

```java
String texto = "Vamos aprender Java!";           // Declara uma string
boolean terminaCom = texto.endsWith("Java!");    // Verifica se a string termina com "Java!"
System.out.println(terminaCom);                  // Exibe `true` porque a string termina com "Java!"
```

### 13. `substring()`
Retorna uma parte da string, do índice inicial até o índice final (não incluso).

```java
String texto = "Aprender Java é incrível";       // Declara uma string
String parte = texto.substring(9, 13);           // Retorna a substring do índice 9 ao 13 (não incluso)
System.out.println(parte);                       // Exibe "Java"
```

### 14. `toLowerCase()`
Converte todos os caracteres da string para letras minúsculas.

```java
String texto = "JAVA";                          // Declara uma string com letras maiúsculas
String minusculo = texto.toLowerCase();          // Converte a string para minúsculas
System.out.println(minusculo);                   // Exibe "java"
```

### 15. `toUpperCase()`
Converte todos os caracteres da string para letras maiúsculas.

```java
String texto = "java";                          // Declara uma string com letras minúsculas
String maiusculo = texto.toUpperCase();          // Converte a string para maiúsculas
System.out.println(maiusculo);                   // Exibe "JAVA"
```

### 16. `trim()`
Remove os espaços em branco no início e no fim da string.

```java
String texto = "  Java é legal  ";               // Declara uma string com espaços em branco
String semEspacos = texto.trim();                // Remove os espaços no início e no fim
System.out.println(semEspacos);                  // Exibe "Java é legal"
```

### 17. `compareTo()`
Compara duas strings lexicograficamente.

```java
String a = "Java";                              // Declara a string "Java"
String b = "Python";                            // Declara a string "Python"
int resultado = a.compareTo(b);                 // Compara "Java" com "Python" lexicograficamente
System.out.println(resultado);                  // Exibe -6 (porque "Java" vem antes de "Python")
```
