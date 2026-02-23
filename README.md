# Atividade 01 — Tipos de Dados em C++

> "First, solve the problem. Then, write the code." — John Johnson

---

## Objetivos de Aprendizagem

Ao concluir esta atividade você será capaz de:

1. Utilizar o **GitHub** para versionar e publicar os exercícios da disciplina.
2. Navegar pelo **Visual Studio** (IDE adotada na disciplina) com familiaridade.
3. **Compilar e executar** programas em C++.
4. Identificar e usar os principais **tipos de dados primitivos** em C++.
5. Compreender a diferença entre **valor** e **referência (ponteiro)**.
6. Ler dados digitados pelo usuário com `cin` e exibir resultados com `cout`.

---

## Conceitos Fundamentais

### Por que tipos de dados importam?

Todo dado armazenado na memória ocupa um espaço físico (bytes). O **tipo de dado** informa ao compilador:

- Quanto espaço reservar na memória.
- Que operações são permitidas sobre aquele valor.
- Como interpretar os bits armazenados.

Escolher o tipo errado pode causar desperdício de memória, perda de precisão ou comportamentos imprevistos.

---

### Tipos Numéricos Inteiros

Representam números **sem parte decimal**.

| Tipo    | Tamanho típico | Faixa aproximada                          |
|---------|---------------|-------------------------------------------|
| `short` | 2 bytes        | −32.768 a 32.767                          |
| `int`   | 4 bytes        | −2.147.483.648 a 2.147.483.647            |
| `long`  | 4 ou 8 bytes   | Depende da plataforma/compilador          |

```cpp
int    i = 10;
short  s = 18;
long   l = 200000;
```

> **Dica:** Use `sizeof(variavel)` para descobrir o tamanho real em bytes na sua máquina.

---

### Tipos Numéricos de Ponto Flutuante

Representam números **com parte decimal** (reais).

| Tipo     | Tamanho | Precisão (dígitos significativos) |
|----------|---------|-----------------------------------|
| `float`  | 4 bytes | ~7 dígitos                        |
| `double` | 8 bytes | ~15 dígitos                       |

```cpp
float  f = 1.97F;   // sufixo 'F' indica que é float
double d = 4.73;    // sem sufixo é double por padrão
```

> **Atenção:** Para valores monetários ou científicos que exigem precisão, prefira `double`.

---

### Tipo Lógico (`bool`)

Representa apenas dois estados: **verdadeiro** (`true`) ou **falso** (`false`).

```cpp
bool flFacil = false;
```

Internamente, `false` é armazenado como `0` e `true` como qualquer valor diferente de zero (geralmente `1`).

Ocupa **1 byte** na maioria dos compiladores.

---

### Tipo Caractere (`char`)

Armazena **um único caractere** codificado na tabela ASCII.

```cpp
char letra = 'Z';   // aspas simples para char
```

Ocupa **1 byte**. Como `char` é, internamente, um número inteiro pequeno, operações aritméticas são válidas:

```cpp
char a = 'A';       // armazena 65 (código ASCII de 'A')
char b = a + 1;     // b == 'B' (66)
```

---

### Tipo Texto (`string`)

Representa uma **sequência de caracteres** (texto). Requer o cabeçalho `<string>` (ou `<iostream>` indiretamente via `using namespace std`).

```cpp
string texto = "Estrutura de Dados vai ser moleza!";  // aspas duplas para string
```

> Diferente dos tipos primitivos acima, `string` é uma **classe** da biblioteca padrão do C++ (STL), por isso seu `sizeof` retorna o tamanho do objeto que gerencia o texto, não o número de caracteres.

---

### Ponteiros

Um **ponteiro** é uma variável que armazena o **endereço de memória** de outra variável.

```cpp
string* ponteiro = &texto;  // '&' obtém o endereço de 'texto'
```

| Operador | Significado                                      |
|----------|--------------------------------------------------|
| `&var`   | Endereço de memória da variável `var`            |
| `*ptr`   | Valor armazenado no endereço apontado por `ptr`  |

```cpp
cout << ponteiro;    // exibe o endereço (ex.: 0x61fe10)
cout << *ponteiro;   // exibe o valor:   "Estrutura de Dados vai ser moleza!"
```

> **Por que ponteiros são importantes em Estrutura de Dados?**  
> Listas encadeadas, árvores, grafos e outras estruturas dinâmicas são construídas conectando nós através de ponteiros.

---

### Entrada de Dados (`cin`)

O operador `>>` lê um valor digitado pelo usuário e armazena na variável indicada.

```cpp
string nome = "";
int    idade = 0;

cout << "Digite seu nome: ";
cin  >> nome;

cout << "Digite sua idade: ";
cin  >> idade;
```

> **Limitação:** `cin >>` interrompe a leitura no **primeiro espaço em branco**. Para ler uma linha inteira, use `getline(cin, nome)`.

---

## Como Executar o Projeto

1. Abra o arquivo `TiposDeDados.sln` no **Visual Studio**.
2. Pressione **F5** (ou `Depurar → Iniciar Depuração`) para compilar e executar.
3. Observe a saída no console. Anote os tamanhos de cada tipo na sua máquina.

---

## Exercícios Propostos

Após estudar e executar o código de exemplo, implemente as extensões abaixo no mesmo projeto (ou em um projeto separado, como preferir).

### Exercício 1 — Limites dos Tipos

Inclua o cabeçalho `<climits>` e exiba os valores máximo e mínimo de `int` e `short`:

```cpp
#include <climits>
cout << "int  max = " << INT_MAX  << "\n";
cout << "int  min = " << INT_MIN  << "\n";
cout << "short max = " << SHRT_MAX << "\n";
```

**Pergunta:** O que acontece quando você soma `INT_MAX + 1`?

---

### Exercício 2 — Conversão de Temperatura

Leia uma temperatura em **Celsius** (use `double`) e converta para **Fahrenheit** e **Kelvin**.

- Fórmula Fahrenheit: $F = C \times 1{,}8 + 32$
- Fórmula Kelvin: $K = C + 273{,}15$

---

### Exercício 3 — Calculadora de Segundos

Leia um número de segundos (`long`) digitado pelo usuário e exiba o equivalente em:
- Dias
- Horas
- Minutos
- Segundos restantes

---

### Exercício 4 — Ponteiro na Prática

Declare uma variável `int` com qualquer valor, depois:

1. Exiba o **valor** da variável.
2. Exiba o **endereço** da variável usando `&`.
3. Declare um ponteiro `int*` apontando para ela.
4. Através do ponteiro, **altere** o valor para o dobro.
5. Exiba o novo valor da variável original (sem usar o ponteiro desta vez).

---

## Entrega

### 1. Faça um *fork* do repositório

Um **fork** cria uma cópia do repositório da disciplina na **sua própria conta do GitHub**, permitindo que você trabalhe de forma independente sem afetar o original.

1. Acesse o repositório da disciplina no GitHub (URL fornecida pelo professor).
2. Clique no botão **Fork** (canto superior direito da página).
3. Confirme a criação do fork na sua conta. O repositório aparecerá em `github.com/<seu-usuario>/<nome-do-repo>`.

### 2. Clone o fork para o seu computador

No terminal (ou no próprio Visual Studio), clone o repositório forkado:

```bash
git clone https://github.com/<seu-usuario>/<nome-do-repo>.git
```

### 3. Implemente as atividades

- Abra o projeto `TiposDeDados.sln` no Visual Studio.
- Estude, execute e modifique o código de exemplo conforme necessário.
- Implemente **pelo menos dois** dos exercícios propostos neste roteiro.
- Certifique-se de que o projeto **compila sem erros** antes de continuar.

### 4. Salve e envie para o GitHub

```bash
git add .
git commit -m "Atividade 01 - Tipos de Dados"
git push
```

### 5. Envie a URL do seu repositório

- Copie a URL do seu fork no GitHub (ex.: `https://github.com/<seu-usuario>/<nome-do-repo>`).
- Cole essa URL na **plataforma da disciplina**, conforme orientação do professor.

> **Atenção:** Certifique-se de que o repositório está **público**, caso contrário o professor não conseguirá visualizar o conteúdo.

---

## Referências

- [cppreference — Tipos fundamentais (C++)](https://en.cppreference.com/w/cpp/language/types)
- [cppreference — Ponteiros](https://en.cppreference.com/w/cpp/language/pointer)
- [LearnCpp — Chapter 4: Fundamental Data Types](https://www.learncpp.com/cpp-tutorial/introduction-to-fundamental-data-types/)
