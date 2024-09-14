
#### Classe `Jogador`

```java
package com.jogo.advinhacao;

import java.util.Scanner;

public class Jogador {
    // Atributos privados
    private String nome;
    private int tentativas;
    private Scanner scanner;  // Scanner agora é parte da classe Jogador

    // Construtor
    public Jogador(String nome) {
        this.nome = nome;
        this.tentativas = 0;  // Inicializa as tentativas com 0
        this.scanner = new Scanner(System.in);  // Inicializa o Scanner
    }

    // Getter para o nome
    public String getNome() {
        return nome;
    }

    // Getter para o número de tentativas
    public int getTentativas() {
        return tentativas;
    }

    // Método para incrementar as tentativas
    public void incrementarTentativas() {
        this.tentativas++;
    }

    // Método para solicitar o palpite do jogador
    public int darPalpite() {
        System.out.print("Digite seu palpite: ");
        String entrada = scanner.nextLine();  // Lê a entrada como uma string

        // Verifica se a entrada é numérica
        if (entrada.matches("\\d+")) {  // Verifica se a string contém apenas números
            return Integer.parseInt(entrada);  // Converte para inteiro
        } else {
            System.out.println("Por favor, digite um número válido.");
            return -1;  // Retorna -1 para indicar entrada inválida
        }
    }
}
```

#### Classe `JogoAdvinhacao`

```java
package com.jogo.advinhacao;

import java.util.Scanner;

public class JogoAdvinhacao {
    // Atributos privados
    private int numeroSecreto;
    private int limiteTentativas;
    private Jogador jogador;  // Associação com a classe Jogador

    // Construtor padrão
    public JogoAdvinhacao(int limiteTentativas, Jogador jogador) {
        this.numeroSecreto = (int) (Math.random() * 100) + 1;  // Gera um número entre 1 e 100
        this.limiteTentativas = limiteTentativas;
        this.jogador = jogador;  // Atribui o jogador
    }

    // Método para verificar a tentativa do jogador
    public boolean verificarTentativa(int tentativa) {
        jogador.incrementarTentativas();  // Incrementa as tentativas do jogador

        if (tentativa == numeroSecreto) {
            System.out.println("Parabéns, " + jogador.getNome() + "! Você acertou o número.");
            return true;
        } else if (tentativa < numeroSecreto) {
            System.out.println("Tente um número maior.");
        } else {
            System.out.println("Tente um número menor.");
        }

        if (jogador.getTentativas() >= limiteTentativas) {
            System.out.println("Você atingiu o limite de tentativas! O número correto era " + numeroSecreto);
            return true;  // Termina o jogo
        }

        return false;
    }

    // Método que inicia o jogo
    public void iniciarJogo() {
        System.out.println("Bem-vindo ao jogo de adivinhação, " + jogador.getNome() + "!");
        System.out.println("Você tem " + limiteTentativas + " tentativas para adivinhar o número entre 1 e 100.");

        boolean acertou = false;

        while (!acertou) {
            int palpite = jogador.darPalpite();  // Agora o palpite vem da classe Jogador
            if (palpite != -1) {  // Verifica se o palpite é válido (não é -1)
                acertou = verificarTentativa(palpite);
            }
        }
    }
}
```

---

#### Classe `JogoAdvinhacao`

```java
package com.jogo.advinhacao;

import java.util.Scanner;

public class App {
    

    public static void main(String[] args) {
        // Coletando o nome do jogador
        System.out.print("Digite seu nome: ");
        Scanner scanner = new Scanner(System.in);
        String nome = scanner.nextLine();

        // Criando uma instância do jogador
        Jogador jogador = new Jogador(nome);

        // Criando uma instância do jogo
        JogoAdvinhacao jogo = new JogoAdvinhacao(5, jogador);
        jogo.iniciarJogo();  // Iniciando o jogo
    }
}
```

---

### Explicação

1. **Verificação Simples de Entrada**:
   - Na classe `Jogador`, o método `darPalpite()` verifica se a entrada do jogador contém apenas dígitos (`\\d+`). Se sim, a string é convertida para um número inteiro usando `Integer.parseInt()`. Caso contrário, o método retorna `-1`, indicando que a entrada é inválida.
   - O jogo só processa a tentativa se o valor retornado for diferente de `-1`.

2. **Separação de Responsabilidades**:
   - A classe `Jogador` continua responsável por capturar o palpite do jogador, e agora faz uma verificação simples para garantir que a entrada seja válida.
   - A classe `JogoAdvinhacao` é responsável pela lógica do jogo, verificando se o palpite é válido e se o jogador acertou ou esgotou suas tentativas.

3. **Manutenção Simples**:
   - A verificação da entrada foi simplificada sem usar exceções. O código permanece claro e modular, facilitando o entendimento dos conceitos de encapsulamento e modularidade em Java.

---