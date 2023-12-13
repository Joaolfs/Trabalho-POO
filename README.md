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
  
   - ## Código:
   - using System;
using System.Linq;
using System.Collections.Generic;

using System;
using System.Collections.Generic;
using System.Threading;

namespace programaCaixasupermercado
{
    class Program : Caixa
    {
        static void Main(string[] args)
        {
            Program programa = new Program();
            programa.PassarCompras();
        }

        protected override void EmitirSom(string mensagem)
        {
            Console.WriteLine(mensagem);
            Console.Beep();
        }

        public override void ReiniciarPrograma()
        {
            AgradecerVolteSempre();
            Proximo();

            Console.Clear();
            produtos.Clear();
            somaTotal = 0;
            PassarCompras();
        }
    }

    public abstract class Caixa
    {
        protected List<Produto> produtos = new List<Produto>();
        protected double somaTotal = 0;

        public void PassarCompras()
        {
            bool continuar = true;

            do
            {
                Console.WriteLine("Digite o nome do produto: ");
                string nome = Console.ReadLine();

                Console.WriteLine("Digite o valor do produto: ");
                double item = Convert.ToDouble(Console.ReadLine());

                Console.WriteLine("Digite a quantidade do produto: ");
                double quantidade = Convert.ToDouble(Console.ReadLine());

                Produto produto = new Produto(nome, item, quantidade);
                produtos.Add(produto);
                somaTotal += (quantidade * item);

                Console.WriteLine("Digite 0 para parar ou 1 para continuar: ");
                int parar = Convert.ToInt32(Console.ReadLine());

                if (parar == 0)
                {
                    continuar = false;
                    Pagar();
                }
            } while (continuar);
        }

        protected abstract void EmitirSom(string mensagem);

        protected void AgradecerVolteSempre()
        {
            Console.Clear();
            EmitirSom("Obrigado pela compra! Volte sempre.");
        }

        protected void Proximo()
        {
            EmitirSom("Próximo...");
            Thread.Sleep(2000);
        }

        public abstract void ReiniciarPrograma();

        public void Pagar()
        {
            Console.WriteLine("O valor total das compras é: " + somaTotal);
            Console.WriteLine("Deseja pagar com débito, crédito ou à vista?");
            Console.WriteLine("1 - Débito");
            Console.WriteLine("2 - Crédito");
            Console.WriteLine("3 - À vista");

            int opcaoPagamento;

            // Loop para garantir uma opção válida
            do
            {
                Console.WriteLine("Escolha a opção de pagamento (1, 2 ou 3): ");
                if (!int.TryParse(Console.ReadLine(), out opcaoPagamento) || opcaoPagamento < 1 || opcaoPagamento > 3)
                {
                    Console.WriteLine("Opção inválida. Tente novamente.");
                }
            } while (opcaoPagamento < 1 || opcaoPagamento > 3);

            double valorPagamento;
            double troco = 0;

            if (opcaoPagamento == 3)
            {
                Console.WriteLine("Digite o valor do pagamento à vista: ");
                valorPagamento = Convert.ToDouble(Console.ReadLine());

                troco = valorPagamento - somaTotal;
                if (troco < 0)
                {
                    Console.WriteLine("Valor insuficiente. Insira um valor igual ou maior que o total das compras.");
                    Pagar();
                    return;
                }
            }
            else
            {
                IPagamento pagamento = PagamentoFactory.GetPagamento(opcaoPagamento);
                valorPagamento = pagamento.Pagar(somaTotal);
            }

            EmitirNota(opcaoPagamento, valorPagamento, troco);

            AgradecerVolteSempre();
            Proximo();
            PassarCompras();
        }

        public void EmitirNota(int opcaoPagamento, double pagamento, double troco)
        {
            Console.WriteLine("---------------------------------------------------");

            foreach (var produto in produtos)
            {
                Console.WriteLine("Produto: " + produto.Nome);
                Console.WriteLine("Item: " + produto.Item);
                Console.WriteLine("Quantidade: " + produto.Quantidade);
                Console.WriteLine("---------------------------------------------------");
            }

            Console.WriteLine("Opção de pagamento escolhida: " + opcaoPagamento);
            Console.WriteLine("Valor pago: " + pagamento);

            if (troco > 0)
                Console.WriteLine("Troco: " + troco);

            Console.WriteLine("---------------------------------------------------");
            Console.WriteLine("Nota emitida com sucesso!");
            Console.WriteLine("---------------------------------------------------");

            Console.WriteLine("Pressione Enter para continuar...");
            Console.ReadLine();
        }
    }

    public interface IPagamento
    {
        double Pagar(double total);
    }

    public class PagamentoDebito : IPagamento
    {
        public double Pagar(double total)
        {
            return total * 0.9;
        }
    }

    public class PagamentoCredito : IPagamento
    {
        public double Pagar(double total)
        {
            return total * 0.95;
        }
    }

    public class PagamentoAVista : IPagamento
    {
        public double Pagar(double total)
        {
            return total;
        }
    }

    public class PagamentoFactory
    {
        public static IPagamento GetPagamento(int opcao)
        {
            switch (opcao)
            {
                case 1:
                    return new PagamentoDebito();
                case 2:
                    return new PagamentoCredito();
                case 3:
                    return new PagamentoAVista();
                default:
                    throw new ArgumentException("Opção inválida");
            }
        }
    }

    public class Produto
    {
        public string Nome { get; set; }
        public double Item { get; set; }
        public double Quantidade { get; set; }

        public Produto(string nome, double item, double quantidade)
        {
            Nome = nome;
            Item = item;
            Quantidade = quantidade;
        }
    }
}
