# COMPILADORES P2 - Lox: Análise Léxica - Fernanda Sousa de Assunção Vale e Izadora de Paula Santos Lima
Trabalho submetido à disciplina de Compiladores - Lox: Análise Léxica


# Lox: Análise Léxica
<div align="center">
  <img src="https://img.shields.io/badge/Versão-1.0-blue.svg" alt="Versão 1.0">
  <img src="https://img.shields.io/badge/Licença-MIT-green.svg" alt="Licença MIT">
</div>

---

## Resumo do Trabalho

> Este projeto apresenta a implementação inicial de um interpretador em Java baseado na linguagem Lox, conforme o livro Crafting Interpreters de Robert Nystrom. 
> O trabalho consiste na construção do scanner (analisador léxico), responsável por ler o código-fonte e convertê-lo em uma sequência de tokens (as menores unidades significativas de um programa). 
> Além disso, foi estruturada a classe principal do interpretador (Lox.java), com suporte para execução via arquivo e em modo interativo (REPL), e um sistema básico de tratamento de erros. 
> O objetivo é demonstrar os fundamentos do processo de tradução dirigida por sintaxe e a importância da análise léxica no fluxo de compilação e interpretação de linguagens.

## Descrição
> O sistema foi dividido em **módulos principais**, que juntos implementam a primeira etapa de um interpretador funcional:

### **1. Classe Principal – `Lox.java`**
- Responsável por iniciar o programa.
- Oferece dois modos de execução:
    - **Execução de Arquivo:** `jlox [arquivo]`
    - **Modo Interativo (REPL):** executa linha a linha.
- Implementa **tratamento básico de erros** e controle de fluxo com códigos de saída padrão UNIX (`sysexits.h`).

### **2. Scanner (Analisador Léxico)**
- Lê o código-fonte caractere a caractere.
- Agrupa caracteres em **lexemas** e os classifica em **tokens**.
- Implementa a lógica de avanço (`advance()`), identificação e armazenamento de tokens.
- Finaliza com um token **EOF (End Of File)** para indicar o fim da leitura.

### **3. Token e TokenType**
- **`TokenType.java`** define todos os tipos de tokens da linguagem Lox (operadores, palavras-chave, literais, etc.).
- **`Token.java`** representa cada token identificado, contendo:
    - Tipo (`TokenType`)
    - Lexema (texto original)
    - Valor literal (quando aplicável)
    - Linha de ocorrência

### **4. Tratamento de Erros**
- Implementado diretamente em `Lox.java` para centralizar a lógica de relatórios.
- Usa o método `error(line, message)` para exibir erros de sintaxe e interromper a execução quando necessário.
- Mantém o controle de estado por meio da variável estática `hadError`.

---
## Estrutura do Repositório

```plaintext
/src
└── lox
       ├── Lox.java          → Classe principal do interpretador (REPL e execução de arquivo)
       ├── Scanner.java      → Scanner que percorre o código-fonte e gera tokens
       ├── Token.java        → Classe de representação dos tokens
       ├── TokenType.java    → Enum com todos os tipos possíveis de tokens
       └── Parser.java
       └── Interpreter.java

```
---
## Autora

- [Fernanda Sousa de Assunção Vale](fernanda.sav@discente.ufma.br) -> GitHub: [Fernanda-SAV](https://github.com/Fernanda-SAV) 
- [Izadora de Paula Santos Lima](izadora.paula@discente.ufma.br) -> Github: [izadora-paula](https://github.com/izadora-paula)

---

## Agradecimentos

- **Universidade Federal do Maranhão (UFMA)**
- **Professor Doutor Sergio Souza Costa**
- **Colegas de curso**

Agradecemos a todas as pessoas e instituições que contribuíram para a realização deste trabalho.

---

## Materiais de Apoio para o Projeto

- [Link para material usado como referência de exercícios e exemplos](https://craftinginterpreters.com/scanning.html#the-interpreter-framework)

---

## Copyright / License

Este material é resultado de um trabalho acadêmico para a disciplina **Compiladores**, sob a orientação do professor **Dr. SERGIO SOUZA COSTA**, no semestre letivo **2025.2**, do curso de **Engenharia da Computação** na Universidade Federal do Maranhão (**UFMA**).

Todo o material sob esta licença é **software livre**: pode ser usado para fins acadêmicos e comerciais **sem nenhum custo**. Não há papelada, nem royalties, nem restrições de “copyleft” do tipo GNU. Ele é licenciado sob os termos da **Licença MIT**, reproduzida abaixo, e, portanto, é compatível com a GPL e também se qualifica como software de código aberto. É de domínio público. O espírito desta licença é que você é livre para usar este material para qualquer finalidade, sem nenhum custo. O único requisito é que, se você usá-lo, me dê crédito.



Copyright © 2025 Material Educacional

Este material está licenciado sob a Licença MIT. É permitido o uso, cópia, modificação, e distribuição deste material para qualquer fim, desde que acompanhado deste aviso de direitos autorais.

O MATERIAL É FORNECIDO "COMO ESTÁ", SEM GARANTIA DE QUALQUER TIPO, EXPRESSA OU IMPLÍCITA, INCLUINDO, MAS NÃO SE LIMITANDO ÀS GARANTIAS DE COMERCIALIZAÇÃO, ADEQUAÇÃO A UM DETERMINADO FIM E NÃO VIOLAÇÃO. EM HIPÓTESE ALGUMA OS AUTORES OU DETENTORES DE DIREITOS AUTORAIS SERÃO RESPONSÁVEIS POR QUALQUER RECLAMAÇÃO, DANOS OU OUTRA RESPONSABILIDADE, SEJA EM UMA AÇÃO DE CONTRATO, ATO ILÍCITO OU DE OUTRA FORMA, DECORRENTE DE, OU EM CONEXÃO COM O MATERIAL OU O USO OU OUTRAS NEGOCIAÇÕES NO MATERIAL.

Para mais informações sobre a Licença MIT: https://opensource.org/licenses/MIT.

Copyright © 2025 Educational Material

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the “Software”), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

Para mais informações sobre a **Licença MIT**: [https://opensource.org/licenses/MIT](https://opensource.org/licenses/MIT).

---

<div align="center">
Feito com ♥ por <strong>Alunos UFMA</strong>
</div>