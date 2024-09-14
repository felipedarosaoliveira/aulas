### Exercícios Didáticos sobre Herança em Java

#### Objetivo:
Os exercícios a seguir são projetados para fortalecer os conceitos de **herança** e **polimorfismo** em Java. A herança permite que classes compartilhem atributos e métodos, melhorando a reutilização de código e a organização do sistema. Um dos exercícios abordará o uso de **classes abstratas**.

---

### Exercício 1: Herança Simples - Classe `Animal`

#### Descrição:
Implemente uma hierarquia de classes onde a classe **`Animal`** é a classe base, e as classes **`Cachorro`** e **`Gato`** herdam de `Animal`. Cada animal deve ter um comportamento próprio ao emitir som.

#### Requisitos:
1. Crie a classe `Animal` com o método `emitirSom()`, que será sobrescrito nas subclasses.
2. Crie as classes `Cachorro` e `Gato` que herdam de `Animal` e implementam suas próprias versões do método `emitirSom()`.
3. No método `main()`, crie objetos de `Cachorro` e `Gato` e chame o método `emitirSom()`.

#### Exemplo:
```java
public class Animal {
    public void emitirSom() {
        System.out.println("Animal fazendo som");
    }
}

public class Cachorro extends Animal {
    @Override
    public void emitirSom() {
        System.out.println("Cachorro latindo");
    }
}

public class Gato extends Animal {
    @Override
    public void emitirSom() {
        System.out.println("Gato miando");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal cachorro = new Cachorro();
        Animal gato = new Gato();

        cachorro.emitirSom();  // Cachorro latindo
        gato.emitirSom();      // Gato miando
    }
}
```

---

### Exercício 2: Herança e Polimorfismo - Classe `Veiculo`

#### Descrição:
Crie uma hierarquia de classes onde `Veiculo` é a classe base, e as classes **`Carro`** e **`Moto`** herdam de `Veiculo`. Implemente o método `mover()` de maneira polimórfica para cada tipo de veículo.

#### Requisitos:
1. Crie a classe `Veiculo` com o método `mover()`, que será sobrescrito nas subclasses.
2. As classes `Carro` e `Moto` devem sobrescrever o método `mover()` para indicar como cada veículo se move.
3. No método `main()`, crie uma lista de `Veiculo` contendo `Carro` e `Moto`, e chame `mover()` polimorficamente.

#### Exemplo:
```java
import java.util.ArrayList;
import java.util.List;

public class Veiculo {
    public void mover() {
        System.out.println("Veículo se movendo");
    }
}

public class Carro extends Veiculo {
    @Override
    public void mover() {
        System.out.println("Carro acelerando");
    }
}

public class Moto extends Veiculo {
    @Override
    public void mover() {
        System.out.println("Moto acelerando");
    }
}

public class Main {
    public static void main(String[] args) {
        List<Veiculo> veiculos = new ArrayList<>();
        veiculos.add(new Carro());
        veiculos.add(new Moto());

        for (Veiculo v : veiculos) {
            v.mover();
        }
    }
}
```

---

### Exercício 3: Herança com Super - Classe `Pessoa`

#### Descrição:
Crie uma hierarquia de classes onde `Pessoa` é a classe base, e as classes **`Aluno`** e **`Professor`** herdam de `Pessoa`. Utilize o construtor da classe base para inicializar os atributos comuns.

#### Requisitos:
1. Crie a classe `Pessoa` com os atributos `nome` e `idade`, e um construtor que inicializa esses atributos.
2. As classes `Aluno` e `Professor` devem herdar de `Pessoa` e usar o construtor da superclasse (`super()`).
3. No método `main()`, crie objetos de `Aluno` e `Professor` e exiba suas informações.

#### Exemplo:
```java
public class Pessoa {
    protected String nome;
    protected int idade;

    public Pessoa(String nome, int idade) {
        this.nome = nome;
        this.idade = idade;
    }

    public void exibirInformacoes() {
        System.out.println("Nome: " + nome + ", Idade: " + idade);
    }
}

public class Aluno extends Pessoa {
    public Aluno(String nome, int idade) {
        super(nome, idade);
    }

    @Override
    public void exibirInformacoes() {
        System.out.println("Aluno - " + "Nome: " + nome + ", Idade: " + idade);
    }
}

public class Professor extends Pessoa {
    public Professor(String nome, int idade) {
        super(nome, idade);
    }

    @Override
    public void exibirInformacoes() {
        System.out.println("Professor - " + "Nome: " + nome + ", Idade: " + idade);
    }
}

public class Main {
    public static void main(String[] args) {
        Pessoa aluno = new Aluno("João", 20);
        Pessoa professor = new Professor("Carlos", 45);

        aluno.exibirInformacoes();     // Aluno - Nome: João, Idade: 20
        professor.exibirInformacoes(); // Professor - Nome: Carlos, Idade: 45
    }
}
```

---

### Exercício 4: Herança com Classes Abstratas - Classe `Forma`

#### Descrição:
Implemente uma classe abstrata chamada **`Forma`** que define o método abstrato `calcularArea()`. Crie classes concretas **`Circulo`** e **`Retangulo`** que herdam de `Forma` e implementam o cálculo da área de acordo com suas fórmulas específicas.

#### Requisitos:
1. Crie a classe abstrata `Forma` com o método abstrato `calcularArea()`.
2. A classe `Circulo` deve implementar `calcularArea()` para calcular a área de um círculo.
3. A classe `Retangulo` deve implementar `calcularArea()` para calcular a área de um retângulo.
4. No método `main()`, crie objetos de `Circulo` e `Retangulo` e exiba suas áreas.

#### Exemplo:
```java
public abstract class Forma {
    public abstract double calcularArea();
}

public class Circulo extends Forma {
    private double raio;

    public Circulo(double raio) {
        this.raio = raio;
    }

    @Override
    public double calcularArea() {
        return Math.PI * raio * raio;
    }
}

public class Retangulo extends Forma {
    private double largura;
    private double altura;

    public Retangulo(double largura, double altura) {
        this.largura = largura;
        this.altura = altura;
    }

    @Override
    public double calcularArea() {
        return largura * altura;
    }
}

public class Main {
    public static void main(String[] args) {
        Forma circulo = new Circulo(5);
        Forma retangulo = new Retangulo(4, 6);

        System.out.println("Área do Círculo: " + circulo.calcularArea());    // 78.5398...
        System.out.println("Área do Retângulo: " + retangulo.calcularArea()); // 24.0
    }
}
```

---

### Exercício 5: Herança e Sobrescrita de Métodos - Classe `ContaBancaria`

#### Descrição:
Implemente uma hierarquia de classes onde `ContaBancaria` é a classe base, e as classes **`ContaCorrente`** e **`ContaPoupanca`** herdam de `ContaBancaria`. Cada conta deve calcular o saldo de maneira diferente.

#### Requisitos:
1. Crie a classe `ContaBancaria` com o método `calcularSaldo()`, que será sobrescrito nas subclasses.
2. A classe `ContaCorrente` deve ter uma taxa de manutenção mensal que deve ser subtraída do saldo.
3. A classe `ContaPoupanca` deve ter um rendimento mensal que deve ser adicionado ao saldo.
4. No método `main()`, crie objetos de `ContaCorrente` e `ContaPoupanca`, e calcule o saldo para ambos.

#### Exemplo:
```java
public class ContaBancaria {
    protected double saldo;

    public ContaBancaria(double saldoInicial) {
        this.saldo = saldoInicial;
    }

    public void calcularSaldo() {
        System.out.println("Saldo da conta: " + saldo);
    }
}

public class ContaCorrente extends ContaBancaria {
    private double taxaManutencao;

    public ContaCorrente(double saldoInicial, double taxaManutencao) {
        super(saldoInicial);
        this.taxaManutencao = taxaManutencao;
    }

    @Override
    public void calcularSaldo() {
        saldo -= taxaManutencao;
        System.out.println("Saldo da Conta Corrente após taxa de manutenção: " + saldo);
    }
}

public class ContaPoupanca extends ContaBancaria {
    private double rendimentoMensal;

    public ContaPoupanca(double saldoInicial, double rendimentoMensal) {
        super(saldoInicial);
        this.rendimentoMensal = rendimentoMens