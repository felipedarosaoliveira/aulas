
# Classes Wrapper dos Tipos Primitivos em Java

---

### Objetivos:
1. Entender o conceito e a necessidade das classes Wrapper dos tipos primitivos em Java.
2. Aprender a definir e inicializar objetos das classes Wrapper.
3. Explorar os principais métodos para manipulação dessas classes.
4. Compreender o conceito de **Boxing** e **Unboxing**.
5. Aprender sobre o processo antes da versão Java 1.5.

---

## 1. O que são Classes Wrapper?

Em Java, tipos primitivos como `int`, `float`, `boolean` são eficientes em termos de memória e desempenho. No entanto, em muitos casos, especialmente ao trabalhar com estruturas de dados que requerem objetos (como as coleções em Java), é necessário ter uma versão "envolvida" ou "embrulhada" desses tipos primitivos. Para isso, usamos as **classes wrapper**.

As classes wrapper permitem que você trabalhe com tipos primitivos como se fossem objetos. Cada tipo primitivo tem uma classe correspondente na biblioteca Java:

- `int` → `Integer`
- `char` → `Character`
- `boolean` → `Boolean`
- `byte` → `Byte`
- `short` → `Short`
- `long` → `Long`
- `float` → `Float`
- `double` → `Double`

Essas classes são parte do pacote `java.lang`, então não é necessário importá-las explicitamente.

---

## 2. Boxing e Unboxing

Antes de entrar nos detalhes de cada classe wrapper, é importante entender os conceitos de **Boxing** e **Unboxing**.

- **Boxing**: É o processo de converter um tipo primitivo em seu equivalente wrapper. Por exemplo, converter um `int` para um `Integer`.
  
- **Unboxing**: É o processo inverso, de converter um objeto wrapper de volta para o seu tipo primitivo.

Esses processos são feitos automaticamente em Java a partir da versão 5 (Java 1.5). Vamos ver um exemplo:

```java
int numeroPrimitivo = 10;
Integer numeroObjeto = numeroPrimitivo;  // Boxing (int → Integer)

int outroPrimitivo = numeroObjeto;  // Unboxing (Integer → int)
```

### **Como era antes do Java 1.5?**

Antes do **Java 1.5**, o processo de **Boxing** e **Unboxing** não era automático. Você precisava realizar essas conversões manualmente, o que tornava o código mais verboso e propenso a erros.

#### Exemplo no Java anterior à versão 1.5:
```java
int numeroPrimitivo = 10;

// Boxing manual
Integer numeroObjeto = new Integer(numeroPrimitivo);  // Criava explicitamente o objeto Integer

// Unboxing manual
int outroPrimitivo = numeroObjeto.intValue();  // Chamava o método intValue() para converter o objeto em primitivo
```

#### Comparação:
- **Antes do Java 1.5**: Era necessário criar explicitamente o objeto wrapper com o construtor (`new Integer()`) e usar métodos como `intValue()`, `doubleValue()` etc., para extrair o valor primitivo.
- **Depois do Java 1.5**: A conversão entre tipos primitivos e objetos wrapper passou a ser feita de forma automática pelo compilador.

---

## 3. Definindo e Inicializando Objetos Wrapper

#### Exemplo: `Integer` (Wrapper para `int`)

```java
Integer numero = 42;  // Boxing automático de int para Integer
System.out.println(numero);  // Saída: 42
```

#### Exemplo: `Double` (Wrapper para `double`)

```java
Double pi = 3.14159;  // Boxing automático de double para Double
System.out.println(pi);  // Saída: 3.14159
```

#### Exemplo: `Boolean` (Wrapper para `boolean`)

```java
Boolean ativo = true;  // Boxing automático de boolean para Boolean
System.out.println(ativo);  // Saída: true
```

No Java moderno, o processo de **Boxing** é automático. No entanto, se você quiser usar construtores explícitos como no exemplo anterior, ainda é possível, embora isso não seja mais recomendado, pois o desempenho é pior.

```java
Integer numero = new Integer(42);  // Uso do construtor (não recomendado)
```

---

## 4. Métodos Mais Utilizados nas Classes Wrapper

Cada classe wrapper vem com diversos métodos úteis. Abaixo estão alguns dos métodos mais comumente usados:

### 4.1 `Integer`

- **`parseInt(String s)`**: Converte uma string em um `int`.

```java
int valor = Integer.parseInt("123");
System.out.println(valor);  // Saída: 123
```

- **`toString()`**: Converte um valor `Integer` para `String`.

```java
Integer numero = 456;
String str = numero.toString();
System.out.println(str);  // Saída: "456"
```

- **`MAX_VALUE` e `MIN_VALUE`**: Valores máximos e mínimos que um `int` pode armazenar.

```java
System.out.println(Integer.MAX_VALUE);  // Saída: 2147483647
System.out.println(Integer.MIN_VALUE);  // Saída: -2147483648
```

### 4.2 `Double`

- **`parseDouble(String s)`**: Converte uma string em um `double`.

```java
double valor = Double.parseDouble("3.14");
System.out.println(valor);  // Saída: 3.14
```

- **`isNaN()`**: Verifica se o valor é `NaN` (Not a Number).

```java
Double valor = 0.0 / 0.0;
System.out.println(valor.isNaN());  // Saída: true
```

- **`toString()`**: Converte um valor `Double` para `String`.

```java
Double pi = 3.14159;
String str = pi.toString();
System.out.println(str);  // Saída: "3.14159"
```

### 4.3 `Boolean`

- **`parseBoolean(String s)`**: Converte uma string em um valor `boolean`.

```java
boolean ativo = Boolean.parseBoolean("true");
System.out.println(ativo);  // Saída: true
```

- **`toString()`**: Converte um valor `Boolean` para `String`.

```java
Boolean ativo = true;
String str = ativo.toString();
System.out.println(str);  // Saída: "true"
```

- **`TRUE` e `FALSE`**: Constantes que representam os valores `true` e `false`.

---

## 5. Exemplos de Definição e Inicialização de Outras Classes Wrapper

### 5.1 `Character` (Wrapper para `char`)

```java
Character letra = 'A';  // Boxing automático
char letraPrimitiva = letra;  // Unboxing automático
System.out.println(letra);  // Saída: 'A'
```

### 5.2 `Byte` (Wrapper para `byte`)

```java
Byte byteValor = 10;  // Boxing automático
byte valorPrimitivo = byteValor;  // Unboxing automático
System.out.println(byteValor);  // Saída: 10
```

### 5.3 `Short` (Wrapper para `short`)

```java
Short numeroPequeno = 32000;  // Boxing automático
short valorPrimitivo = numeroPequeno;  // Unboxing automático
System.out.println(numeroPequeno);  // Saída: 32000
```

### 5.4 `Long` (Wrapper para `long`)

```java
Long valorGrande = 123456789L;  // Boxing automático
long valorPrimitivo = valorGrande;  // Unboxing automático
System.out.println(valorGrande);  // Saída: 123456789
```

### 5.5 `Float` (Wrapper para `float`)

```java
Float valorFlutuante = 3.14f;  // Boxing automático
float valorPrimitivo = valorFlutuante;  // Unboxing automático
System.out.println(valorFlutuante);  // Saída: 3.14
```

---

## 6. Vantagens de Usar Classes Wrapper

As classes wrapper oferecem várias vantagens, incluindo:

1. **Trabalhar com Coleções**: As coleções em Java, como `ArrayList` e `HashMap`, não podem armazenar tipos primitivos diretamente, apenas objetos. Portanto, os tipos primitivos devem ser convertidos em seus equivalentes wrapper.

2. **Métodos úteis**: Cada classe wrapper fornece métodos utilitários úteis, como conversões de tipos e operações de comparação.

3. **Valores nulos**: Diferente dos tipos primitivos, os objetos wrapper podem ser atribuídos ao valor `null`, o que pode ser útil em algumas situações.

---

## 7. Recapitulando os Principais Conceitos

- As classes wrapper convertem tipos primitivos em objetos, permitindo maior flexibilidade ao trabalhar com coleções e APIs que requerem objetos, além de fornecerem métodos úteis para manipulação de valores.
