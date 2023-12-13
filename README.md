# Caixa de Supermercado - Trabalho de POO

Bem-vindo ao projeto de Caixa de Supermercado, desenvolvido como parte do trabalho da disciplina de Programação Orientada a Objetos (POO) pelo aluno João Lucas Fernandes Santos, sob a orientação do Professor Luis Chaves.

## Tecnologias Utilizadas

- **Linguagem de Programação:** C#
- **Ambiente de Desenvolvimento:** Microsoft Visual Studio, Visual Studio Code, C# Shell.NET IDE

## Sobre o Projeto

Este projeto tem como objetivo simular uma experiência de caixa de supermercado automatizada, permitindo que os usuários escaneiem produtos, calculem o total da compra, escolham diferentes formas de pagamento e recebam um recibo.

## Principais Funcionalidades

### Estrutura do Código

O código está organizado da seguinte forma:

- **Program:** Herda características da classe `Caixa` e implementa métodos específicos, como `EmitirSom` e `ReiniciarPrograma`.
- **Caixa:** Define a estrutura básica do processo de compra, utilizando a interface `IPagamento` e classes concretas como `PagamentoDebito`, `PagamentoCredito` e `PagamentoAVista`.
- **Produto:** Representa um item comprado.
- **PagamentoFactory:** Cria instâncias de objetos com base na opção escolhida para o pagamento.

### Como Utilizar

1. **Execução do Programa:**
   - Clone este repositório.
   - Execute o programa.
  
2. **Instruções para Utilização:**
   - Siga as instruções para inserir os produtos e escolher as opções de pagamento.
  
3. **Observações Importantes:**
   - Certifique-se de inserir valores válidos durante a entrada dos dados.
   - O programa emite sons simples durante algumas interações para tornar a experiência mais amigável.
