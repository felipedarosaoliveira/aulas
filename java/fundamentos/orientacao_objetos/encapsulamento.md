### Aula: Fundamentos da Programação Orientada a Objetos (POO) - Encapsulamento em Java

#### Duração: 30 minutos

---

### Objetivos da aula:
1. Entender o conceito de **encapsulamento** na Programação Orientada a Objetos.
2. Compreender os **níveis de visibilidade** e **modificadores de acesso** em Java.
3. Aprender sobre a **estrutura de pacotes** em Java.
4. Explorar o padrão **JavaBean** e sua nomenclatura.
5. Assimilar os conceitos de forma prática, clara e aplicável no desenvolvimento de software.

---

### 1. O que é Encapsulamento? Conceito Simplificado

**Imagine que você tem uma caixa-forte** onde guarda seus pertences valiosos. Apenas você ou pessoas autorizadas podem abrir essa caixa. Da mesma forma, em Programação Orientada a Objetos, usamos o **encapsulamento** para proteger os dados dos objetos e controlar quem pode acessá-los ou modificá-los.

O **encapsulamento** é um dos pilares fundamentais da POO. Ele consiste em **ocultar os detalhes internos** de um objeto e **expor apenas o que é necessário**. Isso proporciona:
- **Segurança**: Protege os dados internos dos objetos de serem modificados de forma indevida.
- **Organização**: Mantém o código mais legível e fácil de manter.
- **Controle**: Permite que os dados sejam acessados ou modificados apenas por meio de métodos definidos, como `getters` e `setters`.

---

### 2. Níveis de Visibilidade e Encapsulamento em Java

Em Java, o encapsulamento é implementado usando **modificadores de acesso**. Eles definem **quem pode acessar** ou modificar os atributos e métodos de uma classe. Java oferece quatro níveis de visibilidade principais:

#### 2.1 Modificadores de Acesso

1. **`private`**: O mais restritivo. Quando algo é declarado como `private`, ele só pode ser acessado dentro da própria classe.
   
   - **Exemplo**:
   ```java
   public class Carro {
       private String cor;  // Atributo privado, acessível apenas dentro da classe
       
       public String getCor() {
           return cor;  // Getter para acessar o atributo privado
       }
   }
   ```

2. **`default`** (sem modificador): Quando nenhum modificador de acesso é especificado, o acesso é **restrito ao pacote**. Ou seja, a classe e seus membros só são acessíveis dentro do mesmo pacote.

   - **Exemplo**:
   ```java
   class Pessoa {
       String nome;  // Visível apenas no mesmo pacote
   }
   ```

3. **`protected`**: Acesso dentro do mesmo pacote e também para classes que **herdam** a classe. Ele é usado quando desejamos que subclasses possam acessar certos membros da classe.

   - **Exemplo**:
   ```java
   public class Animal {
       protected String especie;  // Visível no pacote e nas subclasses
   }
   ```

4. **`public`**: O mais permissivo. Quando algo é declarado como `public`, ele pode ser acessado de qualquer lugar, seja no mesmo pacote ou em pacotes diferentes.

   - **Exemplo**:
   ```java
   public class Produto {
       public String nome;  // Visível em qualquer lugar
   }
   ```

---

### 3. Estrutura de Pacotes em Java

**Pacotes** em Java são como **pastas** no sistema operacional, usados para organizar as classes e evitar conflitos de nome. Eles permitem agrupar classes relacionadas, facilitando a manutenção e o entendimento do código.

- **Por que usar pacotes?**
  - Para **organizar** melhor as classes e estruturas.
  - Para **controlar o acesso** às classes e membros.
  - Para evitar **conflitos de nomes** (evitar que classes com o mesmo nome entrem em conflito).

- **Como definir um pacote em Java?**
  - A declaração do pacote deve ser a primeira linha do arquivo de código.
  
  - **Exemplo**:
  ```java
  package com.minhaempresa.produto;

  public class Produto {
      private String nome;
  }
  ```

Neste exemplo, a classe `Produto` pertence ao pacote `com.minhaempresa.produto`, o que ajuda a organizar o código.

#### Níveis de Acesso e Pacotes

O encapsulamento é diretamente afetado pelo uso de pacotes. Dependendo do **modificador de acesso** utilizado, as classes e membros de um pacote podem ou não ser acessíveis em outros pacotes.

---

### 4. O Padrão JavaBean

O **JavaBean** é uma convenção amplamente utilizada para criar classes que seguem boas práticas de encapsulamento e organização. O JavaBean é comumente usado em frameworks e bibliotecas, e segue uma estrutura específica para seus atributos e métodos.

#### Características principais de um JavaBean:
1. **Atributos privados**: Todos os atributos devem ser declarados como `private`, garantindo o encapsulamento.
2. **Métodos getters e setters**: Para cada atributo privado, devemos definir métodos **get** (para acessar o valor) e **set** (para modificar o valor).
3. **Construtor padrão**: Um JavaBean deve ter um **construtor público** sem parâmetros.

#### Exemplo de um JavaBean:

```java
public class Produto {
    private String nome;
    private double preco;

    // Construtor padrão
    public Produto() {
    }

    // Getter para 'nome'
    public String getNome() {
        return nome;
    }

    // Setter para 'nome'
    public void setNome(String nome) {
        this.nome = nome;
    }

    // Getter para 'preco'
    public double getPreco() {
        return preco;
    }

    // Setter para 'preco'
    public void setPreco(double preco) {
        this.preco = preco;
    }
}
```

Neste exemplo, a classe `Produto` segue as regras de um **JavaBean**:
- Os atributos são **privados**.
- Existem métodos **getters** e **setters** para acessar e modificar os atributos.
- Há um **construtor público sem parâmetros**, essencial em um JavaBean.

#### **Por que usar JavaBeans?**
- Eles garantem o **encapsulamento** total dos dados.
- São compatíveis com frameworks Java, como **JavaServer Faces (JSF)**, **Hibernate**, e **Spring**.
- Facilitam a **manutenção e reutilização** do código.

---

### 5. Práticas de Encapsulamento com Getters e Setters

O uso de **getters** e **setters** é uma prática fundamental para garantir o encapsulamento, pois permite que os atributos de uma classe sejam acessados e modificados **indiretamente**.

- **Getters**: Retornam o valor de um atributo.
- **Setters**: Alteram o valor de um atributo.

#### Exemplo de boas práticas com getters e setters:

```java
public class Carro {
    private String modelo;
    private int ano;

    // Getter para 'modelo'
    public String getModelo() {
        return modelo;
    }

    // Setter para 'modelo'
    public void setModelo(String modelo) {
        this.modelo = modelo;
    }

    // Getter para 'ano'
    public int getAno() {
        return ano;
    }

    // Setter para 'ano'
    public void setAno(int ano) {
        if (ano > 1886) {  // Validação no setter
            this.ano = ano;
        }
    }
}
```

Neste exemplo, além de garantir o encapsulamento, o método `setAno()` realiza uma **validação** antes de alterar o valor do atributo. Isso ajuda a garantir que o valor do ano seja realista, melhorando a integridade dos dados.

---

### 6. Resumo Final: Encapsulamento e Boa Estruturação em Java

O **encapsulamento** é um dos conceitos mais poderosos da Programação Orientada a Objetos, pois **protege os dados** e permite que as classes sejam usadas de maneira segura e controlada. Em Java, o encapsulamento é implementado usando **modificadores de acesso** como `private`, `protected`, e `public`.

Além disso, com o uso adequado de **pacotes**, você pode estruturar melhor suas classes e controlar o acesso a elas. E, ao seguir o padrão **JavaBean**, você cria classes que são facilmente reutilizáveis e compatíveis com frameworks importantes.

Encapsular corretamente seus dados não apenas melhora a segurança do código, mas também facilita a manutenção e a escalabilidade do sistema.