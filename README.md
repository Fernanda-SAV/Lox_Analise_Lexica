
# COMPILADORES P2 - Lox: Análise Léxica e Interpretador Tree-Walk - Fernanda Sousa de Assunção Vale e Izadora de Paula Santos Lima
Trabalho submetido à disciplina de Compiladores — Implementação do Interpretador Lox


# Lox: Análise Léxica e Interpretador
<div align="center">
  <img src="https://img.shields.io/badge/Versão-1.0-blue.svg" alt="Versão 1.0">
  <img src="https://img.shields.io/badge/Licença-MIT-green.svg" alt="Licença MIT">
</div>

---

## Resumo do Trabalho

Este repositório contém a implementação das principais etapas do interpretador da linguagem **Lox**, conforme o livro *Crafting Interpreters*, de Robert Nystrom.

O projeto evoluiu da **análise léxica** para um **interpretador completo do tipo Tree-Walk**, contemplando:

> - Análise Léxica (Scanner) — conversão do código-fonte em tokens
> - Análise Sintática (Parser) — construção da Árvore Sintática Abstrata (AST)
> - Representação de Expressões e Comandos (Expr e Stmt)
> - Resolução estática de escopos (Resolver)
> - Execução do código por meio do Interpreter
> - Execução interativa no modo REPL
> - Execução de programas completos a partir de arquivos `.lox`
> - Suporte a variáveis, funções, controle de fluxo e classes

Este trabalho introduz conceitos fundamentais de compiladores e linguagens formais, incluindo:

> - tradução dirigida por sintaxe
> - hierarquias de tokens
> - padrão de projeto Visitor
> - árvores sintáticas abstratas
> - ambientes e escopo léxico
> - interpretadores baseados em AST

---

## Propósito do Projeto

> O objetivo desta implementação é:
> - Compreender e demonstrar o funcionamento interno de um interpretador completo;
> - Aplicar conceitos teóricos de compiladores em um sistema funcional;
> - Integrar análise léxica, análise sintática, resolução de escopos e execução;
> - Permitir a execução de programas escritos na linguagem Lox.

O projeto é totalmente **educacional** e segue rigorosamente a metodologia apresentada no livro *Crafting Interpreters*.

---

## Descrição Geral do Sistema

O sistema foi dividido em **módulos principais**, que juntos implementam um interpretador funcional da linguagem Lox.

### **1. Classe Principal – `Lox.java`**
- Ponto de entrada do interpretador;
- Responsável por inicializar o Scanner, Parser, Resolver e Interpreter;
- Oferece dois modos de execução:
    - **Execução de Arquivo:** `java lox.Lox arquivo.lox`
    - **Modo Interativo (REPL):** execução linha a linha;
- Centraliza o tratamento de erros e o controle do fluxo de execução.

### **2. Scanner (Analisador Léxico)**
- Lê o código-fonte caractere a caractere;
- Agrupa caracteres em **lexemas** e os classifica em **tokens**;
- Reconhece operadores, literais, palavras-chave e símbolos;
- Finaliza a leitura com o token **EOF (End Of File)**.

### **3. Token e TokenType**
- `TokenType.java` define todos os tipos de tokens da linguagem Lox;
- `Token.java` representa um token individual contendo:
    - tipo,
    - lexema,
    - literal,
    - linha de ocorrência.

### **4. Parser (Analisador Sintático)**
- Consome a lista de tokens gerada pelo Scanner;
- Valida a estrutura gramatical do programa;
- Constrói a **Árvore Sintática Abstrata (AST)** por meio das classes `Expr` e `Stmt`.

### **5. AST – Expr.java e Stmt.java**
- Representam, respectivamente, expressões e comandos da linguagem;
- Implementam o padrão de projeto **Visitor**;
- Permitem múltiplas operações sobre a AST sem modificar suas estruturas.

### **6. Interpreter**
- Percorre a AST e executa o programa;
- Avalia expressões, executa comandos e controla o fluxo;
- Implementa operações aritméticas, lógicas, comparações e chamadas.

### **7. Environment**
- Gerencia variáveis e escopos;
- Implementa o encadeamento de ambientes para escopo léxico.

### **8. Funções e Classes**
- `LoxCallable`: interface para entidades chamáveis;
- `LoxFunction`: representação de funções definidas pelo usuário;
- `LoxClass`: definição de classes da linguagem;
- `LoxInstance`: instâncias de objetos.

### **9. Resolver**
- Realiza a resolução estática de escopos;
- Detecta usos inválidos de variáveis antes da execução;
- Garante acesso correto a variáveis locais e globais.

### **10. Tratamento de Erros**
- `RuntimeError.java`: erros em tempo de execução;
- `Return.java`: controle interno do retorno de funções.

---

## Estrutura do Repositório

```plaintext
src/
 ├── main/
 │   └── java/
 │       └── lox/
 │           ├── Lox.java
 │           ├── Scanner.java
 │           ├── Parser.java
 │           ├── Expr.java
 │           ├── Stmt.java
 │           ├── Interpreter.java
 │           ├── Resolver.java
 │           ├── Environment.java
 │           ├── Token.java
 │           ├── TokenType.java
 │           ├── LoxCallable.java
 │           ├── LoxFunction.java
 │           ├── LoxClass.java
 │           ├── LoxInstance.java
 │           ├── RuntimeError.java
 │           ├── Return.java
 │           └── GenerateAst.java
 └── test/
     └── java/
         └── arquivos .lox
pom.xml
```

---

## Como Compilar o Projeto

### Requisitos
- JDK 17 ou superior;
- Apache Maven 3.9 ou superior.

### Compilação

Abra o terminal na pasta onde está o `pom.xml` e execute:

```bash
mvn clean package
```

Se aparecer **BUILD SUCCESS**, a compilação foi realizada corretamente.

---

## Como Utilizar o Interpretador

O interpretador pode ser utilizado de **duas formas distintas**: modo interativo (REPL) e execução de programas completos.

---

## ▶️ Execução no Modo REPL (Interpretador Interativo)

1. Acesse o diretório:

```bash
cd src/main/java
```

2. Execute o interpretador:

```bash
java lox.Lox
```

3. O prompt `>` será exibido, indicando que o REPL está ativo.

4. Exemplos de comandos no REPL:

```lox
var x = 10;
print x + 5;

fun soma(a, b) {
  return a + b;
}

print soma(3, 4);

class Exemplo {
  init(v) { this.v = v; }
  mostrar() { print this.v; }
}

var e = Exemplo(20);
e.mostrar();
```

---

## ▶️ Execução de Programas Completos (.lox)

### Programa 1 — Exemplo Geral (funções, laços e condicionais)

```bash
java lox.Lox src/test/java/codigo1.lox
```

Este programa demonstra:
- declaração e chamada de funções;
- uso de laços `while`;
- condicionais `if/else`;
- retorno de valores.

---

### Programa 2 — Exemplo com Classes

```bash
java lox.Lox src/test/java/codigo2.lox
```

Este programa demonstra:
- declaração de classes;
- inicializadores (`init`);
- métodos;
- criação e uso de instâncias.

---

## Considerações Finais

O interpretador desenvolvido permite a execução de programas completos escritos na linguagem Lox, oferecendo uma visão prática e aprofundada do funcionamento interno de linguagens interpretadas.

O projeto consolida os principais conceitos abordados na disciplina de Compiladores, integrando teoria e prática de forma clara, estruturada e didática.

---

## Autoras

- **Fernanda Sousa de Assunção Vale**  
  E-mail: fernanda.sav@discente.ufma.br  
  GitHub: https://github.com/Fernanda-SAV

- **Izadora de Paula Santos Lima**  
  E-mail: izadora.paula@discente.ufma.br  
  GitHub: https://github.com/izadora-paula

---

## Agradecimentos

- Universidade Federal do Maranhão (UFMA);
- Professor Doutor Sergio Souza Costa;
- Colegas do curso.

---

## Copyright / License

Este material é resultado de um trabalho acadêmico para a disciplina **Compiladores**, sob a orientação do professor **Dr. SERGIO SOUZA COSTA**, no semestre letivo **2025.2**, do curso de **Engenharia da Computação** na Universidade Federal do Maranhão (**UFMA**).

Todo o material sob esta licença é **software livre**, licenciado sob os termos da **Licença MIT**.

O MATERIAL É FORNECIDO “COMO ESTÁ”, SEM GARANTIA DE QUALQUER TIPO.

Para mais informações sobre a Licença MIT: https://opensource.org/licenses/MIT.

---

<div align="center">
Feito com ♥ por <strong>Alunos da UFMA</strong>
</div>
