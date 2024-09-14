### Exercício: Modelagem e Implementação de Sistema de Gerenciamento de Estacionamento

#### Descrição do Problema:

Você precisa modelar um sistema de gerenciamento de veículos para um **pátio de estacionamento**. O objetivo é **registrar a entrada e saída** dos veículos e calcular o **valor a ser cobrado** pelo tempo que eles permaneceram estacionados. Vamos detalhar as necessidades do sistema e definir os atributos e métodos necessários para a modelagem.

#### Requisitos:

1. **Gerenciamento de veículos:**
   - O sistema precisa **registrar** cada veículo que entra no estacionamento. Cada veículo é **identificado pela sua placa**.
   - Deve ser possível **armazenar** os dados de entrada e saída dos veículos.

2. **Registro de data e hora:**
   - O sistema deve **registrar o momento exato** em que um veículo entra e sai do estacionamento. Esse registro será usado para calcular o tempo total de permanência do veículo.
   
3. **Cálculo do valor a ser cobrado:**
   - O sistema deve calcular o **tempo total** que o veículo permaneceu estacionado e, com base nesse tempo, calcular o **valor a ser cobrado**. 

---

### Modelagem das Classes

#### 1. **Classe `Veiculo`**:
   - **Responsabilidade**: Representar um veículo que entra no estacionamento.
   - **Atributos**:
     - `placa: String`: Identificação única do veículo.
   - **Métodos**:
     - `getPlaca()`: Retorna a placa do veículo.

```java
public class Veiculo {
    private String placa;

    public Veiculo(String placa) {
        this.placa = placa;
    }

    public String getPlaca() {
        return placa;
    }
}
```

#### 2. **Classe `RegistroEstacionamento`**:
   - **Responsabilidade**: Registrar os detalhes de entrada e saída de um veículo no estacionamento.
   - **Atributos**:
     - `veiculo: Veiculo`: O veículo que está sendo registrado.
     - `dataEntrada: LocalDateTime`: O momento em que o veículo entrou no estacionamento.
     - `dataSaida: LocalDateTime`: O momento em que o veículo saiu do estacionamento (opcional até que o veículo saia).
   - **Métodos**:
     - `registrarEntrada()`: Define o momento da entrada do veículo.
     - `registrarSaida()`: Define o momento da saída do veículo.
     - `calcularTempoEstacionado()`: Calcula o tempo total em que o veículo ficou estacionado.
     - `calcularValorEstacionamento()`: Calcula o valor a ser pago com base no tempo estacionado.

```java
import java.time.LocalDateTime;
import java.time.Duration;

public class RegistroEstacionamento {
    private Veiculo veiculo;
    private LocalDateTime dataEntrada;
    private LocalDateTime dataSaida;

    public RegistroEstacionamento(Veiculo veiculo) {
        this.veiculo = veiculo;
        this.dataEntrada = LocalDateTime.now();  // Registra o momento da entrada
    }

    public void registrarSaida() {
        this.dataSaida = LocalDateTime.now();  // Registra o momento da saída
    }

    public Duration calcularTempoEstacionado() {
        if (dataSaida == null) {
            return Duration.between(dataEntrada, LocalDateTime.now());
        }
        return Duration.between(dataEntrada, dataSaida);  // Tempo total estacionado
    }

    public double calcularValorEstacionamento(double tarifaPorHora) {
        Duration tempoEstacionado = calcularTempoEstacionado();
        long horasEstacionadas = tempoEstacionado.toHours();
        return horasEstacionadas * tarifaPorHora;  // Calcula o valor baseado no tempo
    }
}
```

#### 3. **Classe `Estacionamento`**:
   - **Responsabilidade**: Gerenciar os registros de veículos no estacionamento.
   - **Atributos**:
     - `registros: List<RegistroEstacionamento>`: Armazena os registros dos veículos que estão ou estiveram no estacionamento.
     - `tarifaPorHora: double`: Valor cobrado por hora de estacionamento.
   - **Métodos**:
     - `registrarEntradaVeiculo(placa)`: Registra a entrada de um veículo no estacionamento.
     - `registrarSaidaVeiculo(placa)`: Registra a saída de um veículo.
     - `consultarValor(placa)`: Consulta o valor a ser pago por um veículo específico.

```java
import java.util.ArrayList;
import java.util.List;
import java.util.Optional;

public class Estacionamento {
    private List<RegistroEstacionamento> registros = new ArrayList<>();
    private double tarifaPorHora;

    public Estacionamento(double tarifaPorHora) {
        this.tarifaPorHora = tarifaPorHora;
    }

    public void registrarEntradaVeiculo(String placa) {
        Veiculo veiculo = new Veiculo(placa);
        RegistroEstacionamento registro = new RegistroEstacionamento(veiculo);
        registros.add(registro);
    }

    public void registrarSaidaVeiculo(String placa) {
        Optional<RegistroEstacionamento> registro = registros.stream()
                .filter(r -> r.getVeiculo().getPlaca().equals(placa) && r.getDataSaida() == null)
                .findFirst();

        if (registro.isPresent()) {
            registro.get().registrarSaida();
        } else {
            System.out.println("Veículo não encontrado ou já saiu.");
        }
    }

    public double consultarValor(String placa) {
        Optional<RegistroEstacionamento> registro = registros.stream()
                .filter(r -> r.getVeiculo().getPlaca().equals(placa))
                .findFirst();

        return registro.map(r -> r.calcularValorEstacionamento(tarifaPorHora))
                       .orElse(0.0);
    }
}
```

---

### Explicação Passo a Passo:

1. **Classe `Veiculo`**:
   - O veículo é identificado exclusivamente pela sua placa, que é armazenada como uma string.
   - A classe tem um construtor que define a placa e um método para retornar essa placa (`getPlaca`).

2. **Classe `RegistroEstacionamento`**:
   - Registra a **entrada** e **saída** de um veículo no estacionamento.
   - Usa `LocalDateTime` para registrar os **momentos exatos** de entrada e saída.
   - O método `calcularTempoEstacionado()` calcula o tempo total de permanência usando a classe `Duration`.
   - O método `calcularValorEstacionamento()` usa o tempo estacionado e uma tarifa por hora para determinar o valor a ser cobrado.

3. **Classe `Estacionamento`**:
   - Gerencia todos os registros de veículos no estacionamento.
   - Armazena os registros em uma lista e permite registrar a entrada e saída dos veículos.
   - Permite consultar o valor a ser pago por um veículo com base no tempo estacionado e na tarifa por hora.

---

### Desafios:
- Implemente melhorias, como permitir tarifas diferenciadas (ex: por minuto ou por fração de hora).
- Adicione a funcionalidade de emitir um **relatório diário** com todos os veículos e valores cobrados no estacionamento.

---

### Objetivo do Exercício:

O objetivo deste exercício é permitir que você aplique os conceitos de **modelagem orientada a objetos** para resolver um problema real, separando responsabilidades entre classes e entendendo como diferentes entidades interagem no sistema.