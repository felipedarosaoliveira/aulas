### Aula: Fundamentos da Orientação a Objetos - Tratamento de Exceções em Java



---

### Objetivos da aula:
1. Compreender o conceito de **exceção** em Java e sua diferença em relação a um **erro**.
2. Aprender a usar os blocos **try**, **catch**, **finally**, e as instruções **throw** e **throws** para lançar e tratar exceções.
3. Conhecer as principais classes do sistema de exceções em Java: **Throwable**, **Error**, **Exception**, **RuntimeException**.
4. Entender a diferença entre **exceções checadas** e **não checadas**.

---

### 1. O que é uma Exceção?

Uma **exceção** é um evento inesperado que ocorre durante a execução do programa e interrompe seu fluxo normal. Em Java, exceções são representadas como objetos que descrevem a causa e o local onde o erro ocorreu. Quando uma exceção ocorre, o fluxo normal do programa é interrompido, e a linguagem fornece mecanismos para tratá-la e manter a aplicação funcionando.

#### Diferença entre Exceção e Erro:

- **Exceção**: Um problema que pode ser **previsto e tratado** no código, como uma divisão por zero ou o acesso a uma posição inválida em um array.
- **Erro**: Uma condição **imprevisível e grave**, geralmente fora do controle do programa, como a falta de memória (`OutOfMemoryError`).

#### Exemplo de Exceção:
```java
int a = 10;
int b = 0;
int resultado = a / b;  // Gera uma exceção: ArithmeticException
```

Aqui, o programa tenta dividir por zero, o que gera uma **ArithmeticException** e interrompe o fluxo normal da aplicação.

---

### 2. Estrutura Básica do Tratamento de Exceção: `try`, `catch`, e `finally`

Java oferece uma estrutura robusta para tratar exceções usando os blocos **`try`**, **`catch`**, e **`finally`**.

#### Bloco `try`

O bloco **`try`** contém o código que pode lançar uma exceção. Caso uma exceção ocorra dentro do `try`, a execução é desviada para o bloco `catch`.

#### Bloco `catch`

O bloco **`catch`** captura e trata a exceção. Aqui, especificamos o tipo de exceção que estamos esperando e podemos tomar as medidas apropriadas.

#### Bloco `finally`

O bloco **`finally`** é executado **sempre**, independentemente de uma exceção ter sido lançada ou não. Geralmente, é usado para **liberar recursos**, como fechar arquivos ou conexões de banco de dados.

#### Exemplo:
```java
public class ExemploTratamento {
    public static void main(String[] args) {
        try {
            int a = 10;
            int b = 0;
            int resultado = a / b;  // Gera a exceção ArithmeticException
        } catch (ArithmeticException e) {
            System.out.println("Erro: Divisão por zero.");
        } finally {
            System.out.println("Bloco finally: Sempre executado.");
        }
    }
}
```

#### Explicação:
- **try**: Contém o código que pode gerar a exceção.
- **catch**: Captura a exceção `ArithmeticException` e exibe uma mensagem.
- **finally**: Sempre é executado, independentemente de uma exceção ter ocorrido ou não.

---

### 3. A Hierarquia de Exceções em Java

Todas as exceções em Java derivam da classe base **`Throwable`**, que possui duas subclasses principais: **`Error`** e **`Exception`**.

#### Hierarquia:
1. **`Throwable`** (superclasse de todas as exceções)
   - **`Error`**: Indica erros graves que normalmente o programa não pode tratar, como falta de memória (`OutOfMemoryError`).
   - **`Exception`**: Indica condições que o programa pode tentar tratar.
     - **`RuntimeException`**: Exceções que ocorrem em tempo de execução (não verificadas pelo compilador).
     - Outras subclasses de `Exception`: Exceções verificadas pelo compilador.

#### Exemplo de Exceções:
- **`ArithmeticException`**: Gerada ao tentar dividir por zero.
- **`NullPointerException`**: Gerada ao tentar acessar um objeto que é `null`.
- **`ArrayIndexOutOfBoundsException`**: Gerada ao acessar um índice inválido de um array.

---

### 4. Diferença entre Exceções Checadas e Não Checadas

Java divide suas exceções em dois tipos principais: **checadas** e **não checadas**.

#### Exceções Checadas

- São exceções que o **compilador obriga** a serem tratadas ou declaradas. Se o programador não fizer isso, o código não será compilado.
- São subclasses de **`Exception`**, mas não de **`RuntimeException`**.

#### Exemplo de Exceção Checada:
```java
public void lerArquivo(String nomeArquivo) throws FileNotFoundException {
    FileReader file = new FileReader(nomeArquivo);  // Exceção checada
}
```
Neste exemplo, a exceção **FileNotFoundException** deve ser tratada ou declarada com `throws`, caso contrário, o programa não compilará.

#### Exceções Não Checadas (Runtime Exceptions)

- São exceções que ocorrem em **tempo de execução** e não precisam ser tratadas ou declaradas pelo compilador.
- São subclasses de **`RuntimeException`**.

#### Exemplo de Exceção Não Checada:
```java
int[] numeros = new int[5];
int valor = numeros[10];  // Exceção não checada: ArrayIndexOutOfBoundsException
```
O código acima lança uma exceção em tempo de execução, mas o compilador não exige seu tratamento.

---

### 5. Lançando Exceções com `throw` e `throws`

Java permite que você **lance exceções manualmente** em seu código usando a instrução **`throw`**. Além disso, você pode **declarar exceções** que um método pode lançar utilizando a instrução **`throws`**.

#### Usando `throw`

A palavra-chave **`throw`** é usada para **lançar manualmente** uma exceção em um ponto específico do código.

#### Exemplo de `throw`:
```java
public class ExemploThrow {
    public void sacar(double saldo, double valorSaque) {
        if (valorSaque > saldo) {
            throw new IllegalArgumentException("Saldo insuficiente!");
        }
        saldo -= valorSaque;
    }
}
```
No exemplo acima, estamos lançando uma exceção **`IllegalArgumentException`** se o valor do saque for maior que o saldo disponível.

#### Usando `throws`

A palavra-chave **`throws`** é usada na **assinatura de um método** para indicar que ele pode lançar exceções. O método que chama esse método deve tratar ou propagar essa exceção.

#### Exemplo de `throws`:
```java
public void lerArquivo(String nomeArquivo) throws FileNotFoundException {
    FileReader file = new FileReader(nomeArquivo);  // Pode lançar FileNotFoundException
}
```
Aqui, estamos informando ao compilador que o método `lerArquivo()` pode lançar a exceção `FileNotFoundException`.

---

### 6. Exceções Personalizadas

Podemos criar nossas próprias exceções para lidar com erros específicos da lógica de nosso programa. Para isso, criamos uma classe que herda de **`Exception`** ou **`RuntimeException`**.

#### Exemplo de Exceção Personalizada:
```java
public class SaldoInsuficienteException extends Exception {
    public SaldoInsuficienteException(String mensagem) {
        super(mensagem);
    }
}

public class ContaBancaria {
    private double saldo;

    public ContaBancaria(double saldoInicial) {
        this.saldo = saldoInicial;
    }

    public void sacar(double valor) throws SaldoInsuficienteException {
        if (valor > saldo) {
            throw new SaldoInsuficienteException("Saldo insuficiente para o saque.");
        }
        saldo -= valor;
    }
}
```

Neste exemplo, a exceção **SaldoInsuficienteException** é lançada quando o saldo da conta não é suficiente para realizar um saque.

---

### 7. Boas Práticas no Tratamento de Exceções

- **Capture exceções específicas**: Evite capturar exceções gerais como `Exception`, a menos que realmente necessário. Isso facilita a identificação de erros.
  
- **Use o bloco `finally`** para liberar recursos: Certifique-se de que recursos importantes, como arquivos ou conexões de banco de dados, sejam sempre liberados.
  
- **Não use exceções para controle de fluxo**: Exceções devem ser usadas para lidar com situações excepcionais, e não como um substituto para lógica de controle.

- **Lance exceções personalizadas** quando necessário: Isso ajuda a descrever melhor os erros e facilita o entendimento do que ocorreu no sistema.

---

### 8. Resumo Final

- **Exceções** são eventos que ocorrem durante a execução de um programa e que podem ser tratadas para evitar a interrupção abrupta do código.
- Java fornece os blocos **`try`**, **`catch`**, e **`finally`

