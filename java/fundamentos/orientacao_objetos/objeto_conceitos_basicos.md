
# Aula: Fundamentos da Programação Orientada a Objetos (POO) - Definição de Objeto


---

### Objetivos da aula:
1. Introduzir o conceito de objetos na Programação Orientada a Objetos (POO).
2. Compreender a relação entre propriedades (atributos) e ações (métodos).
3. Aprender a mapear propriedades e ações em um processo de modelagem.
4. Aplicar os conceitos de forma prática e objetiva, facilitando a compreensão dos alunos que estão começando.

---

### 1. O que é um Objeto? Uma Abordagem Simples

**Imagine o mundo ao seu redor.** Pense em um carro, uma caneta ou até mesmo em um cachorro. Esses são exemplos de **objetos** no mundo real. Cada um desses objetos tem características próprias e comportamentos que eles podem realizar. Na Programação Orientada a Objetos (POO), seguimos essa mesma ideia para representar objetos dentro do nosso código.

Assim como no mundo real, em POO, um **objeto** é algo que tem:
- **Propriedades**: características que descrevem o objeto.
- **Ações**: comportamentos que o objeto pode executar.

Ao programar, criamos "objetos" para modelar partes do mundo real. Por exemplo, um carro pode ser um objeto no nosso programa, com suas próprias propriedades e ações. Isso torna o desenvolvimento mais intuitivo e fácil de entender.

---

### 2. Propriedades de um Objeto: O que ele tem?

Pense no **seu celular**. Ele tem várias características: cor, marca, modelo, capacidade de armazenamento. Na POO, chamamos essas características de **propriedades**, ou também **atributos**. Propriedades são os **dados** que descrevem o objeto.

#### Exemplo:
Um carro pode ser representado com propriedades como:

```java
public class Carro {
    String cor;
    String modelo;
    int ano;
    int numeroDePortas;
}
```

Aqui, `cor`, `modelo`, `ano`, e `numeroDePortas` são as **propriedades** que descrevem o objeto `Carro`. Cada carro terá valores diferentes para essas propriedades. Assim como no mundo real, um carro pode ser vermelho, enquanto outro pode ser azul.

---

### 3. Ações de um Objeto: O que ele faz?

Agora, **pense no que um carro pode fazer**. Ele pode acelerar, frear e ligar o motor. Na POO, as **ações** são chamadas de **métodos**. Elas definem o que o objeto pode fazer, seus comportamentos.

#### Exemplo:
Vamos definir algumas ações para o nosso `Carro`:

```java
public class Carro {
    void acelerar() {
        System.out.println("O carro está acelerando.");
    }

    void frear() {
        System.out.println("O carro está freando.");
    }

    void ligarMotor() {
        System.out.println("O motor está ligado.");
    }
}
```

Esses métodos representam as **ações** que o objeto `Carro` pode realizar. Assim como você pressiona o acelerador para acelerar um carro, em POO, chamamos o método `acelerar()` para executar essa ação.

---

### 4. Mapeando Propriedades e Ações: Como fazemos isso?

Agora que você já entende que um objeto tem **propriedades** (o que ele **é**) e **ações** (o que ele **faz**), o próximo passo é aprender **como mapear essas propriedades e ações na prática**.

**Quando estamos modelando um sistema**, como, por exemplo, um sistema de gestão de uma biblioteca, precisamos fazer algumas perguntas para identificar esses objetos:

1. **Quais são os objetos principais?**  
   No exemplo da biblioteca, podemos identificar objetos como `Livro`, `Cliente`, `Empréstimo`.

2. **Quais são as propriedades desses objetos?**  
   - O `Livro` tem `título`, `autor`, `ano de publicação`, `número de páginas`, etc.
   - O `Cliente` tem `nome`, `CPF`, `endereço`.

3. **Quais são as ações desses objetos?**  
   - O `Livro` pode ser **emprestado** ou **devolvido**.
   - O `Cliente` pode **realizar um empréstimo** ou **reservar um livro**.

---

### 5. A Técnica de Modelagem: Passo a Passo

Para mapear as **propriedades** e **ações** de um objeto, siga este processo simples, que pode ser aplicado a qualquer sistema:

1. **Identifique os objetos principais**: Olhe para o sistema e determine as entidades importantes. Por exemplo, em um sistema de uma loja virtual, os objetos podem ser `Produto`, `Cliente`, `Pedido`.

2. **Liste as propriedades de cada objeto**: Pergunte-se: **O que descreve esse objeto?** O `Produto` pode ter `preço`, `nome`, `categoria`. O `Cliente` pode ter `nome`, `endereço`, `e-mail`.

3. **Defina as ações que o objeto pode realizar**: Pense em **o que esse objeto faz**. O `Produto` pode **ser vendido** ou **ser atualizado**. O `Cliente` pode **fazer um pedido** ou **consultar o status de um pedido**.

---

### 6. Exemplo Prático

Vamos aplicar esse conceito ao objeto `Livro` de um sistema de biblioteca:

#### Propriedades do objeto `Livro`:
```java
public class Livro {
    String titulo;
    String autor;
    int anoDePublicacao;
    boolean disponivelParaEmprestimo;
}
```

#### Ações do objeto `Livro`:
```java
public class Livro {
    void emprestar() {
        if (disponivelParaEmprestimo) {
            System.out.println("Livro emprestado.");
            disponivelParaEmprestimo = false;
        } else {
            System.out.println("Livro não está disponível.");
        }
    }

    void devolver() {
        disponivelParaEmprestimo = true;
        System.out.println("Livro devolvido.");
    }
}
```

Neste exemplo, o `Livro` tem propriedades que descrevem suas características (como `título`, `autor`) e métodos que definem suas ações (`emprestar()`, `devolver()`).

---

### 7. Resumo Final: A Base da POO

Agora que você conhece os conceitos fundamentais de um objeto na POO, fica mais fácil entender a estrutura de um sistema. **Objetos** são partes essenciais de qualquer aplicação orientada a objetos, e cada objeto tem:
- **Propriedades**: O que ele **é**.
- **Ações**: O que ele **faz**.

Com essas ideias em mente, você pode começar a modelar objetos do mundo real ou abstrato em seus programas, tornando-os mais organizados e fáceis de entender.
