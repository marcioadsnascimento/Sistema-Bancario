# Sistema-Bancario

public class GerenciaBanco3 {

    public static void main(String[] args) {
        System.out.println("Hello World!");
    }
}
import java.util.Scanner;

class Usuario {
    private String nome;
    private String sobrenome;
    private String cpf;

    public Usuario(String nome, String sobrenome, String cpf) {
        this.nome = nome;
        this.sobrenome = sobrenome;
        this.cpf = cpf;
    }

    public String getInformacoes() {
        return "Nome: " + nome + " " + sobrenome + "\nCPF: " + cpf;
    }
}

class ContaBancaria {
    private double saldo;

    public double consultarSaldo() {
        return saldo;
    }

    public void depositar(double valor) {
        if (valor > 0) {
            saldo += valor;
            System.out.println("Depósito realizado com sucesso!");
        } else {
            System.out.println("Valor inválido para depósito.");
        }
    }

    public void retirar(double valor) {
        if (valor > 0 && valor <= saldo) {
            saldo -= valor;
            System.out.println("Retirada realizada com sucesso!");
        } else {
            System.out.println("Valor inválido ou saldo insuficiente.");
        }
    }
}

public class SistemaBancario {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Bem-vindo ao Sistema Bancário!");

        // Criando usuário
        System.out.print("Digite seu nome: ");
        String nome = scanner.nextLine();
        System.out.print("Digite seu sobrenome: ");
        String sobrenome = scanner.nextLine();
        System.out.print("Digite seu CPF: ");
        String cpf = scanner.nextLine();

        Usuario usuario = new Usuario(nome, sobrenome, cpf);
        ContaBancaria conta = new ContaBancaria();

        boolean executar = true;

        while (executar) {
            System.out.println("\nEscolha uma opção:");
            System.out.println("1. Consultar saldo");
            System.out.println("2. Depositar");
            System.out.println("3. Retirar");
            System.out.println("4. Informações do usuário");
            System.out.println("5. Sair");
            int opcao = scanner.nextInt();

            switch (opcao) {
                case 1:
                    System.out.println("Saldo atual: R$" + conta.consultarSaldo());
                    break;
                case 2:
                    System.out.print("Digite o valor para depósito: R$");
                    double valorDeposito = scanner.nextDouble();
                    conta.depositar(valorDeposito);
                    break;
                case 3:
                    System.out.print("Digite o valor para retirada: R$");
                    double valorRetirada = scanner.nextDouble();
                    conta.retirar(valorRetirada);
                    break;
                case 4:
                    System.out.println(usuario.getInformacoes());
                    break;
                case 5:
                    executar = false;
                    System.out.println("Obrigado por usar nosso sistema! Até logo!");
                    break;
                default:
                    System.out.println("Opção inválida. Tente novamente.");
            }
        }

        scanner.close();
    }
}
