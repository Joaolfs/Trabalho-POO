# Trabalho-POO
trabalho da cadeira de poo: Caixa de supermercado <br/>
Aluno: João Lucas Fernandes Santos<br/>
Professor: Luis Chaves
# tecnologias usadas
c#

## Caixa de Supermercado

Este software simula uma caixa de supermercado, onde o usuário pode escanear produtos, calcular o total da compra, escolher diferentes formas de pagamento e receber um recibo.

## Principais Funcionalidades

## Estrutura do Código

- A classe `Program` herda características da classe `Caixa` e possui métodos específicos, como `EmitirSom` e `ReiniciarPrograma`.
- A classe abstrata `Caixa` define a estrutura básica do processo de compra.
- A interface `IPagamento` é utilizada para definir os métodos relacionados ao pagamento.
- As classes concretas `PagamentoDebito`, `PagamentoCredito` e `PagamentoAVista` implementam a interface `IPagamento`.
- A classe `PagamentoFactory` cria instâncias de objetos baseados na opção escolhida para o pagamento.
- A classe `Produto` é uma representação simples de um item comprado.

## Como Utilizar

1. Execute o programa.
2. Siga as instruções para inserir os produtos e escolher as opções de pagamento.
3. Observe a nota fiscal gerada e decida se deseja reiniciar o programa.

## Observações

- Certifique-se de inserir valores válidos durante a entrada dos dados.
- O programa emite sons simples durante algumas interações.



