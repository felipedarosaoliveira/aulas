### Aula: Fundamentos da Programação Orientada a Objetos (POO) - Herança em Java


---

### Objetivos da aula:
1. Compreender o conceito de **herança** na Programação Orientada a Objetos (POO).
2. Entender que na herança apenas os **atributos e métodos públicos e protegidos** são herdados.
3. Conhecer a **classe `Object`** e o fato de que todas as classes em Java herdam dela.
4. Explorar o conceito e a aplicação de **classes abstratas**.
5. Assimilar os conceitos de forma prática e clara, com exemplos aplicáveis em Java.

---

### 1. Introdução à Herança: Um Conceito Natural

Na Programação Orientada a Objetos (POO), a **herança** permite que uma classe derive de outra, herdando suas características e comportamentos públicos e protegidos. A herança é uma maneira poderosa de **reutilizar código** e criar uma relação hierárquica entre classes.

#### Definição Simples de Herança
- A **herança** permite que uma **subclasse** herde atributos e métodos **públicos** e **protegidos** de uma **superclasse**.
- Isso significa que a subclasse pode **acessar** diretamente os membros **públicos** da superclasse, bem como os membros **protegidos**.
- Os **membros privados** não são herdados diretamente, mas podem ser acessados indiretamente por meio de métodos públicos da superclasse (como getters e setters).

---

### 2. Definindo Herança em Java

Em Java, o conceito de herança é implementado com a palavra-chave **`extends`**. Quando uma classe herda outra, ela pode reutilizar os membros públicos e protegidos da superclasse e adicionar ou sobrescrever comportamentos.

#### Exemplo Prático de Herança em Java

```java
// Superclasse (classe base)
public class Animal {
    // Atributo protegido (acessível pela subclasse)
    protected String nome;

    // Método público (herdado e acessível pela subclasse)
    public void comer() {
        System.out.println(nome + " está comendo.");
    }

    // Método público (herdado e acessível pela subclasse)
    public void dormir() {
        System.out.println(nome + " está dormindo.");
    }
}

// Subclasse (classe derivada)
public class Cachorro extends Animal {
    // Método específico da subclasse
    public void latir() {
        System.out.println(nome + " está latindo.");
    }
}
```

#### Como Funciona a Herança
1. **Atributos e métodos públicos e protegidos** da superclasse são herdados e podem ser acessados diretamente pela subclasse.
2. A **subclasse** pode ter métodos específicos que não existem na superclasse, como o método `latir()` no exemplo.
3. A **subclasse** também pode **sobrescrever** métodos da superclasse, permitindo modificar comportamentos herdados.

### Uso:
```java
public class Main {
    public static void main(String[] args) {
        Cachorro cachorro = new Cachorro();
        cachorro.nome = "Rex";  // Nome é acessível pois está protegido na superclasse
        cachorro.comer();    // Rex está comendo.
        cachorro.latir();    // Rex está latindo.
    }
}
```

---

### 3. A Classe `Object`: A Superclasse de Todas as Classes

Em Java, **todas as classes herdam implicitamente da classe `Object`**, a superclasse universal. Mesmo que você não especifique explicitamente, todas as classes têm `Object` como superclasse.

#### Métodos da Classe `Object`:
A classe `Object` define alguns métodos que todas as classes em Java herdam:

1. **`toString()`**: Retorna uma representação textual do objeto.
   - Você pode sobrescrever este método para personalizar a saída.
   - Exemplo:
   ```java
   @Override
   public String toString() {
       return "Nome do animal: " + nome;
   }
   ```

2. **`equals(Object obj)`**: Compara se dois objetos são iguais, baseado nos valores dos atributos.
   
   Exemplo:
   ```java
   @Override
   public boolean equals(Object obj) {
       if (this == obj) return true;
       if (obj == null || getClass() != obj.getClass()) return false;
       Animal animal = (Animal) obj;
       return nome.equals(animal.nome);
   }
   ```

3. **`hashCode()`**: Retorna um valor hash para o objeto, útil em coleções como `HashMap`.
4. **`getClass()`**: Retorna a classe do objeto em tempo de execução.

---

### 4. Conceito de Classes Abstratas

Uma **classe abstrata** em Java é uma classe que **não pode ser instanciada diretamente**. Ela serve como um "molde" para outras classes que a herdam, forçando-as a implementar certos métodos abstratos (métodos sem corpo).

#### O que é uma Classe Abstrata?
- Uma **classe abstrata** pode ter **métodos concretos** (com corpo) e **métodos abstratos** (sem corpo).
- **Métodos abstratos** devem ser implementados pelas subclasses.
- Uma **classe abstrata** não pode ser instanciada diretamente, ou seja, não podemos criar objetos dessa classe.

### Exemplo de Classe Abstrata em Java

```java
// Classe abstrata
public abstract class Animal {
    protected String nome;

    // Método concreto
    public void dormir() {
        System.out.println(nome + " está dormindo.");
    }

    // Método abstrato (sem implementação)
    public abstract void emitirSom();
}

// Subclasse concreta que implementa os métodos abstratos
public class Cachorro extends Animal {
    @Override
    public void emitirSom() {
        System.out.println(nome + " está latindo.");
    }
}
```

### Como Usar:
```java
public class Main {
    public static void main(String[] args) {
        // Animal animal = new Animal(); // Não pode instanciar diretamente!
        Cachorro cachorro = new Cachorro();
        cachorro.nome = "Rex";
        cachorro.emitirSom();  // Rex está latindo.
        cachorro.dormir();     // Rex está dormindo.
    }
}
```

### Benefícios das Classes Abstratas
- **Reutilização de Código**: Classes abstratas permitem que métodos concretos sejam compartilhados entre subclasses.
- **Flexibilidade**: Subclasses podem ser obrigadas a implementar métodos abstratos, garantindo que certos comportamentos existam em todas as subclasses.
- **Polimorfismo**: Uma classe abstrata pode ser usada como tipo de referência, permitindo que várias subclasses diferentes implementem comportamentos de maneiras distintas.

---

### 5. Diferença entre Classe Abstrata e Herança Simples

- **Classe Abstrata**: Não pode ser instanciada diretamente. Serve como um modelo para outras classes. Pode ter métodos abstratos que forçam as subclasses a fornecer implementações específicas.
  
- **Herança Simples**: A subclasse herda atributos e métodos públicos e protegidos da superclasse, mas pode ser instanciada diretamente, exceto se for abstrata.

#### Quando Usar:
- Use **herança simples** quando a classe base pode ser instanciada e tem uma implementação completa.
- Use **classe abstrata** quando a classe base é genérica demais para ser instanciada diretamente, mas deve servir como um modelo para subclasses mais específicas.

---

### 6. Resumo Final: Herança, Classe `Object` e Classes Abstratas

- **Herança** é uma maneira de reaproveitar código. Subclasses herdam **atributos e métodos públicos e protegidos** da superclasse, mas não têm acesso direto aos membros privados.
- Todas as classes em Java herdam da classe **`Object`**, o que fornece métodos comuns como `toString()`, `equals()`, e `hashCode()`.
- **Classes abstratas** são usadas quando queremos criar uma classe genérica que não pode ser instanciada diretamente, mas que define comportamentos que devem ser implementados por suas subclasses.

### Exercício Prático

Crie um programa que modele diferentes tipos de **veículos** usando herança:
- Crie uma **classe abstrata `Veiculo`** com métodos abstratos como `acelerar()` e `frear()`.
- Implemente subclasses como `Carro`, `Moto` e `Bicicleta`, cada uma com sua própria implementação dos métodos.

---

### Considerações Didáticas

1. **Construa o conhecimento gradualmente**: Comece apresentando o conceito de herança de maneira simples e prática, utilizando exemplos do mundo real para facilitar a compreensão.
2. **Foque no essencial**: Mostre que a subclasse herda **apenas os membros públicos e protegidos** da superclasse, e que o acesso a membros privados é feito por métodos públicos.
3. **Dê exemplos claros**: Use exemplos de classes e métodos que os alunos possam facilmente relacionar ao mundo real, como animais e veículos.
4. **Pratique**: Incorpore exercícios que incentivem os alunos a escrever código e aplicar os conceitos discutidos em aula, reforçando a compreensão de herança, classes abstratas e polimorfismo.

Com essa abordagem, os alunos terão uma visão clara e prática dos conceitos de herança em Java e estarão prontos para aplicar esses conceitos em seus projetos.