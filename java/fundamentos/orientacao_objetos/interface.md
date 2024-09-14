### Aula: Fundamentos da Programação Orientada a Objetos (POO) - Interfaces em Java

#### Duração: 30 minutos

---

### Objetivos da aula:
1. Compreender o que é uma **interface** na Programação Orientada a Objetos (POO) em Java.
2. Aprender como definir e implementar uma **interface**.
3. Entender que todos os métodos de uma interface são **públicos**, mesmo que a palavra-chave não seja explicitada.
4. Explorar o conceito de **métodos `default`** em interfaces e como usá-los.
5. Apresentar os conceitos de forma prática e didática, facilitando a compreensão e a fixação dos alunos.

---

### 1. O que é uma Interface?

Imagine que você tem diferentes tipos de **dispositivos** que podem **tocar música**, como um **smartphone** e um **computador**. Cada dispositivo tem sua própria maneira de tocar música, mas ambos seguem a mesma regra: eles devem ser capazes de iniciar e parar uma música. Aqui entra o conceito de **interface**.

#### Definição Simples:
- **Interface** é como um **contrato** que define um conjunto de **métodos** que uma classe deve implementar. No entanto, a interface **não fornece a implementação** para esses métodos.
- A interface especifica **o que** uma classe deve fazer, mas **não como** ela deve fazer.

### Diferença entre Interface e Herança:
- Enquanto a **herança** define uma relação "é um tipo de", a **interface** define "é capaz de". Por exemplo, um **Carro** é um **Veículo** (herança), mas também pode ser capaz de **dirigir** (interface).

---

### 2. Definindo uma Interface em Java

Em Java, usamos a palavra-chave **`interface`** para declarar uma interface. Todas as classes que "implementam" essa interface devem fornecer a implementação dos métodos definidos.

#### Exemplo de Definição de Interface:

```java
// Definindo uma interface
public interface ReprodutorMusical {
    void tocar();  // Método abstrato
    void pausar();  // Método abstrato
    void parar();  // Método abstrato
}
```

#### Características da Interface:
1. **Métodos são sempre públicos**: Todos os métodos de uma interface são **implicitamente públicos**, mesmo que a palavra-chave `public` não seja especificada.
2. **Sem implementação**: Os métodos da interface não possuem corpo (até o Java 8, quando surgiram os métodos `default`, que vamos ver mais adiante).
3. **Classe implementadora**: Uma classe que "implementa" uma interface deve fornecer a implementação de todos os métodos declarados na interface.

---

### 3. Implementando uma Interface em Java

Para que uma classe "use" uma interface, ela deve **implementar** essa interface usando a palavra-chave **`implements`**. A classe então se compromete a implementar **todos os métodos** definidos na interface.

#### Exemplo de Implementação:

```java
// Classe Smartphone que implementa a interface ReprodutorMusical
public class Smartphone implements ReprodutorMusical {
    @Override
    public void tocar() {
        System.out.println("Smartphone tocando música.");
    }

    @Override
    public void pausar() {
        System.out.println("Smartphone pausou a música.");
    }

    @Override
    public void parar() {
        System.out.println("Smartphone parou a música.");
    }
}

// Classe Computador que implementa a mesma interface
public class Computador implements ReprodutorMusical {
    @Override
    public void tocar() {
        System.out.println("Computador tocando música.");
    }

    @Override
    public void pausar() {
        System.out.println("Computador pausou a música.");
    }

    @Override
    public void parar() {
        System.out.println("Computador parou a música.");
    }
}
```

### Benefício:
A interface **`ReprodutorMusical`** define um conjunto de ações (`tocar`, `pausar`, `parar`), mas deixa para cada classe (como `Smartphone` e `Computador`) definir **como** essas ações são executadas.

### Uso:
```java
public class Main {
    public static void main(String[] args) {
        ReprodutorMusical smartphone = new Smartphone();
        ReprodutorMusical computador = new Computador();

        smartphone.tocar();    // Smartphone tocando música.
        computador.tocar();    // Computador tocando música.

        smartphone.pausar();   // Smartphone pausou a música.
        computador.parar();    // Computador parou a música.
    }
}
```

---

### 4. Métodos `default` em Interfaces (Introduzido no Java 8)

Antes do Java 8, **todos os métodos** em uma interface eram **abstratos** (sem implementação). Porém, com a introdução dos **métodos `default`**, agora é possível fornecer uma **implementação padrão** dentro da interface. Isso permite que as classes implementadoras **não precisem obrigatoriamente sobrescrever** esses métodos.

#### O que são Métodos `default`?

- Um método **`default`** em uma interface é um método que já possui uma implementação padrão, mas pode ser sobrescrito pela classe que implementa a interface.
- Isso ajuda a manter a compatibilidade com código antigo ao adicionar novos métodos a uma interface, sem obrigar todas as classes a implementá-los.

---

### 5. Exemplo Prático de Métodos `default` em Interfaces

Imagine que você queira adicionar a funcionalidade de **ajustar o volume** no `ReprodutorMusical`. Se fizermos isso na interface sem fornecer uma implementação padrão, todas as classes que implementam essa interface seriam obrigadas a implementar este novo método. Mas, com o uso do método `default`, podemos fornecer uma implementação padrão que as classes podem ou não sobrescrever.

#### Exemplo de Interface com Método `default`:

```java
public interface ReprodutorMusical {
    void tocar();
    void pausar();
    void parar();

    // Método default com implementação
    default void ajustarVolume(int volume) {
        System.out.println("Ajustando o volume para: " + volume);
    }
}
```

#### Como Funciona:
- A classe implementadora pode usar o método `default` sem precisar sobrescrevê-lo.
- Se a classe implementadora quiser fornecer sua própria versão do método, ela pode sobrescrevê-lo.

#### Exemplo de Classe com Método `default`:

```java
public class Computador implements ReprodutorMusical {
    @Override
    public void tocar() {
        System.out.println("Computador tocando música.");
    }

    @Override
    public void pausar() {
        System.out.println("Computador pausou a música.");
    }

    @Override
    public void parar() {
        System.out.println("Computador parou a música.");
    }

    // Usa o método default sem precisar sobrescrevê-lo
}
```

### Uso:

```java
public class Main {
    public static void main(String[] args) {
        ReprodutorMusical computador = new Computador();
        computador.tocar();   // Computador tocando música.
        computador.ajustarVolume(50);  // Ajustando o volume para: 50
    }
}
```

### Personalizando o Método `default`:

Se desejarmos, podemos sobrescrever o método `default` em uma classe específica. Por exemplo, se o `Smartphone` precisar de uma lógica diferente para ajustar o volume, podemos fazer assim:

```java
public class Smartphone implements ReprodutorMusical {
    @Override
    public void tocar() {
        System.out.println("Smartphone tocando música.");
    }

    @Override
    public void pausar() {
        System.out.println("Smartphone pausou a música.");
    }

    @Override
    public void parar() {
        System.out.println("Smartphone parou a música.");
    }

    // Sobrescrevendo o método default para o Smartphone
    @Override
    public void ajustarVolume(int volume) {
        System.out.println("Ajustando o volume do smartphone para: " + volume);
    }
}
```

---

### 6. Interfaces vs. Classes Abstratas

As **interfaces** e as **classes abstratas** possuem propósitos semelhantes, mas são usadas em contextos diferentes.

#### Diferenças:
1. **Herança múltipla**: Uma classe pode implementar **múltiplas interfaces**, mas só pode herdar de **uma classe abstrata**.
2. **Métodos com corpo**: Antes do Java 8, interfaces não podiam ter métodos com corpo, enquanto classes abstratas podem. Agora, interfaces podem ter **métodos `default`** com implementação.
3. **Estado**: Interfaces não podem armazenar estado (atributos), enquanto classes abstratas podem ter atributos e métodos concretos.

### Quando usar uma Interface?
- Use interfaces quando você precisa definir **comportamentos comuns** que podem ser compartilhados por **classes não relacionadas**. Exemplo: Dispositivos que podem "tocar música", como smartphones e computadores.
  
### Quando usar uma Classe Abstrata?
- Use classes abstratas quando há uma **relação de herança** entre as classes e você deseja **compartilhar código e comportamento** entre elas. Exemplo: `Veículo` como uma classe base para `Carro` e `Moto`.

---
