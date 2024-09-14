### Exercícios Didáticos sobre Definição e Implementação de Interfaces em Java

#### Objetivo:
Os exercícios a seguir têm como objetivo reforçar o conceito de **interfaces** em Java, como defini-las e implementá-las corretamente. Cada exercício foca em um aspecto importante para garantir que você compreenda a **abstração** e o **uso correto de interfaces** na programação orientada a objetos.

---

### Exercício 1: Interface `Imprimivel`

#### Descrição:
Implemente uma interface chamada **`Imprimivel`**, que deve definir o método **`imprimir()`**. Em seguida, implemente essa interface em duas classes: **`Documento`** e **`Imagem`**, que devem exibir diferentes mensagens ao serem impressas.

#### Requisitos:
1. Crie a interface `Imprimivel` com o método `imprimir()`.
2. A classe `Documento` deve implementar `Imprimivel` e imprimir uma mensagem relacionada a um documento.
3. A classe `Imagem` deve implementar `Imprimivel` e imprimir uma mensagem relacionada a uma imagem.
4. No método `main()`, crie objetos de `Documento` e `Imagem` e chame o método `imprimir()` para ambos.

#### Exemplo:
```java
public interface Imprimivel {
    void imprimir();
}

public class Documento implements Imprimivel {
    @Override
    public void imprimir() {
        System.out.println("Imprimindo documento...");
    }
}

public class Imagem implements Imprimivel {
    @Override
    public void imprimir() {
        System.out.println("Imprimindo imagem...");
    }
}

public class Main {
    public static void main(String[] args) {
        Imprimivel doc = new Documento();
        Imprimivel img = new Imagem();
        
        doc.imprimir();  // Imprimindo documento...
        img.imprimir();  // Imprimindo imagem...
    }
}
```

---

### Exercício 2: Interface `Pagavel`

#### Descrição:
Crie uma interface **`Pagavel`**, que deve definir o método **`calcularPagamento()`**. Implemente essa interface em duas classes: **`Funcionario`** e **`Freelancer`**, onde cada uma calcula o pagamento de forma diferente.

#### Requisitos:
1. Crie a interface `Pagavel` com o método `calcularPagamento()`.
2. A classe `Funcionario` deve calcular o pagamento como um **salário fixo**.
3. A classe `Freelancer` deve calcular o pagamento com base no número de **horas trabalhadas** e uma **taxa por hora**.
4. No método `main()`, crie objetos de `Funcionario` e `Freelancer` e exiba o valor do pagamento para ambos.

#### Exemplo:
```java
public interface Pagavel {
    double calcularPagamento();
}

public class Funcionario implements Pagavel {
    private double salario;

    public Funcionario(double salario) {
        this.salario = salario;
    }

    @Override
    public double calcularPagamento() {
        return salario;
    }
}

public class Freelancer implements Pagavel {
    private double horasTrabalhadas;
    private double taxaPorHora;

    public Freelancer(double horasTrabalhadas, double taxaPorHora) {
        this.horasTrabalhadas = horasTrabalhadas;
        this.taxaPorHora = taxaPorHora;
    }

    @Override
    public double calcularPagamento() {
        return horasTrabalhadas * taxaPorHora;
    }
}

public class Main {
    public static void main(String[] args) {
        Pagavel funcionario = new Funcionario(3000);
        Pagavel freelancer = new Freelancer(40, 50);

        System.out.println("Pagamento do Funcionário: " + funcionario.calcularPagamento());
        System.out.println("Pagamento do Freelancer: " + freelancer.calcularPagamento());
    }
}
```

---

### Exercício 3: Interface `Controlavel`

#### Descrição:
Crie uma interface **`Controlavel`** com os métodos **`ligar()`** e **`desligar()`**. Implemente essa interface em duas classes: **`Luz`** e **`Ventilador`**, que devem realizar ações diferentes ao ligar e desligar.

#### Requisitos:
1. Crie a interface `Controlavel` com os métodos `ligar()` e `desligar()`.
2. A classe `Luz` deve imprimir uma mensagem de **luz ligada** e **luz desligada**.
3. A classe `Ventilador` deve imprimir uma mensagem de **ventilador ligado** e **ventilador desligado**.
4. No método `main()`, crie objetos de `Luz` e `Ventilador` e chame os métodos `ligar()` e `desligar()` para ambos.

#### Exemplo:
```java
public interface Controlavel {
    void ligar();
    void desligar();
}

public class Luz implements Controlavel {
    @Override
    public void ligar() {
        System.out.println("Luz ligada.");
    }

    @Override
    public void desligar() {
        System.out.println("Luz desligada.");
    }
}

public class Ventilador implements Controlavel {
    @Override
    public void ligar() {
        System.out.println("Ventilador ligado.");
    }

    @Override
    public void desligar() {
        System.out.println("Ventilador desligado.");
    }
}

public class Main {
    public static void main(String[] args) {
        Controlavel luz = new Luz();
        Controlavel ventilador = new Ventilador();

        luz.ligar();
        luz.desligar();
        
        ventilador.ligar();
        ventilador.desligar();
    }
}
```

---

### Exercício 4: Interface `Movimentavel`

#### Descrição:
Crie uma interface chamada **`Movimentavel`**, que define os métodos **`moverParaCima()`** e **`moverParaBaixo()`**. Implemente essa interface em duas classes: **`Robo`** e **`Carro`**, que devem exibir mensagens diferentes ao mover.

#### Requisitos:
1. Crie a interface `Movimentavel` com os métodos `moverParaCima()` e `moverParaBaixo()`.
2. A classe `Robo` deve implementar a movimentação para cima e para baixo com mensagens específicas para um robô.
3. A classe `Carro` deve implementar a movimentação para cima e para baixo com mensagens específicas para um carro.
4. No método `main()`, crie objetos de `Robo` e `Carro` e teste ambos os métodos.

#### Exemplo:
```java
public interface Movimentavel {
    void moverParaCima();
    void moverParaBaixo();
}

public class Robo implements Movimentavel {
    @Override
    public void moverParaCima() {
        System.out.println("Robô movendo para cima.");
    }

    @Override
    public void moverParaBaixo() {
        System.out.println("Robô movendo para baixo.");
    }
}

public class Carro implements Movimentavel {
    @Override
    public void moverParaCima() {
        System.out.println("Carro subindo.");
    }

    @Override
    public void moverParaBaixo() {
        System.out.println("Carro descendo.");
    }
}

public class Main {
    public static void main(String[] args) {
        Movimentavel robo = new Robo();
        Movimentavel carro = new Carro();

        robo.moverParaCima();
        robo.moverParaBaixo();

        carro.moverParaCima();
        carro.moverParaBaixo();
    }
}
```

---

### Exercício 5: Interface `Conversivel`

#### Descrição:
Crie uma interface **`Conversivel`** que define um método **`converter()`**. Em seguida, implemente essa interface em duas classes: **`Temperatura`** (para converter Celsius para Fahrenheit) e **`Moeda`** (para converter Reais para Dólares).

#### Requisitos:
1. Crie a interface `Conversivel` com o método `converter()`.
2. A classe `Temperatura` deve converter um valor de Celsius para Fahrenheit.
3. A classe `Moeda` deve converter um valor de Reais para Dólares.
4. No método `main()`, crie objetos de `Temperatura` e `Moeda` e realize as conversões.

#### Exemplo:
```java
public interface Conversivel {
    double converter(double valor);
}

public class Temperatura implements Conversivel {
    @Override
    public double converter(double celsius) {
        return (celsius * 9/5) + 32;  // Conversão de Celsius para Fahrenheit
    }
}

public class Moeda implements Conversivel {
    private double taxaCambio;

    public Moeda(double taxaCambio) {
        this.taxaCambio = taxaCambio;
    }

    @Override
    public double converter(double reais) {
        return reais * taxaCambio;  // Conversão de Reais para Dólares
    }
}

public class Main {
    public static void main(String[] args) {
        Conversivel temperatura = new Temperatura();
        Conversivel moeda = new Moeda(0.19);  // Exemplo: 1 Real = 0.19 Dólares

        System.out.println("30°C em Fahrenheit: " + temperatura.converter(30));  // Resultado: 86.0
        System.out.println("100 Reais em Dólares: " + moeda.converter(100));    // Resultado: 19.0
    }
}
```

---

### Conclusão:

Esses exercícios são projetados para reforçar