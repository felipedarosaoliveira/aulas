
# Aula: Fundamentos da Programação Orientada a Objetos (POO) - Conceito de Classe em Java


---

### Objetivos da aula:
1. Entender o que é uma classe na Programação Orientada a Objetos (POO).
2. Aprender a definir uma classe em Java.
3. Compreender como mapear propriedades em atributos e ações em métodos.
4. Conhecer as boas práticas de estruturação e nomeação de classes.

---

### 1. O que é uma Classe?

Na Programação Orientada a Objetos, a **classe** é o conceito mais importante. **Classe** é um modelo ou **plano** a partir do qual os objetos são criados. Ela define as **propriedades** e **ações** que os objetos de uma classe terão. Imagine a classe como um molde que descreve como os objetos serão estruturados e o que eles poderão fazer.

Em termos simples:
- Uma **classe** define **como os objetos serão** (quais características terão) e **o que eles poderão fazer** (quais comportamentos terão).
- Os **objetos** são instâncias dessa classe.

### Exemplo para facilitar a compreensão:
Imagine uma **classe chamada "Carro"**. Essa classe define:
- Quais são as **propriedades** que todos os carros têm (por exemplo, cor, modelo, ano).
- Quais são as **ações** que todos os carros podem executar (por exemplo, acelerar, frear).

---

### 2. Definição de Classe em Java

Em Java, para definir uma classe, utilizamos a palavra-chave `class`, seguida pelo nome da classe. Dentro da classe, definimos as **propriedades** (que em Java chamamos de **atributos**) e as **ações** (chamadas de **métodos**).

#### Exemplo de definição de uma classe em Java:

```java
public class Carro {
    // Propriedades (Atributos)
    String cor;
    String modelo;
    int ano;

    // Ações (Métodos)
    void acelerar() {
        System.out.println("O carro está acelerando.");
    }

    void frear() {
        System.out.println("O carro está freando.");
    }
}
```

Neste exemplo, `Carro` é uma **classe**. Ela possui **três atributos** (`cor`, `modelo` e `ano`) e **dois métodos** (`acelerar()` e `frear()`), que representam as ações que um carro pode realizar.

---

### 3. Mapeamento de Propriedades e Ações

Para que a classe possa ser usada de forma prática, precisamos fazer o **mapeamento das propriedades** do objeto para **atributos** e das **ações** para **métodos**.

#### 3.1 Mapeando Propriedades para Atributos

As **propriedades** de um objeto são mapeadas como **variáveis de instância**, ou seja, atributos. Elas representam os dados que descrevem o objeto.

No exemplo da classe `Carro`:
- As propriedades `cor`, `modelo` e `ano` são mapeadas como atributos do tipo `String` e `int`. Cada objeto da classe `Carro` terá seus próprios valores para esses atributos.

```java
String cor;
String modelo;
int ano;
```

Quando criamos um novo objeto `Carro`, podemos definir diferentes valores para esses atributos:

```java
Carro meuCarro = new Carro();
meuCarro.cor = "Vermelho";
meuCarro.modelo = "Sedan";
meuCarro.ano = 2022;
```

Agora, o objeto `meuCarro` tem as propriedades `cor`, `modelo`, e `ano` preenchidas com valores específicos.

#### 3.2 Mapeando Ações para Métodos

As **ações** de um objeto são mapeadas como **métodos**. Um método é um bloco de código que define um comportamento que o objeto pode realizar.

No exemplo da classe `Carro`:
- O método `acelerar()` define a ação de acelerar o carro.
- O método `frear()` define a ação de frear o carro.

Esses métodos podem ser chamados diretamente no objeto `meuCarro` para executar as ações:

```java
meuCarro.acelerar();  // O carro está acelerando.
meuCarro.frear();     // O carro está freando.
```

---

### 4. Estruturação de uma Classe em Java

Em Java, uma classe é composta pelas seguintes partes:
1. **Declaração da classe**: Definida pela palavra-chave `class`, seguida pelo nome da classe.
2. **Atributos (variáveis de instância)**: Representam as propriedades do objeto.
3. **Métodos**: Representam as ações que o objeto pode realizar.
4. **Construtores** (opcional): São usados para inicializar os objetos.

#### Exemplo de estruturação de uma classe com um construtor:

```java
public class Carro {
    String cor;
    String modelo;
    int ano;

    // Construtor: usado para inicializar os atributos ao criar o objeto
    public Carro(String cor, String modelo, int ano) {
        this.cor = cor;
        this.modelo = modelo;
        this.ano = ano;
    }

    // Métodos
    void acelerar() {
        System.out.println("O carro está acelerando.");
    }

    void frear() {
        System.out.println("O carro está freando.");
    }
}
```

Agora, quando criamos um novo carro, podemos passar os valores diretamente para o construtor:

```java
Carro meuCarro = new Carro("Azul", "SUV", 2023);
```

---

### 5. Boas Práticas na Estruturação e Nomeação de Classes

Para que seu código seja claro, legível e mantenha um padrão consistente, é importante seguir algumas **boas práticas de programação** na estruturação e nomeação de classes.

#### 5.1 Nomeação de Classes
- **Nomes Significativos**: Escolha nomes de classes que representem claramente o que o objeto é. Por exemplo, `Carro`, `Pessoa`, `Produto`. Evite nomes genéricos como `Coisa` ou `Objeto`.
- **Notação PascalCase**: Em Java, os nomes de classes devem começar com uma letra maiúscula e seguir a convenção PascalCase, onde cada palavra começa com uma letra maiúscula. Exemplo: `ContaBancaria`, `ClientePremium`.

#### 5.2 Nomeação de Atributos e Métodos
- **Atributos**: Devem ser nomeados em **camelCase**, começando com letra minúscula e usando maiúsculas para separar palavras. Exemplo: `nomeDoProduto`, `dataDeFabricacao`.
- **Métodos**: Também devem seguir o padrão camelCase. O nome do método deve indicar a ação que ele realiza. Exemplo: `calcularDesconto()`, `verificarDisponibilidade()`.

#### 5.3 Visibilidade e Encapsulamento
- **Modificadores de acesso**: Use modificadores de acesso como `private`, `public` e `protected` para controlar o acesso aos atributos e métodos. Uma boa prática é deixar os atributos como `private` e expor métodos `getters` e `setters` públicos para acessar e modificar os atributos.

Exemplo de encapsulamento:
```java
public class Carro {
    private String cor;
    private String modelo;
    private int ano;

    // Getter e Setter para a cor
    public String getCor() {
        return cor;
    }

    public void setCor(String cor) {
        this.cor = cor;
    }
}
```

Neste exemplo, o atributo `cor` é **privado** e só pode ser acessado ou modificado usando os métodos públicos `getCor()` e `setCor()`.

---

### 6. Resumo Final

A **classe** é o pilar fundamental da Programação Orientada a Objetos. Ela é a **estrutura** que define as propriedades e comportamentos dos objetos que serão criados a partir dela. Em Java, uma classe contém **atributos**, que mapeiam as propriedades dos objetos, e **métodos**, que mapeiam suas ações. 

Compreender como definir e estruturar classes corretamente é essencial para criar um código bem organizado e de fácil manutenção. Além disso, seguir boas práticas de nomeação e encapsulamento ajuda a garantir que o código seja claro e seguro.
