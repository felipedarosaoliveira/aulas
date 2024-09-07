
# Aula: Fundamentos da Programação Orientada a Objetos (POO)

---

### Objetivos da aula:
1. Entender o que é a Programação Orientada a Objetos (POO) e por que ela foi criada.
2. Conhecer o histórico da POO e seus criadores.
3. Compreender os quatro pilares fundamentais da POO.

---

## 1. Introdução à Programação Orientada a Objetos

A Programação Orientada a Objetos (POO) é um paradigma de programação que surgiu como uma solução para lidar com a crescente complexidade dos softwares. Ela organiza o desenvolvimento de programas em torno de **objetos**, que são abstrações do mundo real. Cada objeto combina dados e comportamentos, representando entidades reais de forma mais intuitiva para os programadores.

### Motivo da Criação

Nos primeiros tempos da computação, os programas eram estruturados de maneira linear, o que tornava difícil a manutenção, escalabilidade e compreensão de grandes sistemas. À medida que os sistemas cresciam em complexidade, os programadores sentiram a necessidade de uma abordagem mais modular e organizada para o desenvolvimento de software.

A POO foi criada para resolver esses problemas, permitindo que os desenvolvedores pudessem modelar o mundo real de forma mais próxima à realidade, facilitando o desenvolvimento, a manutenção e a reutilização de código.

### Criadores da POO

O conceito de Programação Orientada a Objetos foi desenvolvido inicialmente por **Ole-Johan Dahl** e **Kristen Nygaard**, dois cientistas noruegueses, no início da década de 1960. Eles desenvolveram a linguagem de programação **Simula**, que é considerada a primeira linguagem orientada a objetos. O objetivo original era criar uma linguagem que pudesse modelar simulações de sistemas complexos.

Mais tarde, na década de 1970, a linguagem **Smalltalk**, desenvolvida por **Alan Kay** e sua equipe no Xerox PARC, popularizou a POO e introduziu conceitos que ainda são amplamente usados em linguagens modernas, como Java e Python.

---

## 2. Os Quatro Pilares da Programação Orientada a Objetos

A POO é sustentada por quatro conceitos principais, também chamados de **pilares**:

### 2.1 Encapsulamento

O encapsulamento é a prática de agrupar dados (atributos) e comportamentos (métodos) em uma mesma unidade chamada **classe**. Ele também controla o acesso a esses dados, protegendo-os de serem alterados de maneira inadequada.

**Exemplo**: Imagine uma classe `ContaBancaria`. Ela tem um atributo privado `saldo`, que só pode ser alterado por métodos públicos como `depositar` e `sacar`. Isso impede que qualquer parte do código altere o saldo diretamente.

### 2.2 Herança

Herança é o mecanismo pelo qual uma classe pode **herdar** características (atributos e métodos) de outra classe. A classe que herda é chamada de **subclasse**, e a classe que é herdada é chamada de **superclasse**.

**Exemplo**: Se temos uma classe `Animal`, podemos criar uma classe `Cachorro` que herda todas as características de `Animal`, mas também pode adicionar comportamentos próprios, como o método `latir()`.

### 2.3 Polimorfismo

O polimorfismo permite que diferentes classes usem métodos com o **mesmo nome**, mas que se comportam de maneira diferente dependendo do contexto. Ele pode ser dividido em:
- **Sobrecarga de métodos**: Definir múltiplos métodos com o mesmo nome, mas com parâmetros diferentes.
- **Sobrescrita de métodos**: A subclasse pode modificar o comportamento de um método herdado da superclasse.

**Exemplo**: Se temos um método `fazerSom()` em `Animal`, a classe `Cachorro` pode sobrescrever esse método para latir, enquanto a classe `Gato` pode sobrescrever para miar.

### 2.4 Abstração

A abstração é a capacidade de simplificar conceitos complexos, ocultando os detalhes de implementação e expondo apenas o essencial. Classes abstratas e interfaces são frequentemente usadas para definir comportamentos gerais que outras classes específicas devem implementar.

**Exemplo**: Em um sistema bancário, podemos ter uma classe abstrata `Conta`, que define o comportamento básico de qualquer conta. As classes `ContaCorrente` e `ContaPoupanca` implementariam essas características de maneira específica.

---

## 3. Resumo Final

A Programação Orientada a Objetos foi criada para resolver os problemas da crescente complexidade dos sistemas de software, oferecendo uma maneira modular e eficiente de estruturar programas. Desenvolvida inicialmente por **Ole-Johan Dahl** e **Kristen Nygaard** com a linguagem **Simula**, e popularizada por **Alan Kay** com **Smalltalk**, a POO permite modelar sistemas complexos de maneira mais próxima à realidade, facilitando a manutenção e a reutilização de código.

Com o uso de **objetos**, **classes** e os pilares da POO (**Encapsulamento**, **Herança**, **Polimorfismo**, e **Abstração**), é possível desenvolver software mais flexível, reutilizável e fácil de manter. Ao entender esses conceitos, você estará preparado para explorar e aplicar a POO em linguagens como Java, Python, C++ e muitas outras.
