Trabalho de POO - Caixa de Supermercado

Olá a todos! Este é o projeto desenvolvido como parte do trabalho da disciplina de Programação Orientada a Objetos (POO) pelo aluno João Lucas Fernandes Santos, sob a orientação do Professor Luis Chaves.

Tecnologias Utilizadas

• Linguagem de Programação: C#

• Ambiente de Desenvolvimento: Microsoft Visual Studio

Sobre o Projeto

Imagine entrar em um supermercado e ter uma experiência de caixa automatizada. Este programa em C# traz essa ideia à vida, permitindo que os usuários escaneiem produtos, calculem o total da compra, escolham diferentes formas de pagamento e recebam um recibo.

Principais Funcionalidades

Como o Código Está Organizado

• Na classe Program, o código herda características da classe Caixa e implementa métodos específicos, como EmitirSom e ReiniciarPrograma.

• A classe abstrata Caixa define a estrutura básica do processo de compra.

• A interface IPagamento é utilizada para definir os métodos relacionados ao pagamento.

• As classes concretas PagamentoDebito, PagamentoCredito e PagamentoAVista implementam a interface IPagamento.

• A classe PagamentoFactory cria instâncias de objetos com base na opção escolhida para o pagamento.

• A classe Produto é uma representação simples de um item comprado.

Como Utilizar

• Execute o programa.

• Siga as instruções para inserir os produtos e escolher as opções de pagamento.

• Observe a nota fiscal gerada e decida se deseja reiniciar o programa.

Dicas Importantes

• Ao inserir os dados, lembre-se de usar valores válidos.

• Ah, e não se esqueça: o programa emite sons simples durante algumas interações para tornar a experiência mais amigável!

