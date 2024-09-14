### Aula: Fundamentos da Programação Orientada a Objetos (POO) - Conceitos SOLID em Java

#### Duração: 30 minutos

---

### Objetivos da aula:
1. Compreender os princípios do **SOLID** na Programação Orientada a Objetos (POO).
2. Entender cada um dos cinco princípios e como aplicá-los em Java.
3. Aprender a importância do SOLID para a **manutenibilidade**, **escalabilidade** e **flexibilidade** do código.
4. Apresentar exemplos práticos e fáceis de assimilar para fixação do conteúdo.

---

### Introdução: O que é SOLID?

**SOLID** é um conjunto de **cinco princípios** fundamentais que ajudam a orientar o desenvolvimento de sistemas orientados a objetos de forma limpa e organizada. Esses princípios foram introduzidos por Robert C. Martin (também conhecido como Uncle Bob) e têm como objetivo tornar o código **mais fácil de manter**, **reutilizar** e **testar**.

### Significado de SOLID:
- **S**: **Single Responsibility Principle** (Princípio da Responsabilidade Única)
- **O**: **Open/Closed Principle** (Princípio Aberto/Fechado)
- **L**: **Liskov Substitution Principle** (Princípio da Substituição de Liskov)
- **I**: **Interface Segregation Principle** (Princípio da Segregação de Interface)
- **D**: **Dependency Inversion Principle** (Princípio da Inversão de Dependência)

Vamos explorar cada um desses princípios.

---

### 1. S - **Single Responsibility Principle** (Princípio da Responsabilidade Única)

#### Conceito:
Uma classe deve ter **apenas uma responsabilidade**. Isso significa que ela deve ter **um único motivo** para ser alterada. Se uma classe estiver lidando com mais de uma responsabilidade, ela se tornará difícil de manter e modificar.

#### Exemplo:
Imagine uma classe que manipula tanto a lógica de um **usuário** quanto a **persistência de dados** no banco de dados. Isso quebra o princípio da responsabilidade única porque a classe tem duas responsabilidades distintas.

#### Código Incorreto:
```java
public class UsuarioService {
    public void salvarUsuario(Usuario usuario) {
        // Lógica de validação
        // Lógica de persistência
    }
}
```

#### Código Correto:
Separando responsabilidades:
```java
public class UsuarioService {
    private UsuarioRepository usuarioRepository;

    public UsuarioService(UsuarioRepository usuarioRepository) {
        this.usuarioRepository = usuarioRepository;
    }

    public void salvarUsuario(Usuario usuario) {
        validarUsuario(usuario);
        usuarioRepository.salvar(usuario);  // A responsabilidade de persistência é delegada
    }

    private void validarUsuario(Usuario usuario) {
        // Lógica de validação
    }
}
```

#### Benefícios:
- **Fácil de modificar**: Alterações em uma responsabilidade não afetam outras.
- **Maior reutilização**: Funções específicas podem ser reaproveitadas em outros contextos.

---

### 2. O - **Open/Closed Principle** (Princípio Aberto/Fechado)

#### Conceito:
As classes devem estar **abertas para extensão**, mas **fechadas para modificação**. Isso significa que você deve ser capaz de adicionar novos comportamentos sem modificar o código existente.

#### Exemplo:
Imagine que você tem uma classe que calcula descontos. Se você precisar adicionar um novo tipo de desconto, não deve modificar a lógica interna da classe original.

#### Código Incorreto:
```java
public class CalculadoraDeDescontos {
    public double calcularDesconto(String tipoDesconto, double valor) {
        if (tipoDesconto.equals("Natal")) {
            return valor * 0.9;
        } else if (tipoDesconto.equals("BlackFriday")) {
            return valor * 0.7;
        }
        return valor;
    }
}
```

#### Código Correto:
Aqui, criamos uma interface de descontos e adicionamos novos tipos sem modificar a classe original.

```java
public interface Desconto {
    double aplicarDesconto(double valor);
}

public class DescontoNatal implements Desconto {
    @Override
    public double aplicarDesconto(double valor) {
        return valor * 0.9;
    }
}

public class DescontoBlackFriday implements Desconto {
    @Override
    public double aplicarDesconto(double valor) {
        return valor * 0.7;
    }
}

public class CalculadoraDeDescontos {
    public double calcular(Desconto desconto, double valor) {
        return desconto.aplicarDesconto(valor);
    }
}
```

#### Benefícios:
- **Facilidade de adicionar novos comportamentos** sem tocar no código existente.
- **Código mais flexível e expansível**.

---

### 3. L - **Liskov Substitution Principle** (Princípio da Substituição de Liskov)

#### Conceito:
Objetos de uma classe derivada devem ser **substituíveis** por objetos da classe base sem alterar o comportamento correto do programa. Em outras palavras, uma subclasse deve ser capaz de substituir sua superclasse sem que o código que usa essa superclasse precise ser alterado.

#### Exemplo:
Suponha que temos uma classe `Retangulo` e uma classe `Quadrado` que herda de `Retangulo`.

#### Código Incorreto:
```java
public class Retangulo {
    protected int largura;
    protected int altura;

    public void setLargura(int largura) {
        this.largura = largura;
    }

    public void setAltura(int altura) {
        this.altura = altura;
    }

    public int getArea() {
        return largura * altura;
    }
}

public class Quadrado extends Retangulo {
    @Override
    public void setLargura(int largura) {
        this.largura = largura;
        this.altura = largura;  // Viola o comportamento da superclasse
    }
}
```
Esse código quebra o princípio porque a substituição de `Quadrado` em lugar de `Retangulo` não funciona corretamente.

#### Código Correto:
Melhor modelar `Quadrado` e `Retangulo` sem usar herança inadequada:

```java
public interface Forma {
    int getArea();
}

public class Retangulo implements Forma {
    protected int largura;
    protected int altura;

    public Retangulo(int largura, int altura) {
        this.largura = largura;
        this.altura = altura;
    }

    @Override
    public int getArea() {
        return largura * altura;
    }
}

public class Quadrado implements Forma {
    private int lado;

    public Quadrado(int lado) {
        this.lado = lado;
    }

    @Override
    public int getArea() {
        return lado * lado;
    }
}
```

#### Benefícios:
- **Substituição adequada** sem comportamento inesperado.
- **Melhor design de herança**.

---

### 4. I - **Interface Segregation Principle** (Princípio da Segregação de Interface)

#### Conceito:
Os clientes não devem ser forçados a depender de interfaces que não utilizam. É melhor ter várias interfaces pequenas e específicas do que uma única interface grande e genérica.

#### Exemplo:
Imagine que temos uma interface `Trabalhador` que tem muitas funções, e nem todas as classes precisam implementá-las.

#### Código Incorreto:
```java
public interface Trabalhador {
    void trabalhar();
    void dirigir();
}

public class Engenheiro implements Trabalhador {
    @Override
    public void trabalhar() {
        // Engenheiro trabalhando
    }

    @Override
    public void dirigir() {
        // Engenheiro não dirige
    }
}
```

#### Código Correto:
Segregamos as interfaces para que cada classe implemente apenas o que realmente utiliza.

```java
public interface Trabalhador {
    void trabalhar();
}

public interface Motorista {
    void dirigir();
}

public class Engenheiro implements Trabalhador {
    @Override
    public void trabalhar() {
        // Engenheiro trabalhando
    }
}

public class Taxista implements Trabalhador, Motorista {
    @Override
    public void trabalhar() {
        // Taxista trabalhando
    }

    @Override
    public void dirigir() {
        // Taxista dirigindo
    }
}
```

#### Benefícios:
- **Interfaces específicas** e focadas em comportamentos reais.
- **Evita código desnecessário** em classes que não precisam de todos os métodos.

---

### 5. D - **Dependency Inversion Principle** (Princípio da Inversão de Dependência)

#### Conceito:
Dependa de **abstrações** e não de implementações concretas. Em vez de depender diretamente de classes específicas, dependa de interfaces ou classes abstratas para tornar o código mais flexível e testável.

#### Exemplo:
Suponha que temos uma classe `PedidoService` que depende diretamente de uma implementação de repositório.

#### Código Incorreto:
```java
public class PedidoService {
    private PedidoRepository pedidoRepository = new PedidoRepository();

    public void salvarPedido(Pedido pedido) {
        pedidoRepository.salvar(pedido);
    }
}
```

#### Código Correto:
Introduzimos uma abstração (interface) para desacoplar a dependência da implementação concreta.

```java
public class PedidoService {
    private Repository<Pedido> repository;

    public PedidoService(Repository<Pedido> repository) {
        this.repository = repository;
    }

    public void salvarPedido(Pedido pedido) {
        repository.salvar(pedido);
    }
}

public interface Repository<T> {
    void salvar(T t);
}


