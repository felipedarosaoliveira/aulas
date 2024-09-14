### Exercício 1: Sistema de Gerenciamento de Biblioteca

#### Descrição:
Você deve modelar um sistema para **gerenciar uma biblioteca**, onde será possível cadastrar livros e gerenciar o empréstimo dos mesmos. O objetivo é manter o controle dos livros disponíveis e daqueles que foram emprestados, além de registrar informações sobre os empréstimos.

#### Requisitos:
1. O sistema deve **registrar os livros** disponíveis na biblioteca. Cada livro tem um **título**, um **autor**, um **ISBN** e um **status** que indica se ele está disponível ou emprestado.
2. O sistema deve **registrar os empréstimos** feitos por usuários. Cada empréstimo deve conter o **nome do usuário**, o **livro emprestado** e as **datas de empréstimo e devolução**.
3. O sistema deve permitir **registrar a devolução** de um livro e calcular o **tempo total** que o livro ficou emprestado.

#### Modelagem:
- **Classe `Livro`**:
  - Atributos: `titulo`, `autor`, `isbn`, `disponivel` (booleano).
  - Métodos: `emprestarLivro()`, `devolverLivro()`.
  
- **Classe `Usuario`**:
  - Atributos: `nome`.
  - Métodos: `getNome()`.
  
- **Classe `Emprestimo`**:
  - Atributos: `livro`, `usuario`, `dataEmprestimo`, `dataDevolucao`.
  - Métodos: `registrarDevolucao()`, `calcularTempoEmprestado()`.
  
- **Classe `Biblioteca`**:
  - Atributos: `livros`, `emprestimos`.
  - Métodos: `adicionarLivro()`, `emprestarLivro()`, `devolverLivro()`, `consultarLivroDisponivel()`.

---

### Exercício 2: Sistema de Controle de Reservas de Hotel

#### Descrição:
Crie um sistema para gerenciar as **reservas de quartos** em um hotel. O objetivo é permitir que o hotel registre as entradas e saídas dos hóspedes e mantenha um controle sobre a disponibilidade dos quartos.

#### Requisitos:
1. O sistema deve **registrar os quartos** disponíveis no hotel. Cada quarto tem um **número**, uma **capacidade máxima** de hóspedes e um status indicando se está **disponível** ou **ocupado**.
2. O sistema deve permitir **registrar a reserva** de um quarto, armazenando a **data de entrada** e **data de saída** do hóspede.
3. O sistema deve calcular o **tempo de estadia** de cada hóspede e permitir consultar a **disponibilidade** dos quartos.

#### Modelagem:
- **Classe `Quarto`**:
  - Atributos: `numero`, `capacidade`, `disponivel` (booleano).
  - Métodos: `reservar()`, `liberarQuarto()`.
  
- **Classe `Hospede`**:
  - Atributos: `nome`.
  - Métodos: `getNome()`.
  
- **Classe `Reserva`**:
  - Atributos: `quarto`, `hospede`, `dataEntrada`, `dataSaida`.
  - Métodos: `registrarSaida()`, `calcularTempoEstadia()`.
  
- **Classe `Hotel`**:
  - Atributos: `quartos`, `reservas`.
  - Métodos: `adicionarQuarto()`, `fazerReserva()`, `consultarDisponibilidade()`.

---

### Exercício 3: Sistema de Gestão de Pedidos em Restaurante

#### Descrição:
Você deve modelar um sistema para **gerenciar os pedidos** de um restaurante. O objetivo é permitir que os funcionários registrem os pedidos de cada mesa e calculem o valor total a ser pago pelo cliente.

#### Requisitos:
1. O sistema deve registrar os **itens do cardápio** do restaurante. Cada item tem um **nome** e um **preço**.
2. O sistema deve permitir **registrar um pedido** para uma determinada mesa, contendo uma **lista de itens pedidos** e o **nome do garçom** que atendeu.
3. O sistema deve calcular o **valor total** do pedido, somando o preço de todos os itens pedidos.

#### Modelagem:
- **Classe `ItemCardapio`**:
  - Atributos: `nome`, `preco`.
  - Métodos: `getPreco()`, `getNome()`.
  
- **Classe `Pedido`**:
  - Atributos: `itens` (lista de itens do cardápio), `garcom`, `mesa`.
  - Métodos: `adicionarItem()`, `calcularValorTotal()`.
  
- **Classe `Garcom`**:
  - Atributos: `nome`.
  - Métodos: `getNome()`.
  
- **Classe `Restaurante`**:
  - Atributos: `pedidos`, `cardapio`.
  - Métodos: `adicionarPedido()`, `calcularContaMesa()`.

---

