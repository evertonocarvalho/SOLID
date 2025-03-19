# SOLID
## Documentação e exemplos sobre os princípios SOLID
<br>

**SOLID** é um conjunto de cinco princípios de design de software que ajudam a criar sistemas mais robustos, legíveis e fáceis de manter. <br>
Esses princípios foram introduzidos por [**Robert Cecil Martin (Uncle Bob)**](http://cleancoder.com/) e são amplamente usados no desenvolvimento orientado a objetos. <br>
<br>
Cada letra na sigla **SOLID** representa um princípio:

**S - Single Responsibility Principle (SRP)** <br>
Cada classe deve ter uma única responsabilidade ou razão para mudar.
Uma classe deve fazer apenas uma coisa, e todas as suas funcionalidades devem estar alinhadas a essa responsabilidade.

Exemplo: Uma classe para gerenciar dados de usuários não deve lidar com a lógica de envio de e-mails.

**O - Open/Closed Principle (OCP)** <br>
O software deve estar aberto para extensão, mas fechado para modificação.
Isso significa que você pode adicionar novas funcionalidades sem alterar o código existente, geralmente usando abstrações (interfaces ou classes abstratas).

Exemplo: Adicionar um novo tipo de cálculo sem alterar a lógica já existente.

**L - Liskov Substitution Principle (LSP)** <br>
Uma subclasse deve ser substituível por sua classe base sem alterar o comportamento esperado do programa.
Em outras palavras, ao usar herança, a subclasse deve respeitar o contrato da classe base.

Exemplo: Se uma classe `Quadrado` herda de uma classe `Retângulo`, os métodos relacionados a áreas e perímetros devem funcionar corretamente.

**I - Interface Segregation Principle (ISP)** <br>
As classes não devem ser forçadas a implementar interfaces que elas não utilizam.
Em vez de criar uma única interface grande, divida-a em interfaces menores e mais específicas.

Exemplo: Uma classe de impressora não deve precisar implementar métodos para escaneamento se ela não for um scanner.
<br>

```java
// Interface para funcionalidades de impressão
interface Impressora {
    void imprimir(String documento);
}

// Interface para funcionalidades de escaneamento
interface Scanner {
    void escanear(String documento);
}

// Classe que implementa apenas a funcionalidade de impressão
class ImpressoraSimples implements Impressora {
    @Override
    public void imprimir(String documento) {
        System.out.println("Imprimindo: " + documento);
    }
}

// Classe que implementa ambas as funcionalidades: impressão e escaneamento
class Multifuncional implements Impressora, Scanner {
    @Override
    public void imprimir(String documento) {
        System.out.println("Imprimindo: " + documento);
    }

    @Override
    public void escanear(String documento) {
        System.out.println("Escaneando: " + documento);
    }
}

public class SegregacaoDeInterfaces {
    public static void main(String[] args) {
        // Usando uma impressora simples
        Impressora impressora = new ImpressoraSimples();
        impressora.imprimir("Relatório financeiro");

        // Usando uma multifuncional (impressora + scanner)
        Multifuncional multifuncional = new Multifuncional();
        multifuncional.imprimir("Contrato");
        multifuncional.escanear("Documento de identidade");
    }
}
```

**D - Dependency Inversion Principle (DIP)** <br>
Dependa de abstrações, não de implementações.
Componentes de alto nível não devem depender de componentes de baixo nível diretamente. Ambos devem depender de abstrações.

Exemplo: Em vez de uma classe Pedido instanciar diretamente uma classe Pagamento, ela deve depender de uma interface como IPagamento.

**Resumo** <br>
Esses princípios ajudam a criar sistemas que são:

- Fáceis de entender, porque seguem responsabilidades claras.
- Mais flexíveis, pois são abertos a extensões e mudanças sem impacto negativo.
- Menos propensos a erros, devido ao uso correto de abstrações.
